# 06. Servidor FTP con FileZilla

## A. Preparar el servidor FTP

Desde centos

~~~bash
sudo dnf install -y vsftpd
sudo systemctl enable --now vsftpd
sudo systemctl status vsftpd

active (running)

**Hacer respaldo:**
~~~bash
sudo cp /etc/vsftpd/vsftpd.conf /etc/vsftpd/vsftpd.conf.bak-examen
sudo ls -l /etc/vsftpd/vsftpd.conf*


**Crear usuario FTP (solo la primera vez):**
~~~bash
sudo useradd -m ftp_estudiante
sudo passwd ftp_estudiante
id ftp_estudiante

**Crear carpeta y propietario:**
~~~bash
sudo mkdir -p /home/ftp_estudiante/subidas
sudo chown ftp_estudiante:ftp_estudiante /home/ftp_estudiante/subidas
sudo ls -ld /home/ftp_estudiante/subidas


**Firewall:**
sudo firewall-cmd --permanent --add-service=ftp
sudo firewall-cmd --reload
sudo firewall-cmd --list-services

Debe aparecer **ftp**.

## B. Conexión desde Windows con FileZilla

**DÓNDE: FILEZILLA CLIENT en WINDOWS (no en MobaXterm).**

Arriba:
- **Servidor:** 192.168.56.103 (la IP de enp0s8).
- **Nombre de usuario:** ftp_estudiante.
- **Contraseña:** la que asignaste.
- **Puerto:** 21 (predeterminado de FTP).


## C. Crear el archivo que vamos a subir
desde windows mob
cd /drives/c/Users/jorge/Downloads
echo 'Prueba FTP Jorge Orellana' > prueba_ftp.txt
cat prueba_ftp.txt


**Evidencias:** vsftpd active (running), respaldo, usuario, carpeta, FileZilla conectado, subida y descarga con transferencia correcta.

**Nota:** si Windows oculta la extensión .txt, puede verse como prueba_ftp.
