[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]


La estructura de directorios y paquetes del proyecto va acorde a la razón de ser del archivo y su contenido, el dominio por defecto para los proyectos: package **(co.edu.uniandes.fuse.{proyect})**

***

### Lógica de enrutamiento

- **Beans :**
Clases utilitarias que permiten hacer pequeños cambios o abstraer logica de negocio requerida para la ruta, tal como calculos matematicos o el validar especifico objeto para tomar una desicion, generalmente utiliza el exchange message de camel (header/body).
- **Models :**
Clases que mapean una estructura de datos de una entidad, generalmente se usa para definir las datos de entrada y salida del servicio, tal como un recurso (persona, producto, etc), este modelo irá ligado al modelo canonico.
- **Processors :**
Clases que abstraen logica de procesamiento donde se requeire un esfuerzo más alto a diferencia de un bean, para leer, validar, transformar una petición o una respuesta, generalmente utiliza el exchange message de camel (header/body).
- **Agreggators :**
Clases que permiten agregar o enriquecer el contenido de un objeto o mensaje, generalmente utiliza el exchange message de camel (header/body).
- **Routes :**
Clases que continen la logica del servicio y estan basadas en camel, ademas de hacer uso de los diferentes tipos de clases previamente mencionados

<img src="https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/raw/master/src/main/resources/documentation/dir_java.png?raw=true?raw=true"/>

***

### Recursos del proyecto

- **Camel Context** : Archivo XML que define el contexto para el arranque del proyecto en jboss fuse.

- **Plantillas (Velocity)** : Archivos que permiten definir una plantilla re-utilizable.

- **Archivos de Propiedades (Properties)** : Archivos donde se define una serie parámetros                                    (llave-valor) con el fin de centralizar datos para configuraciones.

<img src="https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/raw/master/src/main/resources/documentation/dir_resources.png?raw=true?raw=true"/>

***

### Recursos fabric8


***

### Lógica y Recursos de Pruebas Unitarias

Para el desarrollo y ejecución de pruebas unitarias, las clases java y recursos requeridos se deben alojar en el directorio src/main/test:

<img src="https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/raw/master/src/main/resources/documentation/dir_test.png?raw=true?raw=true"/>

***

### Proyectos dependientes

- **Fuse Parent Pom**: Este proyecto **"co.edu.uniandes.fuse.core.parent-pom"** centraliza las dependencias para la creación de API's Rest, de este modo se mantiene un marco de versiones y dependencias estandarizado y desacoplado.

- **Fuse Utils**: Este proyecto **"co.edu.uniandes.fuse.core.utils"** centraliza logica general de los servicios en forma de processor y beans, para que sean reutilizados y no escritos repetidamente en cada proyecto.

- **Fuse DataSource**: Este proyecto **"co.edu.uniandes.datasources"** centraliza la conexión al datasource de banner para la consulta hacia la Base de Datos.

***

### Archivos complementarios

Ubicados en la raiz del proyecto

- **POM.xml** : Archivo XML con la definición del proyecto maven, dependencias & plugins.
- **README.md** : Archivo con la documentación especifica del proyecto 
- **Jenkinsfile** : Archivo que contienen el Pipeline que ejecutará Jenkins o Azure Pipelines.

<img src="https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/raw/master/src/main/resources/documentation/dir_dependencies.png?raw=true?raw=true"/>

***

[ **[Volver al Menú Principal](https://github.com/UniandesDSIT/Fuse-Lab-RestDsl/wiki)** ]