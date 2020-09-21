[﻿![alternativetext](https://github.com/UniandesDSIT/Servicio-Fuse-Persona-Persona/raw/master/path/to/DSIT.png)](https://tecnologia.uniandes.edu.co/)         

[ **[Volver al Menú Anterior](https://github.com/UniandesDSIT/coding-guidelines)** ]

# Repositorios Pentaho

## Filandia
Filandia es el servidor que tiene el CedEx de desarrollo para probar los ETL como ambiente de Desarrollo.

http://filandia.uniandes.edu.co:8080/pentaho/Login
Usuario: Admin
Password: password
(Aqui se pueden subir los etl [.ktr/.kjb])

Para poder acceder al servidor se debe ingresar por CyberArk https://pim.uniandes.edu.co/PasswordVault/auth/cyberark/ 
Desde CyberArk se puede obtener acceso por SSH o SFTP para subir o modificar archivos 


## Gamma:
Gamma es el servidor por defecto de pruebas, esta administrado por el CedEx de Middleware.

http://gama.uniandes.edu.co:8080/pentaho/Login
Los accesos deben ser solicitados por usuario a Middleware.

Los unicos que pueden acceder al servidor para despelgar archivos es Middleware

## Cayetano:
Cayetano es el servidor por defecto de producción, esta administrado por el CedEx de Middleware.

https://cayetano.uniandes.edu.co:8443/pentaho/Login
Usuario: IntegracionesDev
Password: ZUwi7lLDQMfAHr5TljYg

Los unicos que pueden acceder al servidor para despelgar archivos adicionales es Middleware
 

_________________________________________________________________________________________________________

<img width="150px" src="../sources/pentaho.png?raw=true"/>
