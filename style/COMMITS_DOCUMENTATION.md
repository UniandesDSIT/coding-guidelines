# Guía de estílo para Commits y Documentación

> Tomados parcialmente de [Contributing to Atom](https://github.com/atom/atom/blob/master/CONTRIBUTING.md)

En esta sección, hablaremos de como documentar el código y los proyectos, así como la escritura de los commits. El propósito de estas normas es asegurar que el desarrollo pueda ser mantenible en el tiempo, se pueda hacer trazabilidad de cambios y el conocimiento del desarrollo pueda ser transferido.

## Mensajes de Commit de Git

Así como la nomenclatura en código, los mensajes de commit es preferible escribirlos en inglés, para poder facilitar que cualquier persona, independiente de su lengua materna pueda entender el historial de cambios, y asegurarse de que puedan continuar con un desarrollo. 

Los lineamientos de estilo son los siguientes:

* Considere iniciar el mensaje del commit con un emoji descriptivo:
    * :art: `:art:` cuando mejore la forma/estructura del código
    * :racehorse: `:racehorse:` cuando mejore el rendimiento
    * :non-potable_water: `:non-potable_water:` cuando maneje fugas de memoria
    * :memo: `:memo:` cuando escriba documentación
    * :penguin: `:penguin:` cuando arregle algo específico de Linux/Android
    * :apple: `:apple:` cuando arregle algo específico para macOS/iOS
    * :checkered_flag: `:checkered_flag:` cuando arregle algo específico para Windows
    * :bug: `:bug:` cuandoa arregle un bug
    * :fire: `:fire:` cuando elimine código o archivos
    * :green_heart: `:green_heart:` cuando arregle el archivo de CI
    * :white_check_mark: `:white_check_mark:` cuando agregue tests
    * :lock: `:lock:` cuando trabaje con asuntos de seguridad
    * :arrow_up: `:arrow_up:` cuando actualice dependencias
    * :arrow_down: `:arrow_down:` cuando desactualice dependencias
    * :shirt: `:shirt:` cuando elimine advertencias del linter
* Continue por el código de la historia de usuario o issue al cual está aportando el desarrollo. El formato es de la forma <HU/IS>-<ID FASE PROYECTO>-<NÚMERO HISTORIA> Por ejemplo:
	* HU-S1-001
* Haga uso del _present tense_ (_"Add feature"_, no _"Added feature"_)
* Haga uso del _imperative mood_ (_"Move cursor to..."_, no _"Moves cursor to..."_)
* Limite la primera línea a 72 caracteres o menos.
* Refierase a Pull Requests o Issues libremente después de la primera línea.
* Cuando cambie documentación únicamente, incluya en el título del commit las palabras `[ci skip]`. Esto con el fin de no integrar continuamente este cambio.

Por lo tanto, un buen nombramiento del commit sería de la manera:
´´´
git commit -m ":bug: IS-S1-030: Fix bug in class Student"
´´´

## Documentación de código

Todo código en este repositorio debe ser documentado a dos niveles. 

1. Documente el código. Para ello siga los estándares de código según el lenguaje. Todo método, función, clase, archivo, u paquete, debe ser comentado al inicio del bloque de código. La documentación debe contener:
	* Autor (usuario github)
	* Descripción / propósito del código
	* Fecha de codificación
	* En caso de métodos o funciones: precondiciones, postcondiciones, excepciones, parámetros y retornos.
2. Documentación técnica. Para agregar documentación adicional requerida para despliegues y configuración de la aplicación se hace uso de la wiki del repositorio. En esta wiki usted debe tener presente:
	* Use [Markdown](https://daringfireball.net/projects/markdown) para elaborar la documentación en repositorios.
	* Refiérase a los métodos y clases en Markdown con la notación personalizada `{}`:
		* Refiérase a clases con `{ClassName}`
		* Refiérase a los métodos de instancia con `{ClassName#methodName}`
		* Refiérase a los métodos de clase con `{ClassName.methodName}`
	* Use la wiki para documentar todo aquello adicional que otros desarrolladores deben saber del desarrollo para poder ejecutarlo y continuar con el.

Si se considera necesario, la documentación autogenerada de código (dependiendo el framework) puede ser presentada en el repositorio. Para esto usted debe solicitar la aprobación de dejar pública la documentación, si se considera necesario usted debe:
	
* Crear una rama que tendrá solo la documentación. Esta rama debe ser protegida para que no sea mezclada con las demás. 
* Crear una página web haciendo uso de la característica de github para este fin, y apuntando a la rama de documentación.
* Seleccione la plantilla y modifíquela para que integre la documentación autogenerada o los archivos .md que usted requiera para documentar su código.