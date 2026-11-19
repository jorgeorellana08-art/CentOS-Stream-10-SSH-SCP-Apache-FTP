# 07. Lista de evidencias y requisitos de la práctica

**DÓNDE: capturas hechas en VirtualBox, MobaXterm, FileZilla y el navegador de Windows, según corresponda.**

| Requisito | Qué demostrar | DÓNDE |
|---|---|---|
| Identificación | whoami, hostnamectl, IP y sistema CentOS | CENTOS |
| Internet | ping -c 10 con 10 enviados y recibidos | CENTOS |
| SSH | sshd active (running), puerto 2222 y respaldo sshd_config | CENTOS |
| SSH cliente | conexión a puerto 2222, echo $SSH_CONNECTION | MobaXterm pestaña SSH |
| SCP subida | archivo Windows a CentOS, 100% | MobaXterm local |
| SCP verificación | cat del archivo recibido | CentOS pestaña jorellana |
| SCP descarga | archivo CentOS a Windows, 100%, cat local | MobaXterm local |
| Árbol Linux | tree de / y /home, explicación | CENTOS |
| Apache | httpd active (running), backup y archivo index.html | CENTOS |
| Apache cliente | navegador mostrando Jorge Orellana | Navegador Windows |
| FTP | vsftpd active (running), respaldo, usuario, carpeta y firewall | CENTOS |
| FTP subir | archivo en lado remoto, transferencia correcta | FileZilla |
| FTP bajar | archivo en Documents, transferencia correcta | FileZilla |
| Extra sin GUI | «Instalación mínima» + multi-user.target | VirtualBox/CentOS |

**Distribución de la rúbrica principal:** formato/redacción 2; CentOS identificado 0,5; ping 0,5; SSH y respaldo 1; SCP 1; árbol y explicación 1; Apache y respaldo 2; FTP y respaldo 2. Total **10 puntos posibles** (nota otorgada por el profesor). Extras de la guía: LaTeX 1, servidor sin GUI 2.

**Recomendaciones para el informe:** usar la plantilla oficial que indique el profesor, redactar solo lo que hiciste realmente, colocar las capturas legibles con sus nombres y explicar brevemente qué comprueba cada una.

**No publicar:** contraseñas, llaves privadas, datos personales de terceros o capturas con credenciales.