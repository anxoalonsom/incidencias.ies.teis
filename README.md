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

6. Crear el gihub del proyecto


## Creacion de la bases de datos