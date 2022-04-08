---
title: Actividad evaluable 3
Author: Ignacio Pardo Montoto
---


# ACTIVIDAD EVALUABLE 3 - GIT y DOCKER - IGNACIO PARDO MONTOTO

[TOC]

## Ejercicio 1

### 1.1 Servidor Web

El primer paso es arrancar el contenedor. Para ello se procede a la descarga del mismo mediante el siguiente comando:

```bash
$ docker pull php:7.4-apache
```

![image-20220408180943443](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408180943443.png)

A continuación se inicia una se comprueba que se descargó correctamente la imagen y se inicia una instancia.

```bash
$docker run -d --name web -p 8000:80 php:7.4-apache
```

![image-20220408182207471](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408182207471.png)

A continuación se accede al terminal del contenedor en ejecución mediante el siguiente comando.

```bash
$ docker exec -it web bash
```

![image-20220408182838048](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408182838048.png)

Una vez en el contenedor se crea el archivo index.html usando el comando

```bash
$ echo "<H1>HOLA SOY IGNACIO PARDO</H1>" > index.html
```

![image-20220408183618116](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408183618116.png)

y compruebo desde el navegador que efectivamente se muestra la pagina web.

![image-20220408183729069](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408183729069.png)



Para crear el php realizamos el mismo proceso, mediante un comando echo se crea el archivo php. A continuación se visualiza el resultado en el navegador.

![image-20220408185236569](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408185236569.png)

![image-20220408185312047](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408185312047.png)

Por ultimo borramos el contenedor mediante el siguiente comando

```bash
$ docker rm $(docker ps -aq)	
```

![image-20220408185915490](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408185915490.png)



### 1.2 Servidor de Base de Datos

Para arrancar un contenedor que ejecute una instancia de la imagen mariadb se debe ejecutar el siguiente comando

```bash
$ docker run --detach --name bbdd --env MARIADB_USER=invitado --env MARIADB_PASSWORD=invitado --env MARIADB_ROOT_PASSWORD=root --env MARIADB_DATABASE=prueba mariadb:latest
```

![image-20220408204720728](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408204720728.png)

Una vez ejecutado el comando accedo a la base de datos con el usuario invitado y se comprueba que efectivamente esta creada la BBDD prueba.

![image-20220408210832663](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408210832663.png)

En la siguiente imagen se puede observar como no se puede borrar la imagen mariadb mientras el contenedor bbdd está  creado.

![image-20220408211145804](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408211145804.png)

En la siguiente imagen se pueden ver las imágenes de mi registro.

![image-20220408211223626](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408211223626.png)

En la siguiente imagen se puede observar como se eliminan los contenedores utilizados.

![image-20220408211332911](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408211332911.png)



.
