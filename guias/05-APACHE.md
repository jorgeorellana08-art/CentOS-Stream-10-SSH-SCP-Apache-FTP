# 05. Servidor Web Apache

**DÓNDE: CENTOS — pestaña SSH jorellana de MobaXterm (o consola de VirtualBox).**

## Instalar, iniciar y verificar
~~~bash
sudo dnf install -y httpd
sudo systemctl enable --now httpd
sudo systemctl status httpd
~~~

Debe decir **active (running)**. Pulsa **Q** para salir.

## Respaldar configuración antes de modificar
~~~bash
sudo cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.bak-examen
sudo ls -l /etc/httpd/conf/httpd.conf*
~~~

## Crear la página con nombre y apellido
~~~bash
echo '<h1>Jorge Orellana</h1>' | sudo tee /var/www/html/index.html
cat /var/www/html/index.html
~~~

**MUY IMPORTANTE:** utilizar **comillas simples** alrededor de la etiqueta HTML; las comillas dobles con <h1> pueden producir el error «-bash: h1: No existe el fichero».

## Permitir HTTP en firewall
~~~bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
sudo firewall-cmd --list-services
~~~

Debe incluir el servicio **http**.

## DÓNDE: WINDOWS — NAVEGADOR (no terminal)
En Chrome, Brave o Edge abrir:
~~~text
http://192.168.56.103
