
[ **[Volver al Menú Principal](MAIN.md)** ]

### Diseño

El primer paso es analizar el esquema de datos que se desea compartir por medio del API, definiendo una esquema modularizado por recursos y verbos.

**Ejemplo:**

- **Recurso**: Personas (Entidad que contiene datos específicos de una persona y esta mapeada en una serie de tablas en una BD) generalmente se define como plural
- **Verbo:** Acción que identifica el tipo de operación a trabajar sobre el recurso (Consultar [GET], Actualizar [POST], Insertar [PUT], Eliminar [DELETE])

Una vez el recurso este definido se debe armar el path o URI que se expondra definiendo el/los parametros de entrada [REQUEST]

**Ejemplo:**
```
host.com/personas/{id}
host.com/personas/{id}/telefonos
```

Una vez definida la URI del recurso se define la estructura del RESPONSE, para ello se debe tener presente de forma obligatoria el uso de los codigos de respuesta HTTP para que viaje en el Header de la respuesta :

- 100 Respuestas informativas
- 200 Respuestas satisfactorias
- 300 Redirecciones
- 400 Errores de cliente
- 500 Errores de servidor

Para mayor información sobre los códigos de respuesta HTTP: [https://developer.mozilla.org/es/docs/Web/HTTP/Status](HTTP Codes - Mozilla)

En el Body contiene el mensaje de respuesta en formato JSON:

```
{
  "primerNombre": "JUAN",
  "segundoNombre": "PABLO",
  "primerApellido": "PEREZ",
  "segundoApellido": "RODRIGUEZ",
  "fechaNacimiento": "14/05/1990",
  "genero": "MASCULINO",
  "nacionalidad": "CO",
  "estadoCivil": "SOLTERO"
}
```

En caso de que la petición genere un error adicional al codigo HTTP correspondiente es buena practica definir tambien un esquema de respuesta de error:

```
{
  "error": {
    "codigo": "0000",
    "mensaje": "Ha ocurrido un error (...) "
  }
```

Esta definición finalmente debe ser idéntica a la documentación entregada del API en Swagger.

Para Mayor información sobre el diseño de API Rest y sus buenas practicas:[Mejores Practicas en el diseño de API - RedHat](https://www.redhat.com/es/topics/api/what-is-api-design)



### Implementación
 
***

Camel por medio de componentes como (servlet, netty, restlet y spark-rest) se permite la construcción de Api's Rest tanto en JAVA DSL como en XML DSL, lo cual se conoce como (REST DSL).
Esta tecnología es mucho más amigable y legible para la definición de API's Rest, ya que es orientada a recursos y permite una fácil integración con otros componentes como Swagger.

Dependencias en POM.xml (deben estar instaladas como features en el servidor jboss ya que son dependencias que se requieren en el registry):

```xml
<dependency>
	<groupId>org.apache.camel</groupId>
	<artifactId>camel-netty4-http</artifactId>	
	<version>${camel.version}</version>	
</dependency>

<dependency>
	<groupId>org.apache.camel</groupId>
	<artifactId>camel-jackson</artifactId>
	<version>${camel.version}</version>
</dependency>

<dependency>
	<groupId>org.apache.camel</groupId>
	<artifactId>camel-http4</artifactId>
	<version>${camel.version}</version>
</dependency>

```

Ejemplo de configuración del servidor para exponer el API Rest, junto con Swagger:

```java
restConfiguration()
.component("netty-http")
.bindingMode(RestBindingMode.off) //Off para evitar conflictos con los data formats
.endpointProperty("nettySharedHttpServer", "#sharedNettyHttpServer") //#sharedNettyHttpServer Como servicio osgi que comparte el server y puerto de la API
.contextPath("/{{rest.api.name}}/v{{rest.api.version}}")
```

### Servidor/Puerto Netty Compartido

Se desplego como servicio OSGI en un esquema blueprint la conexión al server y puerto compartido entre Api's, por detecto se definio el puerto 8186 como el puerto centralizado para exponer las REST API. el server depende del ambiente (tutaza/topaipi/tenerife ....), el proyecto se puede descar en : [Netty-Server-GitHub](https://github.com/UniandesDSIT/Fuse-Transversal-Netty-Http)

```xml
	<bean id="configuration"
		class="org.apache.camel.component.netty.http.NettySharedHttpServerBootstrapConfiguration">
		<property name="port" value="8186" />
		<property name="host" value="topaipi.uniandes.edu.co" />
		<property name="backlog" value="50" />
	</bean>
	<bean id="httpServer"
		class="org.apache.camel.component.netty.http.DefaultNettySharedHttpServer"
		init-method="start" destroy-method="stop">
		<property name="nettyServerBootstrapConfiguration" ref="configuration" />
	</bean>
	 <service ref="httpServer" interface="org.apache.camel.component.netty.http.NettySharedHttpServer"/>
```

Ejemplo donde se crea el recurso "example" con acciones get y post a "user"

```java
rest("/example").description("Example rest service")
      .get("/user/{type}/{document}")
         .to("direct:find")
      .post("/user")
         .to("direct:update");
```

Para mayor información:
https://camel.apache.org/manual/latest/rest-dsl.html

### Correcto uso del códigos de respuesta HTTP

***

Respuesta satisfactorias:

```
from("direct:find")
.bean(UserService.class, "getUser")
.marshal(jsonDFUser)
.bean(StatusGenerator.class, "statusHttpOk(*,{{http.code.ok}})")
.log("Body: \n ${body}")
.wireTap("mock:outputGet");
```

Respuestas no satisfactorias:

```
onException(Exception.class)
.handled(true)
.choice()
	.when(simple("${property[HttpErrorPropertie]} == null"))
		.setProperty("HttpErrorCode").simple("{{http.code.internal.server.error}}")
		.log("Http-Error-Code: ${property[HttpErrorCode]}")
	.otherwise()
		.setProperty("HttpErrorCode").simple(" ${properties:${property[HttpErrorPropertie]}}")
		.log("Http-Custom-Error-Code: ${property[HttpErrorCode]}")
.end()
.bean(new StatusGenerator(), "statusHttpFail(*,${property[HttpErrorCode]})")
.setBody().simple("${exception.message}")
.wireTap("mock:outputFail");
``` 



[ **[Volver al Menú Principal](MAIN.md)** ]
