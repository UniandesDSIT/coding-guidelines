# Guía de estílo para Commits y Documentación

> Tomados parcialmente de [Contributing to Atom](https://github.com/atom/atom/blob/master/CONTRIBUTING.md)

En esta sección, hablaremos de como documentar el código y los proyecto. El propósito de estas normas es asegurar que el desarrollo pueda ser mantenible en el tiempo, se pueda hacer trazabilidad de cambios y el conocimiento del desarrollo pueda ser transferido.

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
	
La documentación técnica para los proyectos de la DSIT son:

* Documento técnico de la solución donde se indica: arquitectura del software, stack tecnológico, repositorios, herramientas y demás componentes relevantes en el desarrollo. 
* Documento de dependencias donde se indica cada una de las librerías, frameworks e integraciones que se estén usando en la solución. Es importante contar con datos específicos como links de cada elemento, versión, descripción y razón de usarlo.
* Documento de despliegue: documento donde se indica el paso a paso para ejecutar la solución.
* Documento de configuración: documento donde se indica las configuraciones que se deben tener en cuenta para el correcto funcionmiento de la aplicación.

Si se considera necesario, la documentación autogenerada de código (dependiendo el framework) puede ser presentada en el repositorio, para esto usted debe:
	
* Crear una rama que tendrá solo la documentación. Esta rama debe ser protegida para que no sea mezclada con las demás.
* Agregar en la wiki el link a la rama en la cual se encuentra la documentación.

En caso que se considere dejar pública la documentación. Se debe solicitar la aprobación del CedEx que gestiona el repositorio de código, si la DSIT considera que es viable su publicación usted debe:

* Crear una página web haciendo uso de la característica de github para este fin, y apuntando a la rama de documentación.
* Seleccione la plantilla y modifíquela para que integre la documentación autogenerada y/o los archivos .md que usted requiera para documentar su código. Tome el ejemplo de la forma en que está creada esta documentación.
