# 06. Servidor FTP con FileZilla

**FTP se usa aquí solo en la red privada de laboratorio. Transmite usuario, contraseña y datos sin cifrar; fuera del laboratorio usa SFTP.**

## A. Preparar el servidor FTP

**DÓNDE: CENTOS — pestaña SSH jorellana en MobaXterm. NO la terminal local de Windows.**

~~~bash
sudo dnf install -y vsftpd
sudo systemctl enable --now vsftpd
sudo systemctl status vsftpd
~~~

Verificar **active (running)**. Pulsa **Q** para salir.

**Hacer respaldo:**
~~~bash
sudo cp /etc/vsftpd/vsftpd.conf /etc/vsftpd/vsftpd.conf.bak-examen
sudo ls -l /etc/vsftpd/vsftpd.conf*
~~~

**Crear usuario FTP (solo la primera vez):**
~~~bash
sudo useradd -m ftp_estudiante
sudo passwd ftp_estudiante
id ftp_estudiante
~~~

La contraseña debe tener al menos 8 caracteres. No se verá mientras la escribes. No publicarla en GitHub.

**Crear carpeta y propietario:**
~~~bash
sudo mkdir -p /home/ftp_estudiante/subidas
sudo chown ftp_estudiante:ftp_estudiante /home/ftp_estudiante/subidas
sudo ls -ld /home/ftp_estudiante/subidas
~~~

Si ls sin sudo dice **Permiso denegado**, usa **sudo ls**: el directorio es del usuario ftp_estudiante y es normal.

**Firewall:**
~~~bash
sudo firewall-cmd --permanent --add-service=ftp
sudo firewall-cmd --reload
sudo firewall-cmd --list-services
~~~

Debe aparecer **ftp**.

## B. Conexión desde Windows con FileZilla

**DÓNDE: FILEZILLA CLIENT en WINDOWS (no en MobaXterm).**

Arriba:
- **Servidor:** 192.168.56.103 (la IP de enp0s8).
- **Nombre de usuario:** ftp_estudiante.
- **Contraseña:** la que asignaste.
- **Puerto:** 21 (predeterminado de FTP).

Pulsar **Conexión rápida**. Si indica «Registrado en» y lista /home/ftp_estudiante, está conectado.

## C. Crear el archivo que vamos a subir

**DÓNDE: MobaXterm > Start local terminal = WINDOWS LOCAL. NO en la pestaña SSH jorellana.**

~~~bash
cd /drives/c/Users/jorge/Downloads
echo 'Prueba FTP Jorge Orellana' > prueba_ftp.txt
cat prueba_ftp.txt
~~~

## D. Subir con FileZilla

**DÓNDE: FILEZILLA en WINDOWS, sin comandos.**
1. IZQUIERDA = **Sitio local**: C:\Users\jorge\Downloads\.
2. DERECHA = **Sitio remoto**: /home/ftp_estudiante/subidas.
3. Selecciona prueba_ftp.txt en la IZQUIERDA, clic derecho **Subir**.
4. Comprobar «Transferencia correcta» y que el archivo aparece en la DERECHA.

## E. Descargar con FileZilla

**DÓNDE: FILEZILLA en WINDOWS, sin comandos.**
1. Cambiar el SITIO LOCAL (IZQUIERDA) a **C:\Users\jorge\Documents\** para evitar mezclar el original con la descarga.
2. Mantener el SITIO REMOTO (DERECHA) en /home/ftp_estudiante/subidas.
3. Sobre prueba_ftp.txt en la DERECHA, clic derecho **Descargar**.
4. Verificar «Transferencia correcta» y que prueba_ftp.txt aparece en la IZQUIERDA (Documents).
5. Abrir el archivo descargado y comprobar el texto «Prueba FTP Jorge Orellana».

**Evidencias:** vsftpd active (running), respaldo, usuario, carpeta, FileZilla conectado, subida y descarga con transferencia correcta.

**Nota:** si Windows oculta la extensión .txt, puede verse como prueba_ftp.