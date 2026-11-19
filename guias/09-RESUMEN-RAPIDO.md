# 09. Resumen rápido — comandos y DÓNDE escribir

Este es el resumen para revisar el orden. Para entender cada paso, abre las guías completas.

## 🟦 CENTOS: consola de VirtualBox o pestaña `jorellana` SSH

```bash
# IDENTIFICACIÓN
whoami
hostname
hostnamectl
ip -br addr
systemctl get-default
ping -c 10 8.8.8.8

# SSH
sudo dnf install -y openssh-server
sudo systemctl enable --now sshd
sudo systemctl status sshd
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak-examen
sudo ls -l /etc/ssh/sshd_config*
sudo dnf install -y policycoreutils-python-utils
sudo semanage port -a -t ssh_port_t -p tcp 2222
sudo systemctl enable --now firewalld
sudo firewall-cmd --permanent --add-port=2222/tcp
sudo firewall-cmd --reload
echo 'Port 22' | sudo tee /etc/ssh/sshd_config.d/10-examen.conf
echo 'Port 2222' | sudo tee -a /etc/ssh/sshd_config.d/10-examen.conf
cat /etc/ssh/sshd_config.d/10-examen.conf
sudo sshd -t
sudo systemctl restart sshd
sudo ss -tln | grep 2222

# COMPROBAR CONEXIÓN SSH DESDE LA PESTAÑA JORELLANA
echo $SSH_CONNECTION

# CONFIRMAR ARCHIVO SUBIDO POR SCP
ls prueba_scp.txt
cat prueba_scp.txt

# CREAR ARCHIVO PARA DESCARGA POR SCP
echo 'Hola desde CentOS' > respuesta.txt
cat respuesta.txt

# ÁRBOL
sudo dnf install -y tree
tree -L 1 -d /
tree -L 2 -d /home

# APACHE
sudo dnf install -y httpd
sudo systemctl enable --now httpd
sudo systemctl status httpd
sudo cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.bak-examen
sudo ls -l /etc/httpd/conf/httpd.conf*
echo '<h1>Jorge Orellana</h1>' | sudo tee /var/www/html/index.html
cat /var/www/html/index.html
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload

# FTP
sudo dnf install -y vsftpd
sudo systemctl enable --now vsftpd
sudo systemctl status vsftpd
sudo cp /etc/vsftpd/vsftpd.conf /etc/vsftpd/vsftpd.conf.bak-examen
sudo ls -l /etc/vsftpd/vsftpd.conf*
sudo useradd -m ftp_estudiante
sudo passwd ftp_estudiante
id ftp_estudiante
sudo mkdir -p /home/ftp_estudiante/subidas
sudo chown ftp_estudiante:ftp_estudiante /home/ftp_estudiante/subidas
sudo ls -ld /home/ftp_estudiante/subidas
sudo firewall-cmd --permanent --add-service=ftp
sudo firewall-cmd --reload
sudo firewall-cmd --list-services
```

**OJO:** `sudo semanage port -a` y `sudo useradd -m` son operaciones para una instalación limpia. Si ya existen, **no se vuelven a agregar**.

## 🟨 WINDOWS: terminal local de MobaXterm (`/drives/c/...`), NO `jorellana`

```bash
# SUBIDA SCP
cd /drives/c/Users/jorge
echo 'Hola desde MobaXterm' > prueba_scp.txt
cat prueba_scp.txt
scp -P 2222 prueba_scp.txt jorellana@192.168.56.103:/home/jorellana/

# DESCARGA SCP
cd /drives/c/Users/jorge
scp -P 2222 jorellana@192.168.56.103:/home/jorellana/respuesta.txt .
cat respuesta.txt

# CREAR ARCHIVO PARA FILEZILLA
cd /drives/c/Users/jorge/Downloads
echo 'Prueba FTP Jorge Orellana' > prueba_ftp.txt
cat prueba_ftp.txt
```

## 🟩 FILEZILLA EN WINDOWS (sin comandos de terminal)

- Conectar a `192.168.56.103`, usuario `ftp_estudiante`, puerto **21**.
- **Subir:** lado izquierdo `Downloads` → lado derecho `/home/ftp_estudiante/subidas`.
- **Descargar:** lado derecho `subidas` → lado izquierdo `Documents`.

## 🟪 NAVEGADOR DE WINDOWS

```text
http://192.168.56.103
```

Debe aparecer **Jorge Orellana**.