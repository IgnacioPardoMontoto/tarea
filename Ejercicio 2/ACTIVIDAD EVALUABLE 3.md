---
title: Actividad evaluable 3
Author: Ignacio Pardo Montoto
---


# ACTIVIDAD EVALUABLE 3 - GIT y DOCKER - IGNACIO PARDO MONTOTO

[TOC]



## Ejercicio 2 Bind Mount

En primer lugar creo el directorio y el index.html

![image-20220408214129136](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214129136.png)

![image-20220408214213539](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214213539.png)

A continuación arranco uno de los contenedores vinculados mediante el comando

```bash
$docker run -d --name c1 -v /home/daw/saludo:/var/www/html -p 8181:80 php:7.4-apache
```

![image-20220408214352183](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214352183.png)

Posteriormente arranco el segundo contenedor

```bash
$docker run -d --name c2 -v /home/daw/saludo:/var/www/html -p 8282:80 php:7.4-apache
```

![image-20220408214417052](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214417052.png)

En las siguientes imágenes se puede observar como se visualiza correctamente la pagina.

![image-20220408214504677](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214504677.png)

![image-20220408214535434](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214535434.png)

Modifico el fichero index.html de la carpeta saludo.

![image-20220408214741403](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214741403.png)

Compruebo que puedo acceder a los contenedores 

```bash
$ docker exec -it c1 bash
```

![image-20220408214936773](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214936773.png)

```bash
$ docker exec -it c2 bash
```

![image-20220408215015683](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408215015683.png)

Compruebo la nueva visualizacion del fichero en el navegador

![image-20220408214813980](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214813980.png)

![image-20220408214845562](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408214845562.png)

Por ultimo, borro los contenedores realizando un stop a cada instancia.

```bash
$ docker stop c2
```

![image-20220408215220861](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408215220861.png)

```bash
$ docker stop c1
```

![image-20220408215245773](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408215245773.png)

```bash
$ docker rm $(docker ps -aq)
```

![image-20220408215309652](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408215309652.png)

Finalmente se verifica que no hay ninguna instancia en curso

```bash
$ docker ps -a
```

![image-20220408215650884](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408215650884.png)





