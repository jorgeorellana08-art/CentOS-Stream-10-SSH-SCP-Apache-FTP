
**DÓNDE: CENTOS — consola negra de VirtualBox.**

~~~bash
whoami
hostnamectl
ip -br addr
systemctl get-default
~~~

Debe aparecer **multi-user.target**: inicio en modo texto, sin escritorio gráfico.

Si aparece localhost y quieres poner el nombre usado en la práctica:

~~~bash
sudo hostnamectl set-hostname so-jorellana
hostname
~~~

**Evidencias:** captura de «Instalación mínima», inicio de sesión en consola y multi-user.target.

**Importante:** el disco donde se instala CentOS puede borrarse. No uses el disco de tu máquina anterior ni el de Windows.
