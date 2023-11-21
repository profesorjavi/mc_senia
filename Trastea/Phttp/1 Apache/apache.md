# Servidor WEB Apache


## Descripción 
Crearemos un servidor de hosting para que los distintos usuarios de la máquina puedan publicar sus páginas. 

## Preparar el entorno.
Para la realización de está práctica utilizaremos una máquina ubuntu server nueva o bien si la tenéis creada debéis utilizar la máquina de ubuntu server que utilizabámos en la DMZ. La configuraremos en adaptador puente con una IP estática.(la que tenéis asignada. De está manera antes de unirla al proyecto podre realizar las pruebas.
En la máquina crearemmos dos usuarios; mortadelo y filemon. La contraseña se corresponderá con el nombre.

## Instalación
Realiza la instalación de Apache
## Configuración inicial
Crea un directorio en  /var/www/seniaTIC
Crea una página WEB llamada senia.html que sera la página principal de la empresa.
Configura Apache para que cuando accedamos nos muestre está página. 
> Documentroot

> DirectoryIndex

## Errores y logs 
Cambiaremos los ficheros log. Vamos a la configuración de nuestro sitio y modificaremos para que los guarde en un directorio llamado log.
> /var/www/logsenia
 
Cambiaremos el formato en que muestra para que así nos sea más entendible y fácil de comprender. Lo configuraremos de tal manera que muestre la fecha, hora, dirección IP y el código de estado. 

Además personalizaremos los errores 403 y 404. El 403 mostrara un mensaje informativo y el mensaje 404 mmostrará una página personalizada.

1. El registro de errores del servidor, cuyo nombre y ubicación se establece mediante la directiva ErrorLog, es el archivo de registro más importante. Este es el lugar donde Apache httpd enviará información de diagnóstico y registrará cualquier error que encuentre en el procesamiento de solicitudes. 
   > Errorlog

2. La directiva CustomLog se utiliza para registrar solicitudes en el servidor. Se especifica un formato de registro, y el registro opcionalmente se puede condicionar a las características de la solicitud utilizando variables de entorno. 
   > LogFormat 
   
   > Customlog 
   
   AYUDA: https://httpd.apache.org/docs/current/mod/mod_log_config.html 
1. Para personalizar los mensajes de error 
   > ErrorDocument


## Adaptar al proyecto
La maquina virtual la añadiremos al proyecto en la red DMZ y configurares mikrotik para que pueda utilizarse desde el exterior.