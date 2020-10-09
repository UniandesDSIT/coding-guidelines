# Instalación Agente Azure
### 1. Descarga del agente 
Las siguientes instrucciones son ejecutadas en Linux RHEL 8

```bash
$ mkdir myagent && cd myagent
$ wget https://vstsagentpackage.azureedge.net/agent/2.175.2/vsts-agent-linux-x64-2.175.2.tar.gz
$ tar zxvf vsts-agent-linux-x64-2.175.2.tar.gz
```


## Instalación

En caso de que el usuario con que esta ejecutando sea root ejecute antes 

```bash
export AGENT_ALLOW_RUNASROOT="1"
```

Ejecuta el siguiente shell siguiendo las instrucciones, como requisito  es necesario tener antes la url del sitio devops, el token de autenticacion y el agent pool en donde se activara el agente.


```bash
$ ./config.sh
```
Haciendo esto el agente recién instalado se comunicara con nuestro sitio devops y si se ejecuto exitosamente el host ya se vera en el agent pool

## Correr el agent 

Para que el proceso quede corriendo en background y no muera al terminar la sesión ejecutar con nohup

```bash
$ nohup ./run.sh &
```

## Licencia
[MIT](https://choosealicense.com/licenses/mit/)