# 08. Errores comunes y cómo resolverlos

| Problema | Qué revisar o hacer |
|---|---|
| No aparece enp0s8 | VirtualBox: adaptador 2 conectado a Host-only, cable virtual conectado. En CentOS revisar ip -br addr. |
| Hostname sigue como localhost en prompt | Ejecutar hostname; el prompt se actualiza al iniciar una sesión nueva. |
| hostnamectl muestra «Access denied» en serial | Si muestra nombre del host y versión del sistema, esa advertencia no impidió la consulta. |
| semanage dice que no existe el parámetro | Usar semanage port --list o -l con **letra ele minúscula**, no número 1. |
| semanage: puerto 2222 ya definido | No repetir port -a; consultar sudo semanage port --list y buscar ssh_port_t. |
| firewall-cmd «unrecognized arguments: permanent» | Debe escribirse **--permanent** todo junto, sin espacios después de los guiones. |
| SSH no conecta desde Windows | Comprobar IP enp0s8, firewall 2222/tcp, sudo sshd -t, systemctl is-active sshd, sudo ss -tln. |
| SCP no demuestra Windows a servidor | Ejecutarlo desde **Start local terminal**, no desde la pestaña jorellana. |
| SCP: opción de puerto | Usar **-P 2222** mayúscula (no -p). |
| «-bash: h1: No existe el fichero» con echo | Usar **comillas simples**: echo '<h1>Jorge Orellana</h1>' (nunca sin proteger los signos < y >). |
| No puedo ver la carpeta de ftp_estudiante con ls | Probar **sudo ls -ld /home/ftp_estudiante/subidas**. No cambiar permisos de toda la carpeta innecesariamente. |
| FileZilla conecta pero transferencia falla | Confirmar subidas, usuario, propietario con sudo ls -ld, firewall ftp y mensajes exactos de FileZilla. |
| FileZilla muestra «550 Rename failed» | Hubo un intento de renombrar; no significa que la subida o descarga de archivo haya fallado. |
| Archivo descargado ya estaba en Downloads | Cambia el sitio local a **Documents** antes de descargar, así la evidencia es clara. |
| Windows muestra prueba_ftp sin .txt | Puede estar ocultando extensiones de archivos conocidos. Abrir y comprobar contenido. |
| sudo pide contraseña | Es la contraseña del usuario jorellana. No muestra caracteres mientras la escribes. |

**Consejo:** ejecuta un comando por vez y verifica su resultado. Si un comando falla, corrige ese paso antes de seguir.

**No ejecutar comandos destructivos para “empezar de cero”** sobre la VM anterior: crea otra máquina virtual, guarda capturas y configuraciones ya realizadas.