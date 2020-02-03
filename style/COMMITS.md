# Guía de estílo para Commits y Documentación

> Tomados parcialmente de [Contributing to Atom](https://github.com/atom/atom/blob/master/CONTRIBUTING.md)

En esta sección, hablaremos de como documentar los commits. El propósito de estas normas es asegurar que el desarrollo pueda ser mantenible en el tiempo, se pueda hacer trazabilidad de cambios y el conocimiento del desarrollo pueda ser transferido.

## Mensajes de Commit de Git

Así como la nomenclatura en código, los mensajes de commit es preferible escribirlos en inglés, para poder facilitar que cualquier persona, independiente de su lengua materna pueda entender el historial de cambios, y asegurarse de que puedan continuar con un desarrollo. 

Los lineamientos de estilo son los siguientes:

* Si usted está haciendo uso de Azure Boards para la gestión del desarrollo comience el nombre del commit con **AB#<número del work item>**

* Utilice en el mensaje del commit un emoji descriptivo:
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
* Continue por el código de la historia de usuario o issue al cual está aportando el desarrollo. El formato es de la forma `<HU/IS>-<ID FASE PROYECTO>-<NÚMERO HISTORIA>` Por ejemplo:
	* HU-S1-001
* Haga uso del _present tense_ (_"Add feature"_, no _"Added feature"_)
* Haga uso del _imperative mood_ (_"Move cursor to..."_, no _"Moves cursor to..."_)
* Limite la primera línea a 72 caracteres o menos.
* Refierase a Pull Requests o Issues libremente después de la primera línea.
* Cuando cambie documentación únicamente, incluya en el título del commit las palabras `[ci skip]`. Esto con el fin de no integrar continuamente este cambio.

Por lo tanto, un buen nombramiento del commit sería de la manera:
```
git commit -m "AB#312 :bug: IS-S1-030: Fix bug in class Student"
```