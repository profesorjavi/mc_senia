# Servidor WEB Apache
https://www.netcraft.com/blog/june-2023-web-server-survey/

## Descripción 
A lo largo de las diferentes tareas  rearemos un servidor de hosting para que los distintos usuarios de la máquina puedan publicar sus páginas. 

## Preparar el entorno.
Para la realización de está práctica utilizaremos una máquina ubuntu server nueva o bien si la tenéis creada debéis utilizar la máquina de ubuntu server que utilizabámos en la DMZ. La configuraremos en adaptador puente con una IP estática.(la que tenéis asignada. De está manera antes de unirla al proyecto podre realizar las pruebas.
En la máquina crearemmos dos usuarios; mortadelo y filemon. La contraseña se corresponderá con el nombre.

## Instalación

```
apt install apache2
```

Para controlar el servicio apache2 podemos usar
```
systemctl [start|stop|restart|reload|status] apache2.service
```
o bien el comando especifico que proporciona el servicio
```
apache2ctl [-k start|restart|graceful|graceful-stop|stop]
```

La opción graceful es un reinicio suave, se terminan de servir las peticiones que están establecidas y cuando se finaliza se hace una reinicio del servidor.

Con esta herramienta podemos obtener también más información del servidor:
* apache2ctl -t : Comprueba la sintaxis del fichero de configuración.
* apache2ctl -M : Lista los módulos cargados.
* apache2ctl -S : Lista los sitios virtuales y las opciones de configuración.


## Estructura de los ficheros de configuración

El fichero principal de configuración de Apache2 es `/etc/apache2/apache2.conf`. En ese fichero se incluyen los ficheros que forman parte de la configuración de Apache2:

	...
	IncludeOptional mods-enabled/*.load
	IncludeOptional mods-enabled/*.conf
	...
	Include ports.conf
	...
	IncludeOptional conf-enabled/*.conf
	IncludeOptional sites-enabled/*.conf

* Los ficheros que se añaden guardados en el directorio `mods-enabled` correponden a los módulos activos.
* Los ficheros añadidos del directorio `sites-enabled` corresponden a la configuración de los sitios virtuales activos.
* Del directorio `conf-enabled` añadimos ficheros de configuración adicionales.
* Por último en el fichero `ports.conf` se especifica los puertos de escucha del servidor.

## Opciones de configuración para los servidores virtuales

Por defecto se indican las opciones de configuración del directorio `/var/www` y de todos sus subdirectorios, por lo tanto los `DocumentRoot` de los virtual host que se crean deben ser subdirectorios del este directorio, por lo tanto encontramos en el fichero `/etc/apache2/apache2.conf` lo siguiente:

	<Directory /var/www/>
	    Options Indexes FollowSymLinks
	    AllowOverride None
	    Require all granted
	</Directory>

Podemos indicar como directorio raíz de nuestros virtual host otro directorio (tenemos que descomentar):

	#<Directory /srv/>
	#    Options Indexes FollowSymLinks
	#    AllowOverride None
	#    Require all granted
	#</Directory>



