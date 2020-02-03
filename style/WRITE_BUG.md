# Cómo reportar un bug o una mejora

Esta sección lo guía a través del envío de errores. Seguir estas guías lo ayudan a que los desarrolladores y la comunidad entiendan su reporte :pencil:, reproduzca el comportamiento :computer: :computer:, y encuentre informes relacionados :mag_right:.
Antes de crear un reporte de bugs, por favor revise [esta lista](#antes-de-sugerir-un-informe-de-error) como puede descubrir que no necesita uno. Cuando usted esta creando un reporte de bugs, por favor [incluya tantos detalles como sea posible](#cómo-presentar-un-buen-informe-de-error). Complete la lantilla definida, la informacion que esta pregunta ayuda a resolver los issues rapido.

## Antes de sugerir un informe de error

* **Determine en qué repositorio debe informarse el problema**.
* **Realice una [busqueda general](https://github.com/search?q=+is%3Aissue+user%3Auniandesdsit)** para ver si el problema ya ha sido reportado. Si lo ha sido **y el issue aún está abierto**, agregue un comentario al issue existente en lugar de abrir uno nuevo.

## ¿Cómo Presentar un (Buen) Informe de Error?

Los errores se registran y siguen como [GitHub issues](https://guides.github.com/features/issues/). Después de haber determinado en cuál repositorio está relacionado tu error, crea un issue en ese repositorio y provee la siguiente información llenando la plantilla sugerida.

> **Nota:** Si usted encuentra un issue con estado **Closed** que es igual al mismo que usted esta experimentando, abra un nuevo issue e incluya in link al issue original en el cuerpo de su nuevo issue.

Para reportar un bug en un proyecto en github se seguirá el estilo de escritura de pruebas **GIVEN-WHEN-THEN** introducido como parte de BDD [Behavior-Driven-Development](https://dannorth.net/introducing-bdd/)

### Given (Dado):

Describa el estado del sistema, el ambiente de ejecución, las variables que está usando, y cualquier información relevante que considere para poder replicar el evento.
* **Especifique que version del proyecto está utilizando.** Usted puede conocer la version exacta revisando la documentación de API, la de la aplicación en cuestión en su Acerca de, o a través de la tienda de aplicaciones.
* **Especifique el nombre y version de Sistema Operativo que está utilizando**, si es aplicación de escritorio o móvil.
* **Especifique el nombre y version del navegador que está utilizando**, si es aplicación web.

### When (Cuando):

Coloque uno a uno los pasos para reproductir el bug. Sea detallado en cada uno y apóyese de imágenes que permita entender el evento.

### Then (Entonces):

* **Comportamiento observado:** Describa el resultado obtenido, adjunte imágenes que permitan observarlo mejor.

* **Comportamiento esperado:** Describa el comportamiento que esperaba el usuario, enlace esta punto la documentación o diseños correspondientes.

### Template

Use el siguiente template como base para reportar cualquier bug en los proyectos de este repositorio:

```
Reproducible: Siempre / Casi siempre / Algunas veces / Raramente / No se puede reproducir

## Dado 

Sistema Operativo Windows 10 Home edition
Hardware:...
Browser: Google Chrome Versión ...
...
Datos de entrada: ...

## Cuando

* El usuario selecciona filtrar...
* Posteriormente selecciona el primer elemento ...

## Entonces

**Comportamiento observado:**
* Se presenta mensaje de error en pantalla como se ve en la imagen
* Se presenta mensaje de error en consola como se ve en la imagen
* No se encuentran los datos en la base de datos como se ve en la imagen

**Comportamiento esperado:**
* Se debería presentar mensaje de confirmación de la transacción
* Posteriormente la tabla debería presentar el cambio en el registro tal como se describe en la documentación (link a la documentación)

## Información adicional (Opcional)

Si considera que debe ir alguna información adicional para guiar al desarrollador puede escribirlos acá. Por ejemplo:

* Revisando los datos de entrada solo me sucede con el usuario cuando tiene un punto en su username.
* **Empezó a ocurrir el problema recientemente** (ej. después de realizar una actualización) o fue siempre un problema?
* Si el problema empezó a ocurrir recientemente, **puedes reproducir el problema en una versión más antigua?** Cuál es la versión más reciente en la que este problema empieza a ocurrir?
* **Puedes reproducir este error con certeza?** Si no, provee detalles sobre qué tan frecuentemente ocurre y bajo qué condiciones ocurre normalmente.


```
## Sugiriendo Mejoras

Esta sección lo guiará para el envío de sugerencias de mejoras, incluyendo características completamente nuevas y mejoras menores a la funcionalidad existente. Seguir estas pautas ayuda a los desarrolladores y a la comunidad a entender su sugerencia :pencil: y a encontrar sugerencias relacionadas :mag_right:.

Antes de crear sugerencias de mejora, por favor consulte [esta lista](#antes-de-enviar-una-sugerencia-de-mejora) ya que puede descubrir que no necesita crear una. Cuando usted esta creando una Sugerencia de Mejora, por favor [incluya la mayoría de detalles posibles](#cómo-presento-una-buena-sugerencia-de-mejora). complete la [plantilla](#Template) de issues presentada antes, incluya los pasos que ud tomaria si la caracteristica que usted esta solicitando existiera.

#### Antes de Enviar una Sugerencia de Mejora

* **Revise si existe una herramienta que brinde esa mejora.**
* **Determine en cuál proyecto o proyectos se impacta esta mejora.**
* **Realizar una [busqueda superficial](https://github.com/search?q=+is%3Aissue+user%3Auniandesdsit)** para ver si la mejora ha sido sugerida. Si es asi, agregue un comentario al problema existente en lugar de abrir uno nuevo.

#### ¿Cómo Presento una (Buena) Sugerencia de Mejora?

Las sugerencias de mejoras se rastrean como [GitHub issues](https://guides.github.com/features/issues/). Despues de que usted determine cuál repositorio está relacionado con su sugerencia de mejora, cree un issue en el repositorio y provea la siguiente información:

* **Use un titulo claro y descriptivo** para el issue para identificar la sugerencia.
* **Provea una descripcion paso a paso de la sugerencia de mejora** tan detallada como sea posible.
* **De ejemplos especificos para demostrar cada paso**. incluya ejemplos completos y claros, como [Markdown code blocks](https://help.github.com/articles/markdown-basics/#multiple-lines).
* **Describa el comportamiento actual** y **explique que comportamiento espera ver en su lugar** y por qué.
* **Incluya pantallazos y GIFs animados** que le ayuden a demostrar los pasos o señale la parte a la que se refiere la sugerencia. Usted puede usar [esta herramienta](https://www.cockos.com/licecap/) para grabar GIFs en macOS y Windows, y [esta herramienta](https://github.com/colinkeenan/silentcast) o [esta](https://github.com/GNOME/byzanz) en Linux.
* **Explique porque esta mejora debería usarse** para la mayoría de los usuarios y no es algo que pueda o deba implementarse como un módulo específico.
* **Enumere algunas aplicaciones o soluciones donde esta mejora existe.**
* **Especifique que version del proyecto está utilizando.** Usted puede conocer la version exacta revisando la documentación de API, la de la aplicación en cuestión en su Acerca de, o a través de la tienda de aplicaciones.
* **Especifique el nombre y version de Sistema Operativo que está utilizando**, si es aplicación de escritorio o móvil.
* **Especifique el nombre y version del navegador que está utilizando**, si es aplicación web.


