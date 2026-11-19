# CentOS Stream 10: SSH, SCP, Apache y FTP

**Sistemas Operativos · Primer ciclo · Jorge Orellana**

Esta guía sigue la práctica realizada en VirtualBox: instalación mínima de CentOS Stream 10, identificación del servidor, 10 pings, SSH en puerto personalizado con MobaXterm, SCP en ambos sentidos, árbol de directorios, Apache, FTP con FileZilla y respaldos. Usa comandos fáciles y explica **en qué ventana se ejecuta cada uno**.

> **Antes del examen:** revisa si el docente permite usar una guía externa. Los valores de IP, usuario y rutas de este ejemplo pueden cambiar en otra instalación. No guardes contraseñas en GitHub.

## ⛔ Lo primero: identificar DÓNDE debes escribir

| Símbolo de la guía | Ventana que debes abrir | Cómo reconocerla | Para qué sirve |
|---|---|---|---|
| 🟦 **CENTOS** | Consola negra de VirtualBox **o** pestaña SSH de MobaXterm `192.168.56.103 (jorellana)` | Prompt similar a `[jorellana@so-jorellana ~]$` | Instalar servicios, `sudo`, respaldos, Linux, `tree`, crear `index.html` y archivos del servidor |
| 🟨 **WINDOWS LOCAL** | **MobaXterm → Start local terminal**; pestaña con `/home/mobaxterm` o `/drives/c/Users/jorge` | Prompt de MobaXterm con carpeta `/drives/c/...` | Crear archivos en Windows con `echo`, transferir archivos con `scp` hacia/desde CentOS |
| 🟩 **FILEZILLA** | Programa **FileZilla Client** de Windows | Panel **Sitio local** a la izquierda y **Sitio remoto** a la derecha | Subir y descargar archivos por FTP; no hay que ejecutar `scp` aquí |
| 🟪 **NAVEGADOR** | Chrome/Edge/Brave en Windows | Barra de direcciones | Ver `http://192.168.56.103` |
| ⚙️ **VIRTUALBOX** | Oracle VirtualBox Manager | Configuración de la máquina | RAM, disco, NAT y adaptador solo-anfitrión |

**¡Atención!** La pestaña `jorellana` de MobaXterm **es CentOS**, aunque la abras desde Windows. La pestaña `Start local terminal` **es Windows**. No confundas esas dos para SCP.

## Datos que funcionaron en nuestra práctica

| Dato | Ejemplo real de nuestra práctica |
|---|---|
| Sistema | CentOS Stream 10, instalación mínima **sin GUI** |
| Usuario administrador | `jorellana` |
| Nombre del equipo | `so-jorellana` |
| Dirección NAT (Internet) | `10.0.2.15` |
| Dirección host-only (Windows → CentOS) | `192.168.56.103` |
| SSH y SCP | **Puerto 2222** |
| Apache / HTTP | **Puerto 80** |
| FTP / FileZilla | **Puerto 21** |
| Usuario FTP | `ftp_estudiante` |
| Carpeta FTP | `/home/ftp_estudiante/subidas` |
| Carpeta Windows (SCP) | `/drives/c/Users/jorge` |
| Carpeta Windows (FTP) | `C:\Users\jorge\Downloads\` y `C:\Users\jorge\Documents\` |

La IP `192.168.56.103` **no es universal**: la próxima vez copia la IP que muestre `ip -br addr` en la tarjeta `enp0s8`.

## Orden recomendado para repetir la práctica

1. [00 — Instalación sin GUI y VirtualBox](guias/00-INSTALACION-SIN-GUI.md) — NAT + host-only, usuario e instalación mínima.
2. [01 — Identificación y 10 pings](guias/01-IDENTIFICACION-Y-PING.md) — `whoami`, `hostnamectl`, `ip`, `ping`.
3. [02 — SSH, puerto 2222 y respaldo](guias/02-SSH.md) — `cp`, `echo`, `cat`, SELinux, firewall y conexión con **MobaXterm**.
4. [03 — SCP desde MobaXterm](guias/03-SCP.md) — **qué va en la pestaña local** y qué va en `jorellana`.
5. [04 — Directorios Linux](guias/04-TREE.md) — `tree` y explicación de carpetas.
6. [05 — Apache](guias/05-APACHE.md) — instalación, `active (running)`, backup, `index.html`, firewall, navegador.
7. [06 — FTP y FileZilla](guias/06-FTP-FILEZILLA.md) — instalación, backup, usuario, carpeta, subir y descargar.
8. [07 — Evidencias y rúbrica](guias/07-EVIDENCIAS-Y-RUBRICA.md) — capturas requeridas.
9. [08 — Errores habituales](guias/08-ERRORES-COMUNES.md) — errores que encontramos y soluciones simples.
10. [09 — Chuleta de comandos](guias/09-RESUMEN-RAPIDO.md) — consulta rápida al final.

## Comandos básicos que vas a utilizar

| Comando | Significa |
|---|---|
| `clear` | Limpia la pantalla |
| `whoami` | Dice qué usuario soy |
| `hostname` | Muestra el nombre del equipo |
| `ip -br addr` | Muestra IP y adaptadores |
| `ping -c 10 8.8.8.8` | Envía 10 paquetes |
| `cd` | Cambia de carpeta |
| `ls` | Lista archivos |
| `cat` | Lee contenido |
| `echo` | Escribe texto |
| `>` | Crea o reemplaza un archivo |
| `>>` | Agrega texto al final |
| `cp` | Copia un archivo |
| `mkdir -p` | Crea carpeta (y su ruta, si hace falta) |
| `sudo` | Ejecuta con permisos de administrador en CentOS |
| `systemctl` | Maneja servicios de Linux |
| `scp` | Copia archivos a través de SSH |
| `tree` | Muestra árbol de carpetas |

## Comprueba todo antes de entregar

- `systemctl get-default` devuelve `multi-user.target` (sin interfaz gráfica).
- `ping -c 10 8.8.8.8` muestra 10 enviados y 10 recibidos.
- MobaXterm se conecta al puerto `2222` y `echo $SSH_CONNECTION` termina en `2222`.
- SCP sube **desde Windows** y descarga **hacia Windows**, ambos al `100%`.
- `tree` muestra `/` y `/home`, y se explican sus carpetas.
- Apache muestra `active (running)` y en el navegador sale `Jorge Orellana`.
- FileZilla se conecta como `ftp_estudiante`, sube un archivo a `subidas` y lo descarga a `Documents`.
- Hay capturas de los respaldos de SSH, Apache y FTP.

> Esta guía es un registro de la práctica; no sustituye las capturas reales ni una evaluación del docente. **No subas capturas con contraseñas ni claves a un repositorio público.**