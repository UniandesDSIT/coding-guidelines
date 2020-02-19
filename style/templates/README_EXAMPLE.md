
```
# Nombre o titulo del proyecto

## 1. Resumen o Descripcion
Proyecto de administracion de notas de estudiantes de ...


## 2. Pre requisitos
Debe tener instaladas en su maquina las siguientes herramientas: 

- Java JDK 1.8 
- Maven: https://maven.apache.org/download.cgi
- Eclipse: http://download.jboss.org/jbosstools/updates/m2e-extensions/m2e-apt


## 3. Instalacion

Desde el directorio /lib ejecutar el siguiente comando 

	mvn install:install-file -Dfile=ojdbc7.jar -DgroupId=com.oracle -DartifactId=ojdbc7 -Dversion=12.1.0.2.0 -Dpackaging=jar


## 4. Como utilizar

Utilizando Eclipse ...

    maven > Update project

	
Para compilar el proyecto utilizar el siguiente comando maven:

    mvn clean install -DskipTests

## 5. Wiki

Puedes encontrar mucho mas de como utilizar este proyecto en nuestra Link a la wiki

## 6. Contribuyentes

Andres Perez (usuario GitHub)

## 7. Version

1.0.1.2 LTS

## 8. Autores
 
Cristian Camacho (usuario GitHub)
Andres Perez (usuario GitHub)

## 9. Soporte

Este software esta soportado por el equipo de ... Si tienes algun inconveniente con el software puedes reportarlo en ....

## 10. Licencia
Este proyecto esta bajo la Licencia GPL, BSD, Software Propietario

## 11. Estado del proyecto

Este proyecto aun esta en fase de desarrollo, actualmente se está trabajando en los modulos...

Este proyecto se encuentra en fase de soporte, actualmente no se están trabajando nuevos desarrollos sobre el mismo.

**Nota: Este proyecto cumple con el estandar definido para la gestión de versionamiento del codigo definido por la DSIT. El cual se encuentra publicado en...**

```
