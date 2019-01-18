# Custom Linux Daemon
#### Configurar daemon: https://blog.frd.mn/how-to-set-up-proper-startstop-services-ubuntu-debian-mac-windows/
#### Variables de entorno permanente: https://code.i-harness.com/es/q/df5b9b
#### Ejecutar programas en una hora y fecha determinda: https://www.cyberciti.biz/faq/howto-linux-unix-start-restart-cron/
## Forma rapida

>nohup ./miCodigo.py

Para ver las todas las tareas nohup que ejecutaron archivos python.

>ps -ef |grep python

## Ejecutar miCodigo.py como servicio
/usr/bin/python
$ python -m miCodigo.py

## Debian & Ubuntu (sysvinit)

wget https://raw.githubusercontent.com/hoat23/CustomLinuxServer/master/debian -O /etc/init.d/example

Ajustar las variables

sudo vi /etc/init.d/example

Setear el script como ejecutable

chmod +x /etc/init.d/example

Habilitar el daemon con:

update-rc.d example defaults

Iniciar el servicio

service example start

## Ubuntu (upstart)

sudo wget https://raw.githubusercontent.com/hoat23/CustomLinuxServer/master/ubuntu -O /etc/init/example.conf

Ajustar las variables

sudo vi /etc/init/example.conf

Iniciar el servicio

sudo start example

## CentOS 6 (sysvinit)

wget https://raw.githubusercontent.com/hoat23/CustomLinuxServer/master/centos -O /etc/init.d/example

Ajustar las variables

vi /etc/init.d/example

Haciendo ejecutable el script

chmod +x /etc/init.d/example

Habilitar los niveles 2,3,4 y 5 para ejecutar

chkconfig example on

Iniciar el servicio

service example start

## Arch Linux (systemd)

wget https://raw.githubusercontent.com/hoat23/CustomLinuxServer/master/arch -O /etc/systemd/system/example.service

Ajustar las variables

/etc/systemd/system/example.service

Setear el escript como ejecutable

chmod +x /etc/systemd/system/example.service

Habilitar el script como boot

systemctl enable example

iniciar el script

systemctl start example

## Gentoo (runscript)

wget https://raw.githubusercontent.com/hoat23/CustomLinuxServer/master/gentoo-script -O /etc/init.d/example

wget https://raw.githubusercontent.com/hoat23/CustomLinuxServer/master/gentoo-conf -O /etc/conf.d/example

Setear como ejecutables

chmod +x /etc/init.d/example /etc/conf.d/example

Cargar el daemon

rc-update add etherpad-lite default

Iniciar el daemon

rc-service etherpad-lite start

## Mac OS X (launchd)

Crear folder

mkdir /var/log/example

wget https://raw.githubusercontent.com/hoat23/CustomLinuxServer/master/macosx -O /Library/LaunchDaemons/mn.frd.example.plist

Copiar el archivo python a /tmp/

wget https://raw.github.com/../macosx-httpd.py -O /tmp/httpd.py

Ejecutar el demonio

sudo launchctl load /Library/LaunchDaemons/mn.frd.example.plist

## Windows (nssm)

Descargar e installar nssm:

non sucking service manager

Agregar direccion a %PATH%

Abrir el terminal como administrador

Carga el servicio:

nssm install "C:/Python27/python" -m micodigo.py

Reiniciar la máquina



