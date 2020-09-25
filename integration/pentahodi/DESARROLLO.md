[﻿![alternativetext](https://github.com/UniandesDSIT/Servicio-Fuse-Persona-Persona/raw/master/path/to/DSIT.png)](https://tecnologia.uniandes.edu.co/)         

[ **[Volver al Menú Anterior](https://github.com/UniandesDSIT/coding-guidelines/blob/master/integration/pentahodi/MAIN.md)** ]

# Desarrollo ETL

## Uso de Properties
Para facilitar el uso de conexiones a servidores entre ambientes de dllo/qa/prod para bases de datos/sftp y otros se debe ejecutar una transformacion que permite leer un archivo .properties que debe estar por defecto en la ruta:

/home/pentaho/{nombre_proyecto}/{proyecto}.properties

<img src="../sources/job.png?raw=true"/>

## Conexiones BD:
Los properties son cargados como variable en pentaho y se puede hacer uso de ellas en cualquier job o transformacion del proyecto para este caso una base de datos:

<img src="../sources/tr.png?raw=true"/>

Uso de variables en la conexion:

<img src="../sources/db.png?raw=true"/>


## Conexiones SFTP:

Uso de properties en una conexion SFTP

<img src="../sources/sftp.png?raw=true"/>


_________________________________________________________________________________________________________

<img width="150px" src="../sources/pentaho.png?raw=true"/>
