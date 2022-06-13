# Desafío 4
## Índice
1. [Descripción del problema](#descripción-del-problema)
2. [Descripción de la solución](#descripción-de-la-solución)
3. [Cómo ejecutar el programa](#cómo-ejecutar-el-programa)
4. [Análisis de resultados](#análisis-de-resultados)
5. [Video explicativo](#video-explicativo)
6. [Coevaluación](#coevaluación)
## Descripción del problema
***
Para este desafío se utilizó el ambiente Ant-V2 de Mujoco Environments. Este ambiente consta de una hormiga representada por un robot que posee un torso y 4 patas unidas a él. Cada pata, además, está dividida en 2 partes.

El objetivo final dentro de este desafío es lograr, por medio de técnicas de Aprendizaje Reforzado, que la hormiga avance hacia la derecha a travez de la coordinación de sus 4 patas y torso a la vez, aplicando fuerza en forma de torques en cada una de sus partes.

**Características del ambiente:**

* **Action Space:** en este problema, se utiliza un espacio de acción continuo. Cada acción se define por un vector de 8 elementos, cada uno representando las fuerzas de torque aplicadas a cada parte de la hormiga. Las fuerzas se representan en una magnitud que va del -1 al 1.

* **Observation Space:** cada estado se compone de los valores posicionales de cada parte de la hormiga (posición del torso en los ejes X, Y, Z, el ángulo del torso con respecto a los ejes y los ángulos entre cada parte), y la velocidad las velocidades (velocidad y velocidad angular del torso, y la velocidad angular de cada parte de la hormiga), además de las fuerzas de contacto externas como el suelo o la gravedad. En total, se tiene un estado representado con un *ndarray* de forma (111,).

* **Rewards:** el ambiente considera 4 recompensas: *survive_reward* (recompensa por mantenerse con vida), *forward_reward* (recompensa al movimiento, positivamente si es a la derecha), *ctrl_cost* (penaliza acciones muy grandes) y *contact_cost* (penaliza si las fuerzas de contacto son muy elevadas). El total se calcula como: *reward = alive survive_reward + forward_reward - ctrl_cost - contact_cost*.

* **Estado Inicial:** se comienza siempre con los valores (0.0, 0.0, 0.75, 1.0, 0.0 … 0.0) en el vector de estado, con un rango del -0.1 al 0.1 para agregar estocasticidad a cada episodio.

* **Estado Final:** se considera que un episodio ha llegado a su fin si su duración supera los 1000 timestep, algun valor ha dejado de ser finito o la orientación del torso en el eje Y se sale del rango 0.2 a 1.0.

## Descripción de la solución
***
Para este entorno de simulación se implementó la técnica de Aprendizaje Reforzado Deep Q-Learning por medio de una red neuronal (reemplazando la tabla Q). Por otro lado, para el entrenamiento se implementó la técnica de memoria Prioritized Experience Replay (PER), que a diferencia de Experience Replay, ésta prioriza las experiencias más significativas, ayudando a que el agente encuentre mejores estrategias para lograr el objetivo, que es avanzar.

Los parámetros utilizados para el entrenamiento del agente fueron los siguientes:

* **Cantidad de Episodios:** 20
* **Tamaño de memoria para PER:** 20.000

En cuanto a la estrategia de exploración, se utilizó Epsilon-Greedy con Decay, con los siguientes parámetros:

* **Epsilon:** 1
* **Epsilon mínimo:** 0.001
* **Epsilon Decay:** 0.0005

La estrategia calcula una probabilidad de exploración cada vez que se retorna una acción, considerando un decay_step, que representa la cantidad de transiciones realizadas. Esto está representado en la siguiente fórmula:

* _explore_probability = self.epsilon_min + (self.epsilon - self.epsilon_min) * np.exp(-self.epsilon_decay * decay_step)_
## Cómo ejecutar el programa
***
d
## Análisis de resultados
***
c
## Video explicativo
***
Para una mejor comprensión del problema y su resolución, se adjunta un video explicativo en el siguiente [link]().
## Coevaluación
***
A continuación, tablas de coevaluación según estos criterios: [Criterios de coevaluación](https://docs.google.com/document/d/1YSba-KNP-ReP_TJePQkCHXJ1x4_MtOizQPIrNnriZbw/edit#)
1. **Asistencia y puntualidad**

|                     | Esteban González | Carlos Núñez | Priscilla Riffo | Katherine Sepúlveda |
| ------------------- | :--------------: | :----------: | :-------------: | :-----------------: |
| Esteban González    | | | | |
| Carlos Núñez        |X| |X|X|
| Priscilla Riffo     | | | | |
| Katherine Sepúlveda | | | | |
2. **Integración**

|                     | Esteban González | Carlos Núñez | Priscilla Riffo | Katherine Sepúlveda |
| ------------------- | :--------------: | :----------: | :-------------: | :-----------------: |
| Esteban González    | | | | |
| Carlos Núñez        |X| |X|X|
| Priscilla Riffo     | | | | |
| Katherine Sepúlveda | | | | |
3. **Responsabilidad**

|                     | Esteban González | Carlos Núñez | Priscilla Riffo | Katherine Sepúlveda |
| ------------------- | :--------------: | :----------: | :-------------: | :-----------------: |
| Esteban González    | | | | |
| Carlos Núñez        |X| |X|X|
| Priscilla Riffo     | | | | |
| Katherine Sepúlveda | | | | |
4. **Contribución**

|                     | Esteban González | Carlos Núñez | Priscilla Riffo | Katherine Sepúlveda |
| ------------------- | :--------------: | :----------: | :-------------: | :-----------------: |
| Esteban González    | | | | |
| Carlos Núñez        |X| |X|X|
| Priscilla Riffo     | | | | |
| Katherine Sepúlveda | | | | |
5. **Resolución de conflictos**

|                     | Esteban González | Carlos Núñez | Priscilla Riffo | Katherine Sepúlveda |
| ------------------- | :--------------: | :----------: | :-------------: | :-----------------: |
| Esteban González    | | | | |
| Carlos Núñez        |X| |X|X|
| Priscilla Riffo     | | | | |
| Katherine Sepúlveda | | | | |
