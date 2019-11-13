# Vagrant-Docker

## Requisitos

## Herramientas
- Virtual Box (versión 6 o superior): https://www.virtualbox.org/
- Git: https://git-scm.com/
- Vagrant: https://www.vagrantup.com/downloads.html

## Pasos a realizar
Una vez instaladas las herramientas mencionadas anteriormente, realizar los siguientes pasos:
- Crear un directorio **docker** en la ruta deseada
- Abrir una consola de comandos y acceder al directorio creado anteriormente
- Descargar el repositorio desde github con el siguiente comando
```
git clone https://github.com/shokone/Vagrant-Docker.git
```
- Una vez terminada la ejecución del anterior comando, acceder a la carpeta creada "Vagrant-Docker" y ejecutar el siguiente comando para levantar el entorno
```
vagrant up
```
- El anterior comando tardará en levantar, pero su resultado debe de ser la construcción de 1 máquina virtual que termina arrancada.
- Para comprobar que todo ha ido bien, ejecutar el siguiente comando para acceder a la máquina bastión.
```
vagrant ssh bastion
```
- Dentro de esta instancia, ejecutar el siguiente comando:
```
docker images
```
- Si el anterior comando devuelve una lista en la cual se incluye una imagen con nombre **centos** es que está todo OK y podemos dar por completada la creación del entorno de pruebas.


## Otras opciones de vagrant
Accedemos a la carpeta donde se encuentran los ficheros de configuración del entorno y podremos cambiar su estado con los siguientes comandos:
- Para comprobar el estado actual de vagrant podemos utilizar el siguiente comando:
```
vagrant status
```
- Para parar la máquina deseada usaremos el siguiente comando:
```
vagrant halt
```
- Para suspender la misma podemos utilizar:
```
vagrant suspend 
```
- Para levantar la instancia de nuevo usaremos el comando:
```
vagrant up
```
- Para destruir el entorno usaremos el siguiente comando:
```
vagrant destroy 
```
