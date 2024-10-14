# Instalación de zonas mestras primarias.

 1. Primero descargamos o esqueleto do repositorio:
 git clone https://github.com/A23DanielBS/a23danielbs-bind9skel

 Yo cree una carpeta llamada SRI donde coloqué los archivos de la tarea de tal manera que me quedó esta estructura:

 ![Estructura_del_trabajo](/SRI/Imágenes/estructura.png)

 2. Hacemos un cd  a la carpeta donde vayamos a hacer el archivo compose.yml (En mi caso está en Descargas/SRI)

 3. Editamos el archivo compose.yml que hemos descargado o si lo quereis hacer de 0 lo creamos con docker-compose.yml, de tal manera que la estructura quede de esta manera:

 ![compose.yml](/SRI/Imágenes/compose.png)

 4. Levantamos el contenedor creado con docker-compose up -d para luego acceder a él con un: **$docker exec -it sri-darthvader-1 bash**

 ![Login](/SRI/Imágenes/darthvader_login.png)

 5. Instalamos BIND9 y dnsutils usando los comandos:
 **$apt update
 $apt install -y bind9 dnsutils**

 6. Configuramos como Servidor DNS Caché el BIND9 usando:
 **$dig @localhost www.edu.xunta.es**

![ServidorDNSCaché](/SRI/Imágenes/dig@localhostwww.edu.xunta.es.png)

 7. Editamos el archivo named.conf.options para que quede de esta manera:
 ![named_conf_options](/SRI/Imágenes/named_conf_options.png)

 8. Reiniciamos el BIND9 (service bind9 restart) y verificamos el reenviador:

 ## CREACIÓN DE ZONA PRIMARIA ##

 1. Creamos el archivo de zona **db.starwars.lan**

 2. Agregamos la siguiente configuración:

 ![starwars.lan](/SRI/Imágenes/starwars.lan.png)

 3. Configuramos o archivo **named.conf.local** agragando lo siguiente:

![ZonaDirecta](/SRI/Imágenes/ZonaDirecta.png)

  ## CREACIÓN DE ZONA INVERSA ##

1. Creamos el archivo db.20.168.192

2. Agregamos la siguiente configuración:

![db.192.168.20](/SRI/Imágenes/db.192.168.20.png)

3. Volvemos a configurar **named.conf.local** y agregamos la zona inversa:

![ZonaInversa](/SRI/Imágenes/ZonaInversa.png)

  ## COMPROBACIÓN ##

1. Reiniciar BIND9 (service bind9 restart)

2. Comprobamos la resolución de los nombres:

![ResoluciónNome](/SRI/Imágenes/ResolucionNome.png)
 










