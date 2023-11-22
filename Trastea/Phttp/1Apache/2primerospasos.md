# Primeros pasos

## Repaso a la configuración inicial 

El servidor web Apache 2.4 se instala por defecto con la configuración de un servidor virtual. La configuración de este sitio la podemos encontrar en:
```
/etc/apache2/sites-available/000-default.conf
```
Y por defecto este sitio virtual está habilitado, por lo que podemos comprobar que existe un enlace simbólico a este fichero en el directorio /etc/apache2/sites-enabled:
```
lrwxrwxrwx 1 root root   35 Oct  3 15:24 000-default.conf -> ../sites-available/000-default.conf
```

En este archivo encontramos una configuración por defecto que vamos a ir modificando 
```apache
<VirtualHost *:80>	
	#ServerName www.example.com
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
En el fichero de configuración general /etc/apache2/apache2.conf nos encontramos las opciones de configuración del directorio padre del indicado en la directiva DocumentRoot 

```apache
<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>
```

Por lo tanto podemos acceder desde un navegador a la ip de nuestro servidor (también podemos usar un nombre del servidor) y accederemos a la página de bienvenida del servidor que se encuentra en:

/var/www/html/index.html

Por defecto los errores de nuestro sitio virtual se guardan en /var/log/apache2/error.log y los accesos a nuestro servidor se guardan en /var/log/apache2/access.log


## Vamos a lo práctico
### WEB base
1. Prepara una página WEB que simule la web de la empresa con un par de páginas y que una de las páginas contenga a su vez un par de imagenes. 
   * Llama a la página principal senia.html. 
   * Aloja esta web en el directorio /var/www/seniaTIC
2. Configura Apache para que cuando accedamos http://localhost nos muestre está página. 
> DocumentRoot

> DirectoryIndex

### Errores y logs 
1. Cambiaremos los ficheros log. Vamos a la configuración de nuestro sitio y modificaremos para que los guarde en un directorio llamado log.
	> /var/www/logsenia
 
1. Cambiaremos el formato en que muestra para que así nos sea más entendible y fácil de comprender. Lo configuraremos de tal manera que muestre la fecha, hora, dirección IP y el código de estado. 

1. Además personalizaremos los errores 403 y 404. El 403 mostrará un mensaje informativo y el mensaje 404 mostrará una página personalizada.


NOTAS: 

El registro de errores del servidor, cuyo nombre y ubicación se establece mediante la directiva ErrorLog, es el archivo de registro más importante. Este es el lugar donde Apache httpd enviará información de diagnóstico y registrará cualquier error que encuentre en el procesamiento de solicitudes. 
   > Errorlog

La directiva CustomLog se utiliza para registrar solicitudes en el servidor. Se especifica un formato de registro, y el registro opcionalmente se puede condicionar a las características de la solicitud utilizando variables de entorno. 
   > LogFormat 
   
   > Customlog 
   
   AYUDA: https://httpd.apache.org/docs/current/mod/mod_log_config.html 
Para personalizar los mensajes de error 
   > ErrorDocument


## Adaptar al proyecto
La maquina virtual la añadiremos al proyecto en la red DMZ y configurares mikrotik para que pueda utilizarse desde el exterior.