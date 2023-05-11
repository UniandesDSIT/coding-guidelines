# Guías de estilo de código

## Guía de Estilo de Javascript

Todo código escrito en Javascript debe adherirse al [JavaScript Standard Style](https://standardjs.com/).

* Prefiera el object spread operator (`{...anotherObj}`) a usar `Object.assign()`.
* Se hará indentación a 2 espacios.
* No se usarán _semicolons (;)_ para finalizar una acción.

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

## Semántica HTML5 - BEM

Todo código escrito en HTML5 debería adherise a la [Métodología BEM](http://getbem.com/)

## Guía de Estilo para Sass
Todo código escrito en Sass debería adherirse al [Guías de estilo Sass](https://sass-guidelin.es/es/)
* Se hará indentación a 2 espacios.
* No se deberá utilizar sintaxis css en los archivo sass.
* Se debe limitar el uso de !important, solo se debe utilizar en caso extremo de que la regla de estilo no llegue a ser tomada.
* Los colores deben ir con un solo sistema, es decir no puede haber hexadecimal y RGBA para declarar colores cohabitando un mismo proyecto.
* Los parámetros de los mixin deben ir en minúscula, sin espacios y serados por guiones.
* Se debe utilizar para los comentarios "///" (triple barra) y un espacio, esto con el fin que esos comentarios no se compilen y salgan en el archivo .css a producción.
* Al crear una regla de estilo para varios elementos, cada elemento separado por coma debe ocupar una línea.
* Se debe limitar el uso de ID para crear reglas de estilo, solo se debe utilizar en caso de que no se tenga manipulación de la maqueta.
* El nombre de los mixin deben ir en minúscula, sin espacios y separados por guiones.

## Guía de Estilo para paleta de color

El formato RGB (Red Green Blue) se utiliza para definir un color en términos de su composición de rojo, verde y azul. Por ejemplo, el color rojo se puede definir como "rgb(255, 0, 0)". La principal ventaja de usar el formato RGB es que es fácil de entender y leer para los desarrolladores y diseñadores que trabajan con colores.

Buena práctica en codificación:
Todo código escrito en Sass debería adherirse al [Guías de estilo rgb](https://stylelint.io/user-guide/rules/color-function-notation/#legacy)

Pero para nuestros proyectos se sugiere el siguiente formato 

```css
a {
 color: rgb(0, 0, 0);
}

a {
 color: rgba(12, 122, 231, 0.2)
}

```








