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



## Intalar python

sudo apt install python3 python3-pip python3-venv -y

1. crear el entorno virtual y activarrlo

```bash
python3 -m venv venv
source venv/bin/activate

``
2. Unstalar flack, conector de bases de datos , comprobar y guardar las dependencias

```bash
pip install flask
pip install mysql-connector-python
pip list
pip freeze >requirements.txt


```

3. hacer el gitingnore

poner dentro del archivo .gitignore 

```bash

venv/
_pycache__\
*.pyc
.env

```


## Rutina de trabajo con flask (venv)

Al empezar:
```bash

source veny/bin/activate
python app.by 'iniciar aplicacion'

control c para terminar
```

## Hacer aplicacion python

```python 
from flask import Flask

app = Flask(_name_)

@app.route("/")
def inicio():
    return "<h1>Incidencias IES Teis</h1>"

if _name_=="_main_":
    app.run(debug=True)

```
1. para ejecutar 

```bash 
cd /var/www/incidencias.ies.teis
source venv/bin/activate

python3 app.py

```

2. 
Al terminar 

ctrol+C para parar app 

deactivate #para salir del entorno

3. comprobamos http://incidencias.ies.teis:5000


## Migracion del formulario a python/falsk

1. creamos una carpeta templates y movemos ahi nuestro index.html
2. modificamos app.py;
   
   ```puthon
   from flask import Flask, render_template

   app = Flask(_name_)

   @app.router("/")
   def inicio():
        return render_template("index.html")

    if _name_=="_name_":
        app.run(debug=True)

    ```
    ## Recibir los datos del formulario

1. añadimos una ruta en app.py para recibir los datos del formulario:

```python
@app.route("/incidencias", methods=["POST"])
def crear_incidencia():

    aula =request.form["aula"]
    usuario = request.form["usuario"]
    descripcion = request.form["descripcion"]


    print("Aula: " + aula)
    print("Usuario: " + usuario)
    print("Descripcion: " + descripcion)

    return "Incidencia creada correctamente"

```

## Visualizacion por pantalla

```python
@app.route("/incidencias", methods=["POST"])
def crear_incidencia():

    aula =request.form["aula"]
    usuario = request.form["usuario"]
    descripcion = request.form["descripcion"]


    print("Aula: " + aula)
    print("Usuario: " + usuario)
    print("Descripcion: " + descripcion)

    return "<h1>Incidencia creada correctamente</h1><ul><li> Aula:" + aula + "</li></ul>"

```


## Introducir los datos en la BD

1. Añadir

```bash

import mysql.connector
```

2. Añadimos esto 

```bash
   conexion = mysql.connector.connect(
      host = "localhost",
      user = "incidencias",
      password = "incidencias",
      database = "incidencias"
    )

    cursor = conexion.cursor()


    sql = "INSERT INTO incidencias (aula, usuario, descripcion) VALUES (%s, %s, %s)"
    valores = (aula, usuario, descripcion, "Abierta")
    cursor.execute(sql, valores)
    conexion.commit()
    cursor.close()
    conexion.close()

```

Comando para ver los usuarios

```bash
select user,host from mysql.user;

```

Para ver los registros

```bash

select * from registro;
```