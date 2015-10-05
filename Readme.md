DEBIAN 7 PARA LA JA
---

Instrucciones de postinstalación para **Debian 7 (wheezy) 64 bits**

Los archivos necesarios los podmeos obtener der  (también los podemos descargar de sus fuentes originales, que estarán más actualizados):

[http://bit.ly/debian_install_ja](http://bit.ly/debian_install_ja)



## Pasos previos



Sincronizamos el índice de paquetes desde sus fuentes:

    apt-get update


Añadimos el usuario a lista de sudo:

    su -
    vi  /etc/sudoers

> :w! y  :q  <- Salir así para Forzar grabación

    vi /etc/sudoers
    usermod -G sudo -a soporte

Habilitamos servidor ssh (si queremos poder supervisar remotamente):

    apt-get install openssh-server 

Herramientas de búsqueda de Gnome:

    apt-get install gnome-search-tool
    

## Libreoffice
### Libreoffice (usando .deb)

 Primero es necesario descargar los fichero de la página de [Libreoffice en español](http://es.libreoffice.org/descarga/)

    tar -xvf LibreOffice_4.1.4_Linux_x86-64_deb.tar.gz
    tar -xvf LibreOffice_4.1.4_Linux_x86-64_deb_langpack_es.tar.gz
    tar -xvf LibreOffice_4.1.4_Linux_x86-64_deb_helppack_es.tar.gz

Descromprimimos los paquetes

    dpkg -i LibreOffice_4.1.4.2_Linux_x86-64_deb/DEBS/*.deb
    dpkg -i LibreOffice_4.1.4.2_Linux_x86-64_deb_langpack_es/DEBS/*.deb
    dpkg -i LibreOffice_4.1.4.2_Linux_x86-64_deb_helppack_es/DEBS/*.deb


### Libreoffice (con repositorio debian backports) *RECOMENDADO*

Debemos tener esta línea en el fichero `/etc/apt/sources.list` (o en alguno de los `/etc/apt/*.list`)
     
    ## Backports
    deb http://ftp.debian.org/debian/wheezy-backports main

Finalmente, instalamos libreoffice:

    sudo apt-get -t wheezy-backports install libreoffice
    sudo apt-get -t wheezy-backports install libreoffice-l10n-es
    sudo apt-get -t wheezy-backports install libreoffice-help-es


## Google Chrome


    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
    dpkg -i google-chrome-stable_current_amd64.deb
    apt-get -f install
    

## Cliente VPN    

Optenemos la última versión para la JA del cliente VPN *Forticlient*:
    
    wget http://vpn.juntadeandalucia.es/forticlientsslvpn_linux_4.0.2287.tar.gz
    
    tar -zxvf forticlientsslvpn_linux_4.0.2287.tar.gz -C /opt
    cp forticlient.png /opt/forticlientsslvpn/
    
    dpkg --add-architecture i386 # enable multi-archapt-get update
    apt-get install libc6:i386 # install base 32bit libraries
    apt-get install libgtk2.0-0:i386
    apt-get install libsm6:i386   
    apt-get install libstdc++6:i386
    apt-get install ia32-libs-gtk



Ya podemos ejecutar el comando (desde el terminal o haciendo doble click):

    /opt/forticlientsslvpn/forticlientsslvpn

## Cliente SAMBA (CIFS)    

apt-get install cifs-utils


# Instalación de Firefox y Thunderbird

Obtenido de [aquí](http://josecartagena.info/2011/11/08/installing-firefox-and-thunderbird-in-debian/) 

Añadimos el repostorio *Linux Mint* 


    echo deb http://packages.linuxmint.com debian import | sudo tee -a /etc/apt/sources.list
    wget http://packages.linuxmint.com/pool/main/l/linuxmint-keyring/linuxmint-keyring_2009.04.29_all.deb
    sudo dpkg -i linuxmint-keyring_2009.04.29_all.deb

Ya podemos instalar Firefox y Thunderbird:

    sudo apt-get update
    sudo apt-get install firefox firefox-l10n-es  thunderbird thunderbird-l10n-es


Por defecto, se utilizad [DucDuckGo](https://duckduckgo.com) como motor de búsqueda. Si queréis cambiarlo por el de Google:


[https://www.evernote.com/shard/s3/sh/174bfcdc-1071-41ff-ab42-8a1f6034e943/437f72729e6a4974191403f9566ee003](https://www.evernote.com/shard/s3/sh/174bfcdc-1071-41ff-ab42-8a1f6034e943/437f72729e6a4974191403f9566ee003)



## Instalar JAVA [Java:]



### Instalar versión obsoleta y con fallos de seguridad (*Recomendado por Red Profesional*)

Seguir la instrucciones de [Red profesional](https://redprofesional.juntadeandalucia.es/blog/view/2852/hacer-funcionar-el-cliente-de-firma-con-cualquier-firefox-en-ubuntu)



> Cuando usamos linux nos damos cuenta de lo difícil que es hacer que algo tan poco estandarizado como el cliente de firma funcione en las nuevas distribuciones de firma...
> El problema principal del cliente de @firma es que, si éste utiliza el applet, y no el jnlp (buscad en google si no sabeis que es lo que es), el applet intenta leer desde una carpeta de nuestro home el jar instalado del cliente. Ésto estaba permitido en las versiones de java anteriroes a la jre 1.6 update 24, pero a partir de esa versión el applet da un error de Permission denied, ya que no está permitido leerlo tal y como se ha desarrollado.
> El problema es, por tanto, de java y no de la version del navegador Firefox o de si nuestra distribución es de 32 o 64 bits, por lo que hacerlo funcionar en distribuciones modernas no es muy difícil.
> Esto se soluciona instalando una version de java anterior a la 1.6.0.24.
> El segundo problema es que el applet busca las librerías de seguridad nss de mozilla en un path diferente al que utiliza ubuntu desde la 11.04. El applet las busca en /usr/lib y la distribución las pone en /usr/lib/i386-linux-gnu o /usr/lib/x86_64-linux-gnu/ según tengamos una distribución de 32 o 64 bts.
> Así, los pasos para hacerlo funcionar son:


Estas son las instrucciones (con ligeros retoques)

1.- Descargar el jre correcto de http://www.oracle.com/technetwork/java/javasebusiness/downloads/java-archive-downloads-javase6-419409.html#jre-6u20-oth-JPR

Para más facilidad, también está disponible [aquí](https://app.box.com/s/lz8t7viyw4lxf02i35ak)



2.- Descomprimirlo (ejecutando el .bin) y copiándolo a:

    chmod +x jre-6u21-linux-x64.bin
    ./jre-6u21-linux-x64.bin

    
    sudo mkdir -p /usr/lib/jvm/jre1.6.0_21/   
    sudo mv jre1.6.0_21/* /usr/lib/jvm/jre1.6.0_21/


3.- Instalar una alternativa para ejecutar java con los binarios descarados

    sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.6.0_21/bin/java" 1
    sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jre1.6.21/bin/java 0




4.- Establecer la alternativa

    sudo update-alternatives --config java

    > Existen 6 opcioens para la alternativa java (que provee /usr/bin/java).
    >
    >   Selección   Ruta                                            Prioridad  Estado
    >   0            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      modo 
    >  automático
    >   1            /usr/bin/gij-4.7                                 1047      modo manual
    >   2            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      modo manual
    >   3            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      modo manual
    > * 4            /usr/lib/jvm/jre1.6.0_21/bin/java                1         modo manual



Seleccionamos la opción con `jre1.6.0_21` (en nuestro caso `4`)

Borrar el plugin de java anterior(si no lo teneis saldrá un error)

    rm -v ~/.mozilla/plugins/libnpjp2.so

Enlazar el plugin nuevo

    ln -s /usr/lib/jvm/jre1.6.0_20/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

    sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jre1.6.0_21/lib/amd64/libnpjp2.so" 1 
    sudo update-alternatives --config mozilla-javaplugin.so
    
Instalar paquete con librerías NSS:    
    
    sudo apt-get install libpam-ccreds

Enlazar las librerías de nss para que las encuentre el applet:

    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss3.so /usr/lib/libnss3.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss3.so.1d /usr/lib/libnss3.so.1d
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss_compat.so /usr/lib/libnss_compat.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss_dns.so /usr/lib/libnss_dns.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss_files.so /usr/lib/libnss_files.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss_hesiod.so /usr/lib/libnss_hesiod.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss_nisplus.so /usr/lib/libnss_nisplus.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnss_nis.so /usr/lib/libnss_nis.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnssutil3.so /usr/lib/libnssutil3.so
    sudo ln -s /usr/lib/x86_64-linux-gnu/libnssutil3.so.1d /usr/lib/libnssutil3.so.1d
    sudo ln -s /usr/lib/x86_64-linux-gnu/nss /usr/lib/nss

Si se utilizar una distribucion de linux de 32 bits cambiad x86_64-linux-gnu por i386-linux-gnu

Por último, verificamos JAVA:

[https://www.java.com/verify/](https://www.java.com/verify/)


> Con estas instrucciones debería de funcionaros cualquier navegador firefox en linux con las aplicaciones corporativas que usen el applet.

    

### Instalar versión actualizada java (*Recomendable*):

Descargamos la [última versión de Java](https://www.java.com/es/download/linux_manual.jsp?locale=es). Elegimos las versión NO RPM.

    tar -xvf jre-7u51-linux-x64.tar.gz
    sudo mkdir -p /usr/lib/jvm/jre1.7.0/
    sudo mv jre1.7.0_51/* /usr/lib/jvm/jre1.7.0/
    sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jre1.7.0/bin/java 0
    sudo update-alternatives --config java

    sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jre1.7.0/lib/amd64/libnpjp2.so" 1 
    sudo update-alternatives --config mozilla-javaplugin.so 
 
	sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jre1.7.0/bin/javaws" 1   
    sudo update-alternatives --config javaws
 
 Establecemos lo ajustes de seguridad de java:

    /usr/lib/jvm/jre1.7.0/bin/ControlPanel
      
 ![Ajustes de seguridad de JAVA](https://dl.dropbox.com/s/lxv9v045nlpq0qs/java%20ajustes%20de%20seguridad%20baja.png)
    
Por último, verificamos JAVA:

[https://www.java.com/verify/](https://www.java.com/verify/)


### Actualizar versión de java


Entramos desde terminal como root:

	sudo su

Miramos dónde tenemos instalada la versión anterior:

	update-alternatives --list java 
	update-alternatives --list javaws
	update-alternatives --list mozilla-javaplugin.so

En nuestro caso vemos que es en `/usr/lib`. Descomprimimos la versión de java en ese directorio:

	tar -zxvf jre-7u80-linux-x64.tar.gz -C /usr/lib/jvm	

Instalamos la versión de java y 

+ Actualización java

```
# update-alternatives --install /usr/bin/java java /usr/lib/jvm/jre1.7.0_80/bin/java 0
# update-alternatives --config java
Existen 8 opciones para la alternativa java (que provee /usr/bin/java).

  Selección   Ruta                                            Prioridad  Estado
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      modo automático
  1            /usr/bin/gij-4.7                                 1047      modo manual
  2            /usr/bin/gij-4.9                                 1049      modo manual
  3            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      modo manual
  4            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      modo manual
  5            /usr/lib/jvm/jre1.6.0_21/bin/java                1         modo manual
  6            /usr/lib/jvm/jre1.6.0_45/bin/java                0         modo manual
* 7            /usr/lib/jvm/jre1.7.0/bin/java                   0         modo manual
  8            /usr/lib/jvm/jre1.7.0_80/bin/java                0         modo manual

Pulse <Intro> para mantener el valor por omisión [*] o pulse un número de selección: 8
update-alternatives: utilizando /usr/lib/jvm/jre1.7.0_80/bin/java para proveer /usr/bin/java (java) en modo manual
```

+ Actualización javaws

```
# update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/jre1.7.0_80/bin/javaws 0
# update-alternatives --config javaws
Existen 2 opciones para la alternativa javaws (que provee /usr/bin/javaws).

  Selección   Ruta                                 Prioridad  Estado
------------------------------------------------------------
* 0            /usr/lib/jvm/jre1.7.0/bin/javaws      1         modo automático
  1            /usr/lib/jvm/jre1.7.0/bin/javaws      1         modo manual
  2            /usr/lib/jvm/jre1.7.0_80/bin/javaws   0         modo manual

Pulse <Intro> para mantener el valor por omisión [*] o pulse un número de selección: 2
update-alternatives: utilizando /usr/lib/jvm/jre1.7.0_80/bin/javaws para proveer /usr/bin/javaws (javaws) en modo manual
```

+ Actualización mozilla-javaplugin.so

```
# update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so "mozilla-javaplugin.so" /usr/lib/jvm/jre1.7.0_80/lib/amd64/libnpjp2.so 0
# update-alternatives --config mozilla-javaplugin.so
Existen 3 opciones para la alternativa mozilla-javaplugin.so (que provee /usr/lib/mozilla/plugins/libjavaplugin.so).

  Selección   Ruta                                            Prioridad  Estado
------------------------------------------------------------
  0            /usr/lib/jvm/jre1.7.0/lib/amd64/libnpjp2.so      1         modo automático
  1            /usr/lib/jvm/jre1.6.0_21/lib/amd64/libnpjp2.so   1         modo manual
* 2            /usr/lib/jvm/jre1.7.0/lib/amd64/libnpjp2.so      1         modo manual
  3            /usr/lib/jvm/jre1.7.0_80/lib/amd64/libnpjp2.so   0         modo manual

Pulse <Intro> para mantener el valor por omisión [*] o pulse un número de selección: 3
update-alternatives: utilizando /usr/lib/jvm/jre1.7.0_80/lib/amd64/libnpjp2.so para proveer /usr/lib/mozilla/plugins/libjavaplugin.so (mozilla-javaplugin.so) en modo manual
```

Comprobamos la versión actualizada

```
# java -version
java version "1.7.0_80"
Java(TM) SE Runtime Environment (build 1.7.0_80-b15)
Java HotSpot(TM) 64-Bit Server VM (build 24.80-b11, mixed mode)
```

### Tareas post Instalación/Actualización ###


Podemos probar la 

<https://www.java.com/es/download/installed.jsp>


Comprobamos la seguridad. Desde un terminal como usuario (no root) ejecutamos:


	$ /usr/lib/jvm/jre1.7.0_80/bin/ControlPanel



![Consola JAVA - Seguridad](https://dl.dropbox.com/s/zrq6fh5vgr5z2pk/Configuraci%C3%B3n%20Consola%20JAVA-Seguridad.png)


## Tipos de letra


Copiamos y activamos las fuentes:

     sudo cp Tipos\ de\ Letra/* /usr/share/fonts/
     ls -altr /usr/share/fonts/
     
Instalamaos *Font-manager*

sudo apt-get install font-manager 


## Hardware wifi con controlador propietario

Añadimos repositorio non-free:

    sudo vi /etc/apt/sources.list
    
> deb http://http.debian.net/debian/ wheezy main contrib non-free

    sudo apt-get update && apt-get install firmware-iwlwifi
    sudo modprobe -r iwlwifi 
    sudo modprobe iwlwifi

## Multimedia

Añadimos repositorio multimedia:

    sudo vi /etc/apt/sources.list

> deb http://www.deb-multimedia.org wheezy main non-free

    sudo apt-get install deb-multimedia-keyring  
    
Instalamos paquetes:    
    
    
    apt-get install flashplugin-nonfree
    apt-get install w64codecs
    apt-get install fonts-freefont-otf
    apt-get install ttf-mscorefonts-installer
    apt-get install faad gstreamer0.10-ffmpeg gstreamer0.10-x gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly ffmpeg lame twolame vorbis-tools libquicktime2 libfaac0 libmp3lame0
    apt-get -f install
    apt-get install faad gstreamer0.10-ffmpeg
    apt-get install gstreamer0.10-x gstreamer0.10-fluendo-mp3
    apt-get install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
    apt-get install libxvidcore4 libavcodec53 libavcodec54 libavdevice53 libavdevice54 libstdc++5
    apt-get install ffmpeg lame twolame vorbis-tools libquicktime2 libfaac0 libmp3lame0 libxine1-all-plugins
    apt-get install sox libxvidcore4 libavcodec53 libavcodec54 libavdevice53 libavdevice54 libstdc++5
    apt-get install libxine2-all-plugins libdvdnav4 libmad0 libavutil51 


## Skype 

Decargamos .deb de la web de Skype.

Instalamos paquete:

    sudo dpkg -i skype-debian_4.2.0.13-1_i386.deb 
    sudo apt-get -f install


## Virtualbox:

Añadimos repostiorio

    sudo echo "deb http://download.virtualbox.org/virtualbox/debian wheezy contrib" | sudo tee -a  /etc/apt/sources.list
    wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

Instalamos 

    sudo apt-get update 
    sudo apt-get install virtualbox-4.3

Instalar guest addition

## Gparted

    sudo apt-get install gparted


## Solución de problemas con touchpad:

Editaremos el archivo “/etc/rc.local” como root con el editor que nosotros querramos, en mi caso lo hago con el comando “nano“:

    sudo vi /etc/rc.local
    

Una vez abierto el archivo con el editor, deberemos agregar las siguientes lineas al archivo:

    rmmod psmouse 
    modprobe psmouse proto=imps

## Impresión


Instalamos paquetes:

    sudo apt-get install cups cups-filters cups-bsd system-config-printer python-smbc smbclient

### Preparación Configuración Impresora ###


#### Impresora KONICA MINOLTA 500/420/360PS(P):

Instalamos el filtro [faviouspscf110mu.pl](https://www.dropbox.com/s/13jow66pclvi60d/fvariouspscf110mu.pl?dl=0)

    sudo cp cups/fvariouspscf110mu.pl /usr/lib/cups/filter/

Instalamos la impresora usando [este](https://dl.dropbox.com/s/bulymksppbpiaxl/IMP-CEICE-KPL-4NO.ppd) fichero .ppd

#### Impresora KONICA MINOLTA C284e/C554 ###

En este caso utilizamos el [este](https://www.dropbox.com/s/2i0xctj8as1d6xj/KOC554SX.ppd?dl=0) fichero .ppd

### Instalación

Utilizamos el gestor de configuración de impresoras antiguo:

    /usr/bin/python /usr/bin/system-config-printer


Añadir impresora de red:

![Nueva impresora red SMB](https://dl.dropbox.com/s/iaoao0lfwxr4aqn/a%C3%B1adir%20nueva%20impresora.png)




## Adobe Reader

Descargamos paquete de [Adobe](http://get.adobe.com/es/reader/otherversions/). Recomendamos versión 9.5 o superior (sólo disponible en inglés)


    dpkg -i AdbeRdr*.deb 
    apt-get -f install

Configuramos un acceso director desde *Programas*:

    cp ~/.local/share/applications/Adobe*.desktop /usr/share/applications
    cd /usr/share/applications 
    chown root:root Adobe*.desktop
    chmod -x Adobe*.desktop


## Busqueda gnome

Habilitar la búsqueda de fichero en gnome

	gnome-search-tool

Añadir panel de búsqueda en la barra de menu

## Gnome-do


    apt-get install gnome-do

Después configurarlo:

- Tecla disparadora
- Habilitar inicio automático
- Habitar el complementeo *Files and Folder*


## Teamviewer

Descargamos el paquete de la web de teamvier.


    dpkg-i teamviewer_linux_x64.deb
    apt-get -f install 

## Tarjeta criptográfica
### DNIe

Descargar el paquete de la [web descargas FNMT](https://www.sede.fnmt.gob.es/descargas/descarga-software):


[GNU/LINUX Debian 7.0 (Whezzy) - 64 bits](https://www.sede.fnmt.gob.es/documents/11614/144341/libpkcs11-fnmtdnie_1.2.0_Debian_7_64bits.deb/5787c518-13e3-4462-a950-7bf73e1e5013)

Instalamos estos paquetes y el .deb:


    sudo apt‐get install pinentry‐gtk2 pcscd libassuan0
    sudo dpkg ‐i libpkcs11-fnmtdnie_1.2.0_Debian_7_64bits.deb
    


Configurar Firefox:


* Ir a “Preferencias / Avanzado / Cifrado / Dispositivos de seguridad” de Firerfox
* Seleccionar “Cargar”
* Darle un nombre al módulo (Por ejemplo "FNMT-DNIE Módulo P11").
* Indicar manualmente la ruta del módulo:

	* /usr/lib/libpkcs11‐fnmtdnie.so

Una vez instalado el módulo, se deber importar el certificado raíz de la FNMT y del DNIe.
* Ir a “Preferencias / Avanzado / Cifrado / Ver certificados” de Firerfox
* Seleccionar "Importar"
* Indicar manualmente la ruta del certificado raíz: /usr/share/libpkcs11‐fnmtdnie/FNMTClase2CA.crt
* Marcar las tres casillas de confianza.
Realizar los mismos pasos para importar el certificado raíz del DNIe. Este se encuentra ubicado en /usr/share/libpkcs11‐fnmtdnie/ac_raiz_dnie.crt


### Tarjeta Picadas JA 

Instalar paquetes para manejar tarjetas:

	sudo apt-get install opensc pcscd

* Ir a “Preferencias / Avanzado / Cifrado / Dispositivos de seguridad” de Firefox
* Seleccionar “Cargar”
* Darle un nombre al módulo (Por ejemplo "JA").
* Indicar manualmente la ruta del módulo:

	* /usr/lib/x86_64-linux-gnu/opensc-pkcs11.so

### Citrix ICA Receiver

Información basada en:

<https://help.ubuntu.com/community/CitrixICAClientHowTo>

Descargamos el software de la web de CITRIX:

<http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-131.html>


Elegimos `For 64-bit Systems` y descargamos los ficheros `.deb`

<http://www.citrix.com/downloads/citrix-receiver/linux/receiver-for-linux-131.html#ctx-dl-eula>

Instalamos el paquete:

	sudo dpkg -i ~/Downloads/icaclient_*.deb ctxusb_*.deb 

Si nos aparecen mensajes de error como esteL

```
`dpkg: problemas de dependencias impiden la configuración de icaclient:
 icaclient depende de libxerces-c3.1.
dpkg: error al procesar icaclient (--install):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para desktop-file-utils ...
Procesando disparadores para gnome-menus ...
Procesando disparadores para menu ...
Se encontraron errores al procesar:
 icaclient
Si nos da un mensaje de error de que falta un 
```

Entonces forzamos la instalación: 

	sudo apt-get -f install


Instalamos certificados de firefox

	sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
	sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts/


#### Conexión a GIRO

Esta conexión requiere el [certificado de la FNMT](https://www.sede.fnmt.gob.es/documents/11614/116099/FNMTClase2CA.cer):


Como este certificado no está entre los certificado de Firefox, pues lo copiamos a mano:

	wget https://www.sede.fnmt.gob.es/documents/11614/116099/FNMTClase2CA.cer
	sudo cp FNMTClase2CA.cer /opt/Citrix/ICAClient/keystore/cacerts


## Fecha


Reconfigurar zona

	dpkg-reconfigure tzdata

Ajustar hora

	sudo date -s 13:10

O mejor:

	sudo ntpdate ntp.ceice.junta-andalucia.es

Instalar ntp

	ps -ef |grep ntp
	sudo apt-get install ntp ntpclient
	ps -ef |grep ntp
	sudo /etc/init.d/ntp stop

Actualizar ntp.conf

	server ntp.junta-andalucia.es
	server ntp.ceice.junta-andalucia.es
	server ntp.ubuntu.com
	server pool.ntp.org

Actualiza hora vía ntp y arrancar el servicio:

	sudo /usr/sbin/ntpdate ntp.junta-andalucia.es
	sudo /etc/init.d/ntp start


---
# Post instalación 
## Para cada ordenador

### Swap

Habilitación de la partición de **Swap**:

Identificamos la partición de swap:

    sudo swapon -sv
    sudo blkid |grep swap 

Veremos algo similar a esto:
    
> /dev/sda2: UUID="50626e02-d659-4db3-8ba7-6690d27cbdf0" TYPE="swap" 

Añadimos el UUID de la partición al fstab 

    sudo vi /etc/fstab


Activamos el swap:

    sudo swapoff 
    sudo swapon -a
    sudo swapon -sv



### Arranque

Configuramos **Grub2**:

    sudo apt-get install grub2
    sudo upgrade-from-grub-legacy
    sudo os-prober 
    sudo grub-mkconfig -o /boot/grub/grub.cfg
    sudo apt-get install startupmanager
    sudo apt-get install grub2-splashimages

Configuramos las opciones de arranque (entre ellas el orden)

    startupmanager


### Cambiar hostname

    sudo vi /etc/hostname
    sudo vi /etc/hosts

### Otros

Elimamos al CROM como fuente de instalación:

    sudo vi /etc/apt/sources.list
>  # deb cdrom:



# Post instalación
## Para cada usuario:

### Synapse
 
Configurar *Synapse* para 

* Arrancar y pulsar icono superior derechas
* Ejecutar al inicio de sesión y NO mostrar icono de notificación

### Java:

Verificar Java en esta URL:

<http://www.java.com/es/download/installed.jsp>

Si no funciona (probablemente porque no se instaló en ), activamos plugin de java (siguiendo las instrucciones de instalación de java [Java:][]):


    rm -f ~/.mozilla/plugins/libnpjp2.so ~/.mozilla/plugins/libjavaplugin_oji.so
    sudo rm -f /usr/lib/firefox/plugins/libnpjp2.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
    mkdir -p ~/.mozilla/plugins
    ln -s /usr/lib/jvm/jre1.7.0/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
    ls -liar ~/.mozilla/plugins/

Comprobamos la seguridad. Desde un terminal como usuario (no root) ejecutamos:


	$ /usr/lib/jvm/jre1.7.0_80/bin/ControlPanel



![Consola JAVA - Seguridad](https://dl.dropbox.com/s/zrq6fh5vgr5z2pk/Configuraci%C3%B3n%20Consola%20JAVA-Seguridad.png)



### Fuentes


Actualizamos cache de fuentes:

    fc-cache -f -v

### Cliente VPN

    /opt/forticlientsslvpn/forticlientsslvpn

### Impresión

Añadir usuario a lpadmin:

    usermod -G lpadmin  -a <usuario>


### Dropbox

Segimos las instrucciones de [instalación de Dropbox para linux](https://www.dropbox.com/es/install?os=lnx):

    cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
     ~/.dropbox-dist/dropboxd


## Virtualbox

Habilitar soporte USB Virtualbox:

    sudo usermod -aG vboxusers <usuario>


## Carpetas de red


Creamos los directorios `/mnt/<punto_montaje>` donde vamos a montar los directorios compartidos. El usuario que los vaya a crear debe tener  permiso de lectura y escritura. *<punto_montaje>* es cualquier nombre que queramos darle al directorio de montaje

```shell
	 cd /mnt
	 sudo mkdir <punto_montaje>
	 sudo chown <usuario>:usuario 
```	 

Modificamos el fichero  */etc/fstab* añadiendo cada una entrada para cada recurso compartido de red. Por ejemplo si queremos acceder a la carpeta *<compartido>* que se encuentra en el servidor *precdpto.ceice.junta-andalucia.es* debemos incluuir la siguiente línea en el fichero */etc/fstab*: 

(ejemplo):

	//precdpto.ceice.junta-andalucia.es/<compartido> /mnt/<punto_montaje> cifs credential=/home/<usuario>/.credentials.cifs,uid=\<usuario\>,iocharset=utf8,sec=ntlm,noserverino 0 0

El fichero `/home/<usuario>/.credential.cifs` debe tener nuestros usuario y **contraseña del dominio**:

    cat ~/.credentials.cifs

>     username=<usuario_dominio>
>     password=<contraseña_dominio>
>     domain=JDA



## Varios


### Diccionario Thunderbird

Si no lo está, instalar el diccionario de Thunderbird en español:

<https://addons.mozilla.org/es/thunderbird/addon/spanish-spain-dictionary/>


#### Ajustes de gnome

Es conveninente cambiar algunos ajustes por defecto de Gnome (para ver servidores conectadores, papelera, etcl.)

![image](https://dl.dropbox.com/s/nqxp48k697iby52/5121417cd845801777bc0e3ead07d04f.png)

#### Ajustes De Gnome-Tweak-Tool ####

Si no se muestran los iconos de Maximinar y Minimizar, los habilitamos desde `gnome-tweak-tool`

	sudo apt-get install gnome-tweak-tool

Una vez instalada, 

![Gnome-tweak-tool](https://dl.dropbox.com/s/tdbjddtoe0ag7g0/gnome-tweak-tool.png)
