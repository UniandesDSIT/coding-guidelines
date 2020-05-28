[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]


El objetivo de las pruebas unitarias va más allá de asegurar la calidad de las rutas expuestas. Es lograr hacer de las pruebas unitarias cultura de trabajo en el desarrollo de software.
Al definir una serie de pruebas unitarias a los proyectos camel se puede empezar definir un modelo de CI & CD, ya que al automatizar las pruebas es posible generar una secuencia de trabajos (pipelines) para entornos DevOps.

Cada proyecto creado a partir de esta plantilla **deberá asegurar por lo menos un 80% de cobertura en la ejecución de pruebas en SonarQube**, esto permitirá detectar fallas tempranas previas a despliegues. 

Esta cobertura depende de la cantidad de código escrito en la aplicación es decir que si se desea cubrir el 100% de cobertura la prueba unitaria deberá consumir la totalidad de funciones, control de excepciones en try/catch.

Principalmente deben estar enfocadas al core de negocio o razón de ser de la apliación con escensarios y datos reales.
Para los proyectos basados en REST-DSL lo ideal es hacer consumo de cada recurso expuesto con datos reales asegurando también los escenarios de fallo en respuestas (300/400/500)


***

Dependencias requeridas en el POM.xml

```xml
<dependency>
	<groupId>org.apache.camel</groupId>
	<artifactId>camel-test</artifactId>
	<version>${camel.version}</version>
</dependency>

<dependency>
	<groupId>org.apache.camel</groupId>
	<artifactId>camel-test-spring</artifactId>
	<version>${camel.version}</version>
	<scope>test</scope>
</dependency>

<dependency>
	<groupId>org.slf4j</groupId>
	<artifactId>slf4j-api</artifactId>
</dependency>

<dependency>
	<groupId>org.slf4j</groupId>
	<artifactId>slf4j-log4j12</artifactId>
</dependency>
```
Plugins:

```xml
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-surefire-plugin</artifactId>
	<version>2.14.1</version>
	<configuration>
		<includes>
			<include>**/*Test.java</include>
		</includes>
	</configuration>
</plugin>
```

Ejemplo de Implementación:

Se utiliza inyección de dependencias por medio de anotaciones:

@Produce  -> Plantilla encargada de generar el recurso que se utilizará para al prueba.
@EndpointInject-> Punto donde se entra a evaluar el mock donde la prueba finaliza, a esta propiedad en el método de @Test, se define que atributos espera como respuesta, para decir si al prueba fue exitosa o no.

```java
public class RouteBuilderTest extends CamelTestSupport {

    @Produce(uri = "http4://localhost:9090/restDSL/v1.0.0/students/personal-info")
    protected ProducerTemplate testProducerPost;
	
    @EndpointInject(uri = "mock:outputPost")
    protected MockEndpoint resultEndpointPost;
	
    protected RoutesBuilder createRouteBuilder() throws Exception {
	return new MainRoute();
    }
	
    @Test
    public void testPostUser() throws Exception {
    	
    	resultEndpointPost.expectedHeaderReceived("CamelHttpResponseCode", "200");
    	resultEndpointPost.setExpectedCount(1);
    	    	
    	String contents = new String(Files.readAllBytes(Paths.get("src/test/resources/user.json"))); 
    	
    	testProducerPost.sendBodyAndHeader(contents, "CamelHttpMethod", "POST");
    	resultEndpointPost.assertIsSatisfied();
    }
}
```

Como resultado:

```
[main] MockEndpoint        INFO  Asserting: Endpoint[mock://outputPost] is satisfied
[main] RouteBuilderTest    INFO  ********************************************************************************
[main] RouteBuilderTest    INFO  Testing done: testPostUser(co.edu.uniandes.fuse.labs.restdsl.test.RouteBuilderTest)
[main] RouteBuilderTest    INFO  Took: 0.008 seconds (8 millis)
[main] RouteBuilderTest    INFO  ********************************************************************************
```

[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]