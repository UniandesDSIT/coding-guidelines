Se debé manejar 4 repositorios en archiva (uno por ambiente) para almacenar los artefactos generados y tener un versionamiento por ambiente con los properties y el código que se va a desplegar, adicional se debería tener un repositorio de librerías de terceros para la construcción y despliegue de los artefactos.

- http://archiva.uniandes.edu.co/archiva/esb.libs-repo/ Repositorio de librerías comunes de terceros
- http://archiva.uniandes.edu.co/archiva/esb.dev-repo/ Repositorio de artefactos snapshot desplegados en desarrollo.
- http://archiva.uniandes.edu.co/archiva/esb.pru-repo/ Repositorio de artefactos snapshot desplegados en pruebas.
- http://archiva.uniandes.edu.co/archiva/esb.qa-repo/ Repositorio de artefactos snapshot desplegados en calidad.
- http://archiva.uniandes.edu.co/archiva/esb.prod-repo/ Repositorio de artefactos release desplegados en Producción.

### Manejo de usuarios y roles de Archiva.

En el archiva deberían existir 3 usuarios principales distribuidos así:

- Admin: Usuario administrador que puede crear repositorios, usuarios y configuración en general del producto.
- Fuse: Usuario para el ESB que permite descargar artefactos de los diferentes repositorios.
- Jenkins: Usuario para el Jenkins que permite subir y descargar artefactos de los diferentes repositorios.

**Permisos:**

- Cicd: read, upload, delete sobre repositorios
- Esb: read sobre repositorios
- Admin: read, upload, delete, manage, annotate sobre repositorios y builds.

**Asociación:**

- Admin - admin
- Fuse – esb
- Jenkins – cicd
