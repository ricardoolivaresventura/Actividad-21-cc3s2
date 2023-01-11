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
Como ejemplo, vamos a crear un pipeline llamado Helloworld que contendrá dos etapas:

