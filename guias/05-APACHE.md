# 05. Servidor Web Apache

Desde CENTOS 

## Instalar, iniciar y verificar
~~~bash
sudo dnf install -y httpd
sudo systemctl enable --now httpd
sudo systemctl status httpd

 **active (running)**. 

## Respaldar configuración antes de modificar
~~~bash
sudo cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.bak-examen
sudo ls -l /etc/httpd/conf/httpd.conf*
~~~

## Crear la página con nombre y apellido
~~~bash
echo '<h1>Jorge Orellana</h1>' | sudo tee /var/www/html/index.html
cat /var/www/html/index.html

## Permitir HTTP en firewall
~~~bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
sudo firewall-cmd --list-services

Debe incluir el servicio **http**.

## DÓNDE: WINDOWS — NAVEGADOR 

http://192.168.56.103
