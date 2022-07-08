# huayra-talleres
Aplicación para facilitar el desarrollo de talleres multi-etapa

Huayra-talleres está desarrollada en GAMBAS3,  entorno de desarrollo incluido en Huayra Linux.

La idea es facilitar el trabajo de los y las talleristas y de los y las participantes utilizando un servidor remoto (CAP) que guarde los archivos trabajados en cada una de las etapas.

El análisis funcional sería:    Llega un participante a la POSTA 1 ,  presionando el botón "nuevo participante" se le asigna un código de cinco dígitos, por ejemplo "10014".  Ese será su ID durante toda la estadía.  La aplicación automáticamente, al ingresar un código o al generar uno nuevo, monta el servidor remoto como local usando SSHFS, teniendo los archivos de ese participante disponibles en:

/home/estudiante/talleres 

Luego, una vez terminado el trabajo del participante, no hace falta copiar archivos ni trasladarlos, solo guardar. Al dirigirse a la POSTA 2,  deberá ingresar su código ID  con lo que tendrá nuevamente disponibles sus archivos, y así sucesivamente en las siguientes postas.


------------------
Implementación:

El servidor remoto debe tener una carpeta en /home/cap/cap_remoto  donde se guardará la información.

1)  clonar el repo.
2) modificar la línea de conexión al servidor remoto. No olvidar reemplazar la palabra "CONTRASEÑA" por la correspondiente. En el archivo FMain.class  modificar la siguiente línea:

 Shell "sshfs -o reconnect -o password_stdin -p 22 cap@192.168.1.1:/home/cap/remoto_cap /home/estudiante/.talleres <<< 'CONTRASEÑA'" Wait
 
3) Ir a "Proyecto" -> "Crear" -> "Generar paquete".

