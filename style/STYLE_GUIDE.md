# Guías de estilo

> Tomados parcialmente de [Contributing to Atom](https://github.com/atom/atom/blob/master/CONTRIBUTING.md)

## Mensajes de Commit de Git

Así como la nomenclatura en código, los mensajes de commit deben escribirse en inglés, para poder facilitar que cualquier persona, independiente de su lengua materna pueda entender el historial de cambios, y asegurarse de que . Los lineamientos de estilo son los siguientes:

* Haga uso del _present tense_ (_"Add feature"_, no _"Added feature"_)
* Haga uso del _imperative mood_ (_"Move cursor to..."_, no _"Moves cursor to..."_)
* Limite la primera línea a 72 caracteres o menos.
* Refierase a Pull Requests o Issues libremente después de la primera línea.
* Cuando cambie documentación únicamente, incluya en el título del commit las palabras `[ci skip]`.
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

## Guía de Estilo de Javascript

Todo código escrito en Javascript debe adherirse al [JavaScript Standard Style](https://standardjs.com/).

* Prefiera el object spread operator (`{...anotherObj}`) a usar `Object.assign()`.
* Se hará indentación a 4 espacios.
* Se usarán _semicolons (;)_ para finalizar una acción.

## Guía de Estilo de Python

Todo código escrito en Python debe adherirse al [PEP8](https://www.python.org/dev/peps/pep-0008/).

## Guía de Estilo de Kotlin

Todo código escrito en Kotlin debe adherirse a las [convenciones de código](https://kotlinlang.org/docs/reference/coding-conventions.html) de Kotlin.

## Guía de Estilo de Swift

Todo código escrito en Kotlin debe adherirse a las [guías de diseño de APIs](https://swift.org/documentation/api-design-guidelines/) de Swift.

## Guía de Estilo de Java

Todo código escrito en Java debería adherirse a las [guías de estílo de código de Google](https://google.github.io/styleguide/javaguide.html)

## Guía de Estilo de PHP

Todo código escrito en PHP debería adherirse a la [PSR-2](https://www.php-fig.org/psr/psr-2/)

## Guía de Estilo para CSS

Todo archivo CSS debería adherirse a las [guías de estílo de CSS](https://cssguidelin.es/)

## Guía de Estilo de Documentación de código

* Use [Markdown](https://daringfireball.net/projects/markdown) para elaborar la documentación en repositorios.
* Refiérase a los métodos y clases en Markdown con la notación personalizada `{}`:
    * Refiérase a clases con `{ClassName}`
    * Refiérase a los métodos de instancia con `{ClassName#methodName}`
    * Refiérase a los métodos de clase con `{ClassName.methodName}`
