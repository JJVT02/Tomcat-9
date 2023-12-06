# Tomcat-9

## Instalacion 
apt install tomcat10
![](/img/Captura.PNG)

Para gestionar el servicio tomcat:

systemctl stop|start|restart|status tomcat9


## Opciones del servicio tomcat
Para modificar las opciones del servicio tomcat (que se guardan en la variable JAVA_OPTS) tenemos que indicarlas en el fichero /etc/default/tomcat9. Por defectos las opciones que tenemos configuradas son:

JAVA_OPTS="-Djava.awt.headless=true"

Para implantar algunas aplicaciones que necesitan mucha memoria RAM tenemos que añadir una opción indicando la cantidad de memoria que puede usar el servicio, por ejemplo para indicar 1Gb de memoria sería:

JAVA_OPTS="-Djava.awt.headless=true -Xmx1024m"

## Despliegue de aplicaciones mediante la terminal
Implantar una aplicación desde la terminal, tampoco es tan difícil, ya que por defecto cualquier fichero .war que se copie o mueva dentro de l directorio /var/lib/tomcat9/webapps/ se desplegaría automáticamente y dependiendo de nuestra configuración se lanzaría o no.

En mucha documentación sobre tomcat se refiere a la variable de entorno $CATALINA_HOME, en un debian donde hemos instalado tomcat con apt, el valor de esta variable será /var/lib/tomcat9.


AdministraciónPermalink
Esta sección la iniciaremos utilizando una herramienta que nos proporciona la fundación Apache y que nos facilita el despliegue de aplicaciones y manejo del servidor, Tomcat-Manager. Para instalarlo:

# apt install tomcat9-admin
Una vez instalado debemos crear un usuario con el rol manager para acceder a él. Añadimos una línea similar a la siguiente al fichero /etc/tomcat9/tomcat-users.xml:

<role rolename="manager-gui"/>
<user username="tomcat" password="s3cret" roles="manager-gui"/>

## Despliegue de aplicaciones mediante la interfaz webPermalink
Utilizaremos la herramienta anterior para explicar cómo desplegar una aplicación, por ejemplo .war. Simplemente bajamos con el scroll hasta encontrar una sección llamada “WAR file to deploy”. Seleccionamos el fichero .war y le damos al botón “Deploy”.

Puedes bajarte el fichero war desde el siguiente enlace.

