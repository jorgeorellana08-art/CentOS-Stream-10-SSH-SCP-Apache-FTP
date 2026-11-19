# 04. Estructura de directorios de Linux

**DÓNDE: CENTOS — consola de VirtualBox o pestaña SSH jorellana en MobaXterm.**

~~~bash
sudo dnf install -y tree
tree -L 1 -d /
tree -L 2 -d /home
~~~

Significado:
- **tree**: muestra carpetas como árbol.
- **-L 1**: solo un nivel; **-L 2**: dos niveles.
- **-d**: solo directorios.
- **/**: raíz de Linux; **/home**: carpetas de usuarios.

Explicación corta de directorios:
- **/**: punto inicial de todos los directorios.
- **/home**: archivos personales de usuarios.
- **/etc**: configuraciones del sistema y servicios.
- **/var**: registros y datos variables de servicios.
- **/usr**: programas y herramientas instaladas.
- **/bin**: comandos básicos; en CentOS suele enlazar a /usr/bin.
- **/boot**: archivos para iniciar el sistema.
- **/dev**: dispositivos.
- **/tmp**: temporales.
- **/root**: carpeta del administrador.
- **/proc** y **/sys**: información del sistema y núcleo.

**Evidencia:** foto/captura del árbol de / y /home, y la explicación en tu informe.