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
El proceso de integración continua más básico se demonina commit pipeline
Este proceso consta de las siguientes etapas:
- Checkout: Esta etapa descarga el código fuente del repositorio
- Compile: Esta etapa compila el código fuente.
- Unite test: Esta etapa ejecuta un conjunto de pruebas unitarias

# Creación de un repositorio de Github
Crearemos un repositorio llamado calculador
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-github.PNG "")

# Creando la etapa checkout
- En esta etapa se descarga el código del repositorio.
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-checkout.PNG "")
- Pulsamos en build now para ver si se ejecutó con éxito
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-checkout2.PNG "")

# Etapa Compile
## Creación de un proyecto Java Spring Boot
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-code.PNG "")
## Pushing el código a Github
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-repo.PNG "")

Podemos compilar el proyecto localmente usando ./gradlew compileJava
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-compileJava.PNG "")

## Creación de una etapa Compile
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-stage-compileJava.PNG "")

## Pruebas unitarias
En esta etapa, comprobaremos si el código hace lo que esperamos que haga. Para ello, tendremos que hacer lo siguiente:
1. Agrega el código fuente para la lógica del calculador
2. Escribe una prueba unitaria para el código
3. Agrega una etapa de Jenkins para ejecutar la prueba unitaria

## Creamos la lógica de negocios
- Para ellos crearemos una clase llamada Calculator y CalculadorControler
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculadorJava.PNG "")

![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculadorJava2.PNG "")

- Escribiendo la prueba unitaria

![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculadorTest.PNG "")

## Creación de una etapa de prueba unitaria
![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-unitest-stage.PNG "")

## Jenkinsfile

Hasta ahora hemos creado todo el código del pipeline directamente en Jenkins. Sin embargo, es recomendable crear un archivo llamado Jenkinsfile centro del propio repositorio, porque de esa manera podemos controlar su versionamiento.

Además, trae otros beneficios inmediatos, como los siguientes:
- Si Jenkins falla, la definición del pipeline no se pierde, porque está almacenado en el repositorio
- Se almacena el historial de cambios del pipeline
- Cualquier cambio en el pipeline pasa por el proceso de revisión de código

Debido a que Jenkinsfile está dentro del repositorio, entonces la fase de Checkout se puede eliminar, ya que, ya no es necesario descargar el código

![Alt text](https://raw.githubusercontent.com/ricardoolivaresventura/Actividad-21-cc3s2/main/calculador-jenkinsfile.PNG "")

