Subir archivos

desde windows moba

~~~bash
cd /drives/c/Users/jorge
echo 'Hola desde MobaXterm' > prueba_scp.txt
cat prueba_scp.txt
scp -P 2222 prueba_scp.txt jorellana@192.168.56.103:/home/jorellana/

**Desde centos

~~~bash
ls prueba_scp.txt
cat prueba_scp.txt
deb salir el hola 

## B.archivo de CENTOS hacia WINDOWS

**Desde centos 

~~~bash
echo 'Hola desde CentOS' > respuesta.txt
cat respuesta.txt

**Desde windows moba

~~~bash
cd /drives/c/Users/jorge
scp -P 2222 jorellana@192.168.56.103:/home/jorellana/respuesta.txt .
cat respuesta.txt

Debe mostrar **Hola desde CentOS**. 
