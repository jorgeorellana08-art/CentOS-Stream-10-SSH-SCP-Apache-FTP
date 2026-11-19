# 01. Identificar el servidor y comprobar Internet

**DÓNDE: CENTOS — consola de VirtualBox o pestaña SSH jorellana de MobaXterm. NO en Start local terminal.**

~~~bash
clear
whoami
hostname
hostnamectl
ip -br addr
systemctl get-default
~~~

En nuestra práctica apareció usuario **jorellana**, nombre **so-jorellana**, CentOS Stream 10 y dos interfaces:
- enp0s3: NAT, IP **10.0.2.15**.
- enp0s8: Host-only, IP **192.168.56.103**.

La IP puede cambiar en el próximo examen. **Usa la dirección de enp0s8 que te muestre el comando**.

**Internet: 10 pings exactos.**

~~~bash
ping -c 10 8.8.8.8
~~~

Resultado obtenido: **10 paquetes enviados, 10 recibidos, 0% de pérdida**.

**Evidencias:** usuario, nombre, sistema, IP, multi-user.target y el resultado del ping completo.

