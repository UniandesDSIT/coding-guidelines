[﻿![alternativetext](https://github.com/UniandesDSIT/Servicio-Fuse-Persona-Persona/raw/master/path/to/DSIT.png)](https://tecnologia.uniandes.edu.co/)         

[ **[Volver al Menú Anterior](https://github.com/UniandesDSIT/coding-guidelines)** ]

# Pruebas ETL por medio de Postman

## Despliegue
Se debe desplegar el proyecto en un pentaho server (ya sea filandia o gama, preferiblemente gama)

<img src="../sources/repo.png?raw=true"/>

Adicionalmente se debe solicitar al cedEx de Middleware que suban los archivos necesarios para la ejecución del proyecto y creacion de folders necesarios, Ej:

- /home/pentaho/{proyecto}/{proyecto}.properties
- /home/pentaho/{proyecto}/scripts (En caso de tener scripts en shell)
- /home/pentaho/{proyecto}/csv (En caso de tener que generar archivos csv)


## Ejecución del TEST:
Por medio de Postman una herramienta opensource para la ejecución de test en API's se hace uso de la URL del servert especificando el folder y el job a ejecutar, en este caso:
http://gama.uniandes.edu.co:8080/pentaho/kettle/executeJob?rep=local&job=/public/Uplanner/j-agenda
Es importante que se autentique (user/password) con las credenciales dadas para el servidor.

<src="../sources/postman1.png?raw=true"/>

Una vez se ejecute el test, el servidor respondera una estructura xml donde especifica un jobId, el cual nos permite darle seguimiento al estado del job, por medio de la consola o por medio de otra URL que se puede ejecutar en postman:

http://gama.uniandes.edu.co:8080/pentaho/kettle/jobStatus?id=c51195bd-b091-4a20-a825-ba035da17c5d&xml=Y

<src="../sources/postman2.png?raw=true"/>

Este recurso nos permita saber si el ETL esta en estado:
- Running
- Stoped
- Finished
- Finished (with errors)

_________________________________________________________________________________________________________

<img width="150px" src="../sources/pentaho.png?raw=true"/>
