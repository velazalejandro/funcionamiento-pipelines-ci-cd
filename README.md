# funcionamiento-pipelines-ci-cd
FUNCIONAMIENTO PIPELINES INTEGRACIÓN CONTINUA

Para crear repositorios en GitLab hay que tener en cuenta lo siguiente:
1. El código se tiene que convertir mediante formato UTF-8.
2. Se crea el repo y su nombre debe cumplir la nomenclatura adecuada y el número correspondiente de dígitos. Todo código fuente de la aplicación va al repo y después se crean las ramas correspondientes en dicho repo. NOTA: Si existen pruebas de regresión automatizadas, se crea un repositorio para las pruebas de modo que se repiten los pasos anteriores para el código.

Se añade el archivo "Jenkinsfile" que consta de un fichero utilizado por Jenkins para la configuración de pipelines mediante una serie de parámetros o variables establecidas.
El campo "artifacts" sirve para configurar despliegues.
El campo "emails" sirve para agregar correos y con ello se les notifica del estado de las pipelines que puede ser exitosa (success) o fallida (failed).
Los scripts de groovy comprenden construcción (build), análisis de código (code analyze), test unitarios (unit test) y subida de artefactos.

¿Cómo se ejecutan las pipelines en Jenkins?
Hay 2 maneras de poder ejecutarlas:
1. Ejecución manual mediante el botón "Construir con parámetros" (build with parameters).
2. Ejecución automática realizando una serie de commits en GitLab.

Las pipelines de CI/CD conllevan una serie de fases:
1. Fase de evaluación: Lee el repositorio y la configuración de las variables.
2. Fase de build: Fase de construcción que pasa los test unitarios y la subida de los artefactos a Nexus Sonatype.
3. Fase de deploy: Indica el tipo de despliegue de la aplicación. Ej: Helm.
4. Fase de testing: Indica si son pruebas de regresión.
5. Fase de post: Indica el envío de correos a los destinatarios y les notifica el progreso de la ejecución si es exitosa o fallida.

Las pipelines de testing continuo(Selenium, JUnit, Karate, Robot Framework) conllevan una serie de fases:
- Fase de descarga del código fuente de los test.
- Fase de pruebas de regresión completas.
- Fase de pruebas de línea base de rendimiento.
- Fase de pruebas de accesibilidad.
- Fase de registros de resultados en ALM.

¿Cómo se ejecutan las pipelines de testing continuo?
La ejecución es solamente de tipo manual mediante la opción de construir con parámetros (build with parameters), se eligen los tipos de prueba a ejecutar y hay una serie de registros de resultados en la herramienta ALM.
