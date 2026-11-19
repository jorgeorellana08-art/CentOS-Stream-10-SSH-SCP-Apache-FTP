# 00. Instalación de CentOS Stream 10 sin GUI

**DÓNDE: VirtualBox en WINDOWS. No uses la pestaña jorellana ni la terminal local para instalar el sistema.**

1. Crear máquina virtual nueva (Linux, Red Hat 64 bits).
2. Seleccionar la ISO de CentOS Stream 10 y **desactivar la instalación desatendida**.
3. Configurar 4096 MB de RAM, 2 procesadores y un disco virtual NUEVO (en nuestra práctica funcionó con 20 GB).
4. Adaptador 1: **NAT** (Internet). Adaptador 2: **Solo-anfitrión** (conexión de Windows con CentOS). Dejar conectado el cable virtual en ambos.
5. Iniciar el instalador. En **Selección de software** elegir **Instalación mínima**; no seleccionar «Server with GUI».
6. Crear usuario **jorellana**, marcar privilegios administrativos y elegir una contraseña propia.
7. Seleccionar el disco virtual de la máquina nueva, instalar y reiniciar.
8. Entrar en la **consola negra de CentOS**, con usuario jorellana y contraseña.

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