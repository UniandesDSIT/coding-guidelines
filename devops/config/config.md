# Instalación software adicional necesario para las compilaciones de aplicaciones
### 1. Instalación Open JDK 1.8
Las siguientes instrucciones son ejecutadas en Linux RHEL 8, tener en cuenta que la versión de java puede cambiar para cuando ejecute el export

```bash
$ yum install java-1.8.0-openjdk
$ tar zxvf vsts-agent-linux-x64-2.175.2.tar.gz
$ export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.265.b01-0.el8_2.x86_64
$ java -version
openjdk version "1.8.0_256"
OpenJDK Runtime Environment (build 1.8.0_156-b01)
OpenJDK 64-Bit Server VM (build 25.156-b01, mixed mode)
```


### 2 Instalación Maven

Ejecute el siguiente comando 

```bash
$ yum install maven
```

### 3 Instalación Git 
Ejecute el siguiente comando 


```bash
$ yum install git
```

### 4 Instalación node y npm 

Ejecute el siguiente comandos

```bash
$ yum install -y gcc-c++ make
$ curl -sL https://rpm.nodesource.com/setup_14.x | sudo -E bash -
$ yum install nodejs
$ node -v
$ npm -v
```

### 5 Instalación angular 

Instalación angular

```bash
$ npm install -g @angular/cli
```

### 6 Instalación de docker ce 

Ejecute el siguiente comandos

```bash
$ dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
$ dnf list docker-ce
$ dnf install docker-ce --nobest -y
$ systemctl start docker
$ systemctl enable docker

```


### 7 Instalación de kubectl 

Ejecute el siguiente comandos, cree el archivo kubernetes.repo en etc/yum.repos.d/kubernetes.repo con el contenido que se especifica abajo

```bash
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
```

Luego ejecute el siguiente comando una vez se hayan actualizado los repositorios

```bash
$ yum install -y kubectl

```
## Licencia
[MIT](https://choosealicense.com/licenses/mit/)