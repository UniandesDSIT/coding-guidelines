# Guía de Desarrollo de Software

Versión: 1.2.0

## Objetivo

El siguiente documento guía que contiende un conjunto de buenas prácticas y procedimientos diseñados para el desarrollo de nuevas soluciones lideradas por la [Dirección de Servicios de Información y Tecnología](https://tecnologia.uniandes.edu.co) de la [Universidad de los Andes](https://uniandes.edu.co) u otras áreas que desean construir soluciones que serán soportadas posteriormente por la DSIT. Estos son más que todo recomendaciones y guías, por lo tanto siéntase libre de proponer cambios para este documento en un pull request o comunicándote con el equipo de desarrollo.

## ¿Qué debería saber antes de empezar?

### La DSIT y los CedEx

La Dirección de Servicios de Información y Tecnología es una unidad organizativa de la Universidad de los Andes, compuesta por más de 10 Centros de Experiencia (en adelante CedEx). Esta organización pretende dar cabida a todos los proyectos generados por los distintos CedEx que se relacionen con desarrollo de software interno, diseño de productos y posiblemente código abierto generado por estas.

## Contenido

1. Lineamientos para el versionamiento de código
	* [Manejo de ramas](./versioning/BRANCHES.md)
	* [Uso de ambientes](./versioning/ENVIRONMENTS.md)
	* [Nombramiento de versiones](./versioning/VERSIONING.md)
2. Lineamientos para codificación y documentación
	* [Recomendaciones de estilo de código](./style/STYLE_GUIDE.md)
	* [Guías de documentación y escritura de commits](./style/COMMITS.md)
	* [Sobre la documentación de proyectos](./style/DOCS.md)
	* [Cómo debe ser el README](./style/ABOUT_README.md)
	* [Cómo reportar un bug](./style/WRITE_BUG.md)	
	* [Cómo debe ser un Pull request](./style/PULL_REQUESTS.md)
3. Lineamientos para los procesos Desarrollo de Integraciones
	* [Integración de Servicios y API's ESB - Fuse](./integration/fuse/MAIN.md)
	* [Integración procesos ETL - Pentaho DI](./integration/pentahodi/MAIN.md)
