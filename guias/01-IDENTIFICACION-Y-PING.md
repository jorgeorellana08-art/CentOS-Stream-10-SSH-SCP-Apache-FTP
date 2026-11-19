# 01. Identificar el servidor y comprobar Internet
: CENTOS 

~~~bash
clear
whoami
hostname
hostnamectl
ip -br addr
systemctl get-default
multi-user.target

Si aparece localhost y quieres poner el nombre usado en la práctica:

sudo hostnamectl set-hostname so-jorellana
hostname

 10 pings
ping -c 10 8.8.8.8
