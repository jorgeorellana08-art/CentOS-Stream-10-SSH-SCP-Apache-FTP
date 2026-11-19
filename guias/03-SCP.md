# 03. SCP: subir y descargar archivos con MobaXterm

**ATENCIÓN: en esta parte usamos DOS PESTAÑAS distintas de MobaXterm.**

- **🟨 WINDOWS LOCAL:** Start local terminal, prompt con **/drives/c/Users/jorge**. Desde aquí usamos **scp**.
- **🟦 CENTOS:** pestaña **192.168.56.103 (jorellana)**, prompt parecido a **[jorellana@so-jorellana ~]$**. Aquí comprobamos y creamos archivos del servidor.

## A. Subir archivo de WINDOWS hacia CENTOS

**DÓNDE: MobaXterm > Start local terminal (WINDOWS). No en jorellana.**

~~~bash
cd /drives/c/Users/jorge
echo 'Hola desde MobaXterm' > prueba_scp.txt
cat prueba_scp.txt
scp -P 2222 prueba_scp.txt jorellana@192.168.56.103:/home/jorellana/
~~~

Poner la contraseña de jorellana. Confirmar **100%**. La opción de SCP es **-P mayúscula**.

**DÓNDE: MobaXterm > pestaña SSH jorellana (CENTOS).**

~~~bash
ls prueba_scp.txt
cat prueba_scp.txt
~~~

Debe mostrar **Hola desde MobaXterm**.

## B. Descargar archivo de CENTOS hacia WINDOWS

**DÓNDE: pestaña SSH jorellana (CENTOS).**

~~~bash
echo 'Hola desde CentOS' > respuesta.txt
cat respuesta.txt
~~~

**DÓNDE: Start local terminal (WINDOWS). No en jorellana.**

~~~bash
cd /drives/c/Users/jorge
scp -P 2222 jorellana@192.168.56.103:/home/jorellana/respuesta.txt .
cat respuesta.txt
~~~

Debe mostrar **Hola desde CentOS**. El punto **.** del final significa «guardar en la carpeta actual».

**Evidencias:** subida **100%**; comprobación mediante cat en CentOS; descarga **100%**; comprobación mediante cat en la terminal local de Windows.

**Importante:** ejecutar SCP desde CentOS hacia su misma IP NO demuestra una transferencia entre Windows y CentOS. Para eso usamos la pestaña local.