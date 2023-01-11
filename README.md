# Actividad-21-cc3s2
Actividad 21 del curso de Desarrollo de Software CC3S2

En esta actividad nos centraremos en el corazón de Jenkins: Los pipelines.

# Introducción a los pipelines
Un pipeline es simplemente una secuecia de scripts para automatizar procesos, en esta caso, representa una parte del proceso de entrega y control de calidad del software.

El pipeline nos brinda los siguientes beneficios:

- Agrupación de operaciones: Las operaciones o pasos podemos agruparlos en etapas (stages).
- Visibilidad: Podemos visualizar todos los aspectos de un proceso, lo que ayuda en el análisis rápido de fallas.
- Feedback: Cuando ocurre un problema, los miembros del equipo pueden aprender acerca de dichos problemas.

# La estructura de un pipeline
Un pipeline consta de dos elementos:
- Step: Es una sola operación que le dice a Jenkins qué hacer
- Stage: Es una separación lógica de pasos que agrupa un conjunto o secuencia de pasos conceptualmente distintas.

# Veamos un primer ejemplo
- Como ejemplo, vamos a crear un pipeline llamado Helloworld que contendrá dos etapas:

![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/ac21-helloworld.PNG "")
- Luego, pulsamos en Build Now y podemos ver los stages:

![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/ac21-helloworld2.PNG "")

# Secciones de la estructura del pipeline
Las secciones definen la estructura del pipeline y normalmente contienen una o más directivas o pasos.
- Stages: Serie de una o más directivas de etapa
- Steps: Esto define una serie de instrucciones de uno o más pasos
- Post: Es algo que se ejecutará luego de que la construcción del pipeline termine
- Agent: Esto especifica dónde tiene lugar la ejecución

# Directivas del pipeline
Con las directivas podemos configurar un pipeline
- Triggers: Con esto podemos escuchar eventos que inicien la construcción del pipeline
- Options: Con esto podemos especificar ciertas opciones del pipeline, como el tiempo máximo de ejecución del pipeline, la cantidad de veces que se puede ejecutar un pipeline después de una falla, etc.
- Environment: Aquí podemos definir variables de entorno que se utilizarán durante la construcción
- Parameters: Lista de parámetros de entrada
- Stage: Agrupación lógica de pasos
- When: Con esto podemos ejecutar una etapa siempre y cuando se cumpla una condición dada
- Tools: Lista de herramientas a instalar
- Input: Solicitar parámetros de entrada
- Parallel: Especificar etapas que se ejecutan en paralelo

# Commit pipeline
