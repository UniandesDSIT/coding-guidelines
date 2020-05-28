 [ **[Volver al Menú Principal](MAIN.md)** ]


### Uso de Patrones de Integración 

Los EIP de Camel, permiten dar solución a un problema común de una forma estándar y probada por la comunidad. Es aconsejable aplicarlos de manera **_obligatoria_** dependiendo la necesidad:

Para ver la documentación completa de EIP's de Fuse Dirigirse a: [Apache Camel EIP](https://camel.apache.org/components/latest/eips/enterprise-integration-patterns.html)

***
### Buenas Practicas de Escritura de Código 
***
- Declaración de clases e interfaces empleando la nomenclatura de camel-case.
```java
public class ClassExample
{
    (...)
}
```
- Declaración de paquetes con todas las letras en minúsculas.
```java
co.edu.uniandes.fuse.labs.restdsl.routes
```
- Declaración de métodos y variables empleando la nomenclatura camel-case, con la excepción de ser la primera letra de la primera palabra en minúscula. Dichos nombres de clase deben hacer referencia a su funcionalidad.
```java
public void mainClass() throws Exception {
    (...)
}
```
- Declaración de constantes con todas las en mayúsculas separando cada palabra con guiones bajos, procurando dejarlas en una clase aparte.


```java
static final int EJEMPLO_CONSTANTE= 5;
```
- Hacer uso de JavaDoc para documentar brevemente los metodos y clases, parametros recibidos y retornados.

@author
Nombre autor o autores

@deprecated
Indica que el método o clase es obsoleto (propio de versiones anteriores) y que no se recomienda su uso.

**Descripción**

**@param**
Definición de un parámetro de un método, es requerido para todos los parámetros del método.
Nombre de parámetro y descripción

**@return**
Informa de lo que devuelve el método, no se aplica en constructores o métodos "void".
Descripción del valor de retorno

**@see**
Asocia con otro método o clase.
Referencia cruzada
referencia (#método(); clase#método(); paquete.clase; paquete.clase#método()).

**@version**
Versión del método o clase.

```java
/**
 * Returns an Image object that can then be painted on the screen. 
 * The url argument must specify an absolute {@link URL}. The name
 * argument is a specifier that is relative to the url argument. 
 * <p>
 * This method always returns immediately, whether or not the 
 * image exists. When this applet attempts to draw the image on
 * the screen, the data will be loaded. The graphics primitives 
 * that draw the image will incrementally paint on the screen. 
 * @author Universidad de Los Andes - Luis Castillo / l.castillo1@uniandes.edu.co
 * @param  url  an absolute URL giving the base location of the image
 * @param  name the location of the image, relative to the url argument
 * @return      the image at the specified URL
 * @see         Image
 */
 public Image getImage(URL url, String name) {
```

- La clases y funciones deben de ser pequeñas y hacer una sola cosa, evitar duplicar código.
- Los métodos no debes de consumir paramentos a diestra y siniestra, siempre tratar en enviar objetos que contengan los datos con los cuales va a trabajar el método.
- Uso de una plantilla como formato de codificación, todo el equipo debe tener acceso a dicha plantilla. 
- Declarar variables con el menor nivel de acceso posible (solo en dentro del método que trabaja con la variable).
```java
private String sayHello = "Hello World";
```
- Eliminar código innecesario, obsoleto y/o comentado por completo.
- No usar System.out.println(""); para la "creación" de logs, siempre usar un Framework adecuado para el logback.
```java
   org.slf4
```
- Restringir el acceso a paquetes, clases y miembros de clase cuando sea posible, empleando los modificadores de acceso private, protected, (default), public.
```java
   import co.edu.uniandes.fuse.labs.restdsl.routes.MainRoute;
   
   (...) 
   
   public void configure() throws Exception {
       (...)
   }
```
- Evitar la aparición de nullPointerException dentro del código, devolviendo colecciones vacías o empleando excepciones cuando el resultado sea nulo (null).
- Siempre manejar las excepciones, procurando no hacer impresion de todo el printstacke, simplemente el _e->message_.
```java
    try {
         (...)
    } catch (Exception e) {
         (...)
    }
```
- No presentar en los logs información sensible.
- Liberar recursos siempre que no sean requeridos.
- No mostrar información sensible al momento que ocurra una excepción.


_Para mayor información: [Guía de Estilo de Código](https://google.github.io/styleguide/javaguide.html)_
*** 


[ **[Volver al Menú Principal](MAIN.md)** ]
