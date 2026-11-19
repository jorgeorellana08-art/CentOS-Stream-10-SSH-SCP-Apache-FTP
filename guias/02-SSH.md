# 02. Servidor SSH Moba
En centos

## Instalar y comprobar SSH
~~~bash
sudo dnf install -y openssh-server
sudo systemctl enable --now sshd
sudo systemctl status sshd

Debe mostrar **active (running)**. Para salir de status, pulsa **Q**

## Respaldo (antes de cambiar la configuración)
~~~bash
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak-examen
sudo ls -l /etc/ssh/sshd_config*


## Autorizar el puerto con SELinux
~~~bash
sudo dnf install -y policycoreutils-python-utils
getenforce
sudo semanage port -a -t ssh_port_t -p tcp 2222

Si dice que el puerto 2222 ya existe, consulta:
~~~bash
sudo semanage port --list | grep ssh_port_t

No añadas dos veces el mismo puerto.

## Permitir el puerto 2222 en el firewall
~~~bash
sudo systemctl enable --now firewalld
sudo firewall-cmd --permanent --add-port=2222/tcp
sudo firewall-cmd --reload
sudo firewall-cmd --list-ports
....tcp


echo 'Port 22' | sudo tee /etc/ssh/sshd_config.d/10-examen.conf
echo 'Port 2222' | sudo tee -a /etc/ssh/sshd_config.d/10-examen.conf
cat /etc/ssh/sshd_config.d/10-examen.conf
sudo sshd -t
sudo systemctl restart sshd
sudo systemctl is-active sshd
sudo ss -tln | grep 2222
~~~

Debe mostrar **Port .. **Port .... servicio active

Conectar moba

**DÓNDE: pestaña SSH de MobaXterm con jorellana@so-jorellana.**
~~~bash
whoami
echo $SSH_CONNECTION
~~~

El **último valor** de SSH_CONNECTION debe ser **2222**.

**Evidencias:** sshd active (running), respaldo, firewall 2222/tcp, LISTEN :2222, MobaXterm conectado mostrando SSH_CONNECTION.
