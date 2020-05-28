[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]


### Herramientas para CI & CD 

A continuación, se mencionan el conjunto de herramientas que se recomiendan para el proceso de integración continua:

- **Jenkins**: Servidor de integración continua que permite la automatización de tareas, en donde se indica las fases a cubrir en un build.
- **Git**: Software de control de versiones pensado en la eficiencia y la confiabilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente.
- **SonarQube**: Plataforma de código abierto para el análisis de la calidad de código usando herramientas de análisis estático para obtener métricas que pueden ayudar a mejorar la calidad del código de un programa.
- **Archiva**: Programa que sirve para el manejo de repositorios ofreciendo funciones de mantención como proxying de repositorios remotos, seguridad de acceso, almacenamiento de artefactos, suministro revisión, indexación, estadísticas de uso y escaneo de repositorios.
- **Jboos Fuse**: Plataforma de integraciones.

***


### Manejo de profiles

Dado que el código fuente y en cada rama se van a tener los archivos de cada ambiente al momento de la compilación y generación del artefacto, se debería incluir el archivo respectivo del ambiente para el cual se genera la versión. Esta funcionalidad comúnmente se maneja con los profiles de Maven, junto con las siguientes variables:

- URL de Fuse del ambiente a desplegar
- Ruta del archivo properties que se debe utilizar.

***


### Manejo de Pipelines en Jenkins

Se debería manejar un pipeline por cada una de las rutas, el cual tiene un Jenkinsfile que importa otro Jenkinsfile dependiendo del ambiente al cual se desea desplegar. Este valor debe ser ingresado de forma manual.
En este caso cada ruta debería tener cuatro jenkinsfile (uno por cada ambiente), el cual va a tener los siguientes stages:

- **Jenkinsfile de desarrollo**: Este pipeline se debería ejecutar automáticamente con WebHook cuando se realice un push en el git, debería realizar los siguientes stages:

1. Checkout de la rama dev-sprint-x
1. Clean
1. Copiado de archivos properties de desarrollo (por medio del profile de maven)
1. Package
1. Pruebas unitarias
1. Análisis de SonarQube
1. Subir artefacto a archiva al repositorio de snapshots-dev (por medio de profile de maven)
1. Despliegue en ambiente de desarrollo (por medio de profile de maven)

- **Jenkinsfile de paso a pruebas**: Este pipeline se debería ejecutar manualmente cuando QA realice la certificación, este realiza los siguientes stages:

**Parámetros:**

1. Número de la versión que se va a crear en tag
1. Rama dev-sprint-x

**Stages:**

1. Realiza merge del Branch dev-sprint-x hacia el Branch master
1. Crear un tag de la versión en el Branch master
1. Checkout de la rama master del tag anteriormente creado
1. Clean
1. Copiado de archivos properties
1. Package
1. Pruebas unitarias
1. Análisis de SonarQube
1. Subir artefacto a archiva al repositorio de snapshots-pru
1. Despliegue en ambiente de pruebas

- *Jenkinsfile de paso a calidad:* Este pipeline se ejecutaría manualmente por el gestor de la configuración de la administración por parte de uniandes y realiza los siguientes stages:

**Parámetros:**

1. Número de la versión del Git a desplegar.

**Stages:**

1. Checkout de la rama master de un tag especifico
1. Clean
1. Copiado de archivos properties de calidad
1. Package
1. Pruebas unitarias
1. Análisis de SonarQube
1. Subir artefacto a archiva al repositorio de snapshots-calidad
1. Despliegue en ambiente de calidad


- **Jenkinsfile de paso a producción**: Este pipeline se ejecutaría manualmente por el gestor de la configuración de la administración por parte de uniandes y realiza los siguientes stages:

**Parámetros:**

1. Número de la versión de Git a desplegar

**Stages:**

1. Checkout de la rama master del tag específico
1. Clean
1. Copiado de archivos properties de producción
1. Package
1. Pruebas unitarias
1. Análisis de SonarQube
1. Subir artefacto a archiva al repositorio de releases
1. Despliegue en ambiente de producción


***

### Definiendo un PipieLine

Por medio de un Pipeline **(Jenkinsfile)** que todo proyecto camel debe tener se establecerán las tareas de compilación, análisis de código, pruebas unitarias y despliegue en archiva. 

```pipeline
pipeline {
  agent any
	tools {
     maven 'maven-local'
  }
  stages {
     stage ('Compile Stage') {
        steps {
           sh 'mvn clean compile'
        }
     }
     stage ('SonarQube Stage') {
        steps {
           sh 'mvn clean install'
           sh 'mvn test sonar:sonar'
        }
     }
  
     stage ('Deploy Stage') {
        steps {
           sh 'mvn deploy -DskipTests'
        }
     }
}
```

**Despliegue y generación de release con sus respectivos tags.**

Estos pasos están como plan piloto para una definicion completa de integración y despliegue continuo


- _Creación de llaves ssh_

```
	ssh-keygen
	clip {keyPath}
```

- _Agregar llave privada al agente ssh local de git_

```
	eval $(ssh-agent -s)
	ssh-add ~/.ssh/<private-key>
	//Agregar a los repositorios o al perfil las llave publicas
```

**Comandos de despliegue**

- Sube el pom y jar a archiva

```
    mvn deploy
```

- Commit de los cambios realizados en la version 

```
   git add .
   git commit -m "{description}"
```

- Prepara al versión del release, genera el tag en git, pushea cambios, actualiza la próxima version snapshot

```
   mvn release:prepare
```
- Despliega el release final en archiva

```
   mvn release:perform -Darguments="-Dmaven.javadoc.skip=true"
```

[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]

