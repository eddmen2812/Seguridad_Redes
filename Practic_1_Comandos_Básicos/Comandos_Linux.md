# Ejercicio práctico
1) Crear un subdirectorio llamado maestria5 en el directorio de trabajo (home/Kali)
    *  Visualizamos con el comando [pwd] que estemos en el directorio kali, en este caso es: (/home/deed)
    ![Alt text](image.png)
    * Creamos con el comando mkdir el directorio maestria5
    ![Alt text](image-1.png)
    *	Verificamos con el comando ll el directorio creado
    ![Alt text](image-2.png)
2) Ir al directorio creado maestria5
    * Con el comando cd ingresamos al directorio mestria5 y verificamos con el comando pwd.
    ![Alt text](image-3.png)
3) Cree en el directorio maestria5 tres subdirectorios llamados clase.uno, clase.2 y clase_3.
    * Con el comando mkdir y separado con un espacio creamos los tres directorios y listamos con el comando ll para verificar.
    ![Alt text](image-7.png)
4)	Borrar el directorio clase_3
    *	Con el comando rmdir, se elimina el directorio mencionado
    ![Alt text](image-8.png)
5)	Comprobar la eliminación del directorio clase_3
    *	Con el comando ll se lista el contenido y se visualiza solo dos direcctorios
    ![Alt text](image-9.png)
     
6)	Ir a la clase.uno y crear un archivo de texto con el editor nano.
    *	Ingresamos con el comando cd al directorio clase.uno.
    *	Con el comando nano se crea un archivo de texto llamado file.txt.
    ![Alt text](image-10.png)
    *	Se despliega una nueva terminal e ingresamos algún ejemplo
    ![Alt text](image-11.png)
    * Con el comando ll verificamos la creación del archivo y con el comando cat, visualizamos el contenido del arvhivo creado
    ![Alt text](image-12.png)
 
7)	Ir al directorio clase2 y crear dos archivos de texto por medio de vi, de nombre prueba1.txt y prueba2.doc
    *	Regresamos al directorio anterior con el comando cd ..
    ![Alt text](image-13.png)
    *  	Con el comando cd ingresamos al directorio clase2
    ![Alt text](image-14.png)
    *	Con el comando vi creamos dos archivos con extensión txt y doc. Empezamos con extensión txt
    ![Alt text](image-15.png)
    *	Se despliega la terminal de vi, tecleamos la letra i para poder ingresar texto.
    ![Alt text](image-16.png)
    *	Presionamos Esc para salir del modo inserción
    ![Alt text](image-17.png)
    *	Ingresamos el siguiente comando :x para salir y guardar el archivo
    ![Alt text](image-18.png)
    *	Con cat visualizamos el contenido
    ![Alt text](image-19.png)
    *	Con el comando vi creamos dos archivos con extensión txt y doc. Empezamos con extensión doc
    ![Alt text](image-20.png)
    *	Se despliega la terminal de vi, tecleamos la letra i para poder ingresar texto.
    ![Alt text](image-21.png)
    *	Presionamos Esc para salir del modo inserción
    ![Alt text](image-22.png)
    *	Ingresamos el siguiente comando para salir y guardar el archivo
    ![Alt text](image-23.png)
    *	Con cat visualizamos el contenido
    ![Alt text](image-24.png)
    - **Nota:** El editor vi, solo usa ingreso mediante teclado, no se puede usar el mouse.
8)	Sin salir de la carpeta clase2, copiar el archivo que está en clase.uno hacia el directorio de clase2 con el nombre arvhivo1.copia
    *	Con el comando cp realizamos la copia y para detectar que la copia se haga en el directorio actual, ingresamos el punto (.). 
    ![Alt text](image-25.png)
    *	Listamos con el comando ll para verificar la copia
    ![Alt text](image-26.png)
    *	Realizamos una comparación del contenido copiado con el comando cat
    ![Alt text](image-27.png)
9)	En el directorio clase.uno crear un archivo llamado lista.txt que contenga la cantidad de elementos del direccotorio /etc y del directorio /var/log
    *	Para enviar el contenido del directorio /etc, usaremos el comando echo para imprimir un msj por pantalla, ls para listar y el signo de mayor que para enviar todo el contenido al nuevo archivo llamado lista.txt y verificamos con el comando cat
    ![Alt text](image-28.png)
    *	 Para enviar el contenido del directorio /var/log, usaremos el comando ls para listar y doble signo de mayor que para enviar todo el contenido al nuevo archivo llamado lista.txt, evitando la sobreescritura.
    ![Alt text](image-29.png)
    *	Con el comando cat verificamos
    ![Alt text](image-30.png)
10)	Listar los 10 archivos de mayor tamaño que existen en el direccotrio /var/log y en el directorio /etc
    *	En este caso usaremos los siguientes comandos. du para listar, sort para ordendar, tail para imprimir solo los 10 primeros y nl para listar el número de líneas, que son 10.
    *	Listando el contenido del direcotrio /var/log
    ![Alt text](image-31.png)
    *	Listando el contenido del directorio /etc
    ![Alt text](image-32.png)
 
