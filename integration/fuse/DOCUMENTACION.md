[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]

Con fin de automatizar procesos se implementa swagger de la mano con Rest Dsl para generar una documentación de las API Rest directamente basada con el código, esto asegura una documentación actualizada.

Se debe documentar en swagger toda API-Rest o servicio que exponga por medio de HTTP **recursos que permita interactuar con otras aplicaciones por medio de acciones como _(consultar / modificar / crear / eliminar)_** haciendo énfasis en la estructura de petición y respuesta, y el manejo de errores.


***

Dependencia requerida en el POM
```xml
<dependency>
	<groupId>org.apache.camel</groupId>
	<artifactId>camel-swagger-java</artifactId>
	<version>${camel.version}</version>
</dependency>
```
Código Ejemplo:

```java
/**
* REST & SWAGGER CONFIGURATION
*/
restConfiguration()
.component("netty4-http")
.bindingMode(RestBindingMode.off) //Off para evitar conflictos con los data formats
.host("{{rest.api.host}}")
.port("{{rest.api.port}}")
.contextPath("/{{rest.api.name}}/v{{rest.api.version}}")
.apiContextPath("/doc")
.apiContextRouteId("doc")
.apiProperty("api.title", "{{rest.api.description}}")
.apiProperty("api.version", "{{rest.api.version}}")
.apiProperty("cors", "{{rest.api.cors}}");

/**
* REST & SWAGGER COMPONENTSS
*/
rest("/students").description("Example rest service")
.get("/personal-info/{type}/{document}")
	.description("Find a user by type and document")				
	.consumes("application/json").produces("application/json")
		.param().name("type").required(true).description("The type of the user").defaultValue("CC").dataType("string")
		.endParam()
		.param().name("document").required(true).description("The document of the user").defaultValue("1234567").dataType("integer")
		.endParam()
	.outType(User.class)
	.to("direct:find")
```	    
Una vez el proyecto este corriendo en el servidor, se puede acceder a la documentación meadiente la URL compuesta en la configuración, swagger permite generar el contenido tanto en json como en yaml 

- Ejemplo Json: http://localhost:9090/restDSL/v1.0.0/doc/swagger.json

```json
  {
  "swagger" : "2.0",
  "info" : {
    "version" : "1.0.0",
    "title" : "User Api Example"
  },
  "host" : "localhost:9090",
  "basePath" : "/restDSL/v1.0.0",
  "tags" : [ {
    "name" : "students",
    "description" : "Example rest service"
  }, {
    "name" : "teachers",
    "description" : "Example rest service"
  } ],
  "schemes" : [ "http" ],
```

Ejemplo Yaml: http://localhost:9090/restDSL/v1.0.0/doc/swagger.yaml

```yaml
---
swagger: "2.0"
info:
  version: "1.0.0"
  title: "User Api Example"
host: "localhost:9090"
basePath: "/restDSL/v1.0.0"
tags:
- name: "students"
  description: "Example rest service"
- name: "teachers"
  description: "Example rest service"
schemes:
- "http"
paths:
  /students/personal-info:
```
Para mayor información:
https://camel.apache.org/components/latest/swagger-java.html

<img src="https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/raw/master/src/main/resources/documentation/swagger.png?raw=true?raw=true"/>

[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]
