# Instalación de Asterisk en un servidor EC2

## Objetivo
El alumno aplicará los conocimientos adquiridos hasta el momento instalando un servidor de voz por ip (VOIP) dentro de un servidor de EC2

## Especificaciones
Preparar un reporte en el cual se cubran los siguientes puntos de la manera más detallada posible. En el caso de la instalación de asterisk de deberá reportar paso a paso mediante tomas de pantalla en las cuales se muestre el paso en ejecución.

### Investigación previa:
1. Investigar en que consiste la VOIP.
2. Investigar en que consiste el software Asterisk.
3. Investigar que alternartivas a asterisk existen.
4. Investigar que es un softphone.
5. Investigar que programas de softphone existen para Linux, Window y Mac Os.
6. Investigar que programas de softphone existen para Android & iOS.
7. Investigar que es una NAT Network.
8. Investigar cual es la diferencia entre un puerto TCP y un UDP
9. Investigar cual es la función del archivo sip.conf en asterisk.
10. Investigar cual es la función del archivo extensions.conf en asterisk.

### Instrucciones de instalación de Asterisk
1. Crear Una instancia EC2 dentro de AWS  
  i. Utilizar una imagen del sistema operativo Ubuntu  
  ii. Abrir los puertos inbound:  
    * TCP 22
    * TCP 1723
    * UDP 10000 - 20000
    * UDP 5060
    * UDP 4569
2. Preparar el sistema para instalar asterisk  
  i. Cambiar a modo super usuario  
  ii. Actualizar el sistema mediante `apt-get update`  
  iii. Instalar las dependencias para compilar asterisk:  
  ` apt-get -y install libc6-dev g++ gcc libncurses5-dev make subversion
  `  
3. Compilar Asterisk  
  i. Cambiar al directorio `/mnt` y crear el directorio `source`  
  ii. Cambiar al al directorio `source`  
  iii. Descargar via svn la version 1.4.21.1 (Se recomienda esta versión por estabilidad, se puede usar la mas reciente si se desea).  
  `svn checkout http://svn.digium.com/svn/asterisk/tags/1.4.21.1 asterisk
  `  
  iv. Cambiar al directorio `asterisk`  
  v. Escribir en la terminal `./configure`  
  vi. Correr el comando `make install`  
  vii. Correr el comando `make samples`
4. Configurar Asterik  
  i. Cambiar al directorio /etc/asterisk.  
  ii. Reemplazar el contenido del archivo **sip.conf** con el contenido archivo **sip.conf** de este repositorio.  
  iii. Reemplazar el contenido del archivo **extensions.conf** con el contenido del archivo **extensions.conf** de este repositorio.
5. Ejecutar Asterisk en el servidor.  
  i. Correr el comando `asterisk`  
  ii. Correr el comando `asterisk -r`  
  Nota: En este punto el prompt debe cambiar como se muestra en la imagen.
  ![asterisk service](http://res.cloudinary.com/juancrg90/image/upload/e_sepia/v1457843316/asterisk-r_jxzhsv.png)
6. Configurar el cliente de VOIP  
  i. Este punto se deja a consideración del alumno utilizar el softphone de su preferencia.  
  Si la conexión del cliente con el servidor es exitosa se deberá ver en el prompt de asterisk un mensaje similar al siguiente:
  ![asterisk client reachable](http://res.cloudinary.com/juancrg90/image/upload/e_sepia/v1457843769/client-reachable_idn9ai.png)
  ii. Para verificar que el cliente ya esta correctamente enlazado, marcar `*98` 
  7. Marcando a otro usuario  
    i. Para verificar que el sistema esta correctamente montado, se deberá abrir un issue en este repositorio con los siguientes datos:
      * Usuario
      * contraseña
      * IP del servidor.  

Nota: Se deberá enviar un correo a JuanCrg90@gmail.com para solicitar la prueba de conexión.
      
### Pruebas posteriores a la instalación de asterisk
1. ¿Cual es la función de comando `sip show peers`?
2. ¿Cual es la función de la función `dialplan show local-sip`?
3. ¿Qué concluyes de la presente práctica?

## Instrucciones de entrega
* La fecha limite para solicitar la prueba de conexión es el 1 de abril de 2016 a las 8 pm despues de esa fecha ya no se recibirán solicitudes.
* El reporte se deberá entregar a más tardar  el día 4 de abril de 2016. Se deberá enviar en formato **PDF** al  correo JuanCrg90@gmail.com con la clave de la materia, **En caso de no entregarse de esta manera no se tomará como recibido.**  
