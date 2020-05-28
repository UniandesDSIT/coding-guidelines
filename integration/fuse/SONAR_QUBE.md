[ **[Volver al Menú Principal](MAIN.md)** ]


El objetivo de SonarQube, es ayudarle al equipo de desarrollado a mantener un código limpio que permita detectar bugs, vulnerabilidades y posibles mejoras para asegurar un código legible y  mantenible en el tiempo.
Adicionalmente si el proyecto cuenta con Pruebas Unitarias, SonarQube permite analizar la covertura (alcance) y éxito de las pruebas del proyecto.

Posterior al análisis de código los aspectos a corregir inmediatamente en el proyecto son los **BUGS** y **Vulnerabilidades**, los Code Smells en la medida de lo posible es aconsejable también depurarlos pero no es la prioridad.


***

Para ello se requiere la siguiente configuración y dependencias en el POM.xml:

```xml
<plugin>
	<groupId>org.jacoco</groupId>
	<artifactId>jacoco-maven-plugin</artifactId>
	<version>0.8.4</version>
	<executions>
		<execution>
			<id>default-prepare-agent</id>
			<goals>
				<goal>prepare-agent</goal>
			</goals>
		</execution>
		<execution>
			<id>default-report</id>
			<goals>
				<goal>report</goal>
			</goals>
	   </execution>
	</executions>
</plugin>
```

Una vez el proyecto se encuentre listo para analizar, se utiliza el siguiente comando:

```ssh
mvn clean install test sonar:sonar
```

como resultado desde el panel de SonarQube se visualiza el análisis ejecutado y las sugerencias:

<img src="https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/raw/master/src/main/resources/documentation/sonar_gen.png?raw=true?raw=true" width="900"/>

<img src="https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/raw/master/src/main/resources/documentation/sonar_esp.png?raw=true?raw=true"/>

Para mayor información:
https://docs.sonarqube.org/latest/ 

[ **[Volver al Menú Principal](MAIN.md)** ]
