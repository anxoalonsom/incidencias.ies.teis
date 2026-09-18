# Manual de intalacion de la aplicacion web 

## Decisiones de proyecto

|Elemento|Decision|Version|Justificacion|
|--------|-------|--------|-------------|
|Servidor web|Apache|2|Sencillo de usar,popular |
|Bases de datos|MySQL|8|Experiencia prebia, popular|
|Lenguaje servidor|Python|3|Uso extendido, interesante para ASIR|
|Framework|Flask|3|Sencillo de usar, pensado especificamente para web(formularios,sesiones)|
|Control de sesiones|Git|2.55|Muy extendido|
|Documentacion|MarkDown|-|Muy utilizado con github|


## ¿Que hace un servidor web?

Recibe peticiones HTTP y devuelve recursos al navegador

## Crear respositorio git

1. Crear git

`git init`
2. Crear

`git add`

3. Añadir un comentario
`git commit -m "Commit inicial con readme y página principal con formulario web"`

## Proceso de instalacion / puesta en marcha

1. Actualicacion sistema
`sudo apt update`
`sudo apt upgrade`
2. Instalar git
`sudo apt install git`
3. Instalar VSCODE + plugins:

    - Markdown all in one

4. Instalar apache2

`sudo apt install apache2`

5. Cambiar permisos carpeta /var/ww/html

``` bash 
sudo chown -R $USER:$USER /var/www/html

sudo chmod -R u=rwx,go=rx /var/www/html
```

1. Instalar mysql server

```bash

sudo apt install mysql-servers

```

## Creacion de la bases de datos

## Entrar en SQL 

```bash
1. sudo mysql

2. mysql> create database incidencias;

3. mysql> create user 'incidencias'@'localhost' identified by 'incidencias';

4. mysql> grant all privileges on incidencias.* to  'incidencias'@'localhost';

5. mysql> flush privileges;


```

1. usar tabla
mysql> use incidencias;



1. cree tabala
   mysql> create table registro(
    -> id int auto_increment primary key,
    -> aula varchar(30),
    -> descripcion text,
    -> usuario varchar(20),
    -> estado verchar(30)
    -> );

 
2. mysql> insert into registro (aula, descripcion,usuario,estado) values ('Taller1', 'Pc 24 no arranca', 'ifpereira','ABIERTA');


## Configuracion de git/github

