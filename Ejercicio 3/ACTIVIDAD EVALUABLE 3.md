---
title: Actividad evaluable 3
---

## Ejercicio 3 Despliegue de contenedores en red

En primer lugar creo manualmente una red bridge denominada redbd

```bash
$docker network create redbd
```

![image-20220408225136148](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408225136148.png)

Posteriormente se crea un contenedor con una imagen mariadb con la red creada anteriormente y todas las particularidades descritas en el ejercicio.

```bash
$docker run -d --name bbdd -v volumen:/home/daw/saludo --env MARIADB_USER=usuarioinicial --env MARIADB_PASSWORD=passusuario --env MARIADB_ROOT_PASSWORD=passroot --network reddb -p 3306:80 mariadb:latest
```

![image-20220408225434380](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408225434380.png)

Posteriormente se crea el contenedor con Adminer con la misma red

```bash
$docker run -d --name ad --network reddb adminer:latest
```

![image-20220408225550348](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408225550348.png)

Se comprueba que los dos contenedores está en ejecución

```bash
$docker ps -a
```

![image-20220408225647100](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408225647100.png)



Borrar los contenedores

![image-20220408230233410](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408230233410.png)

Borrar la red

```bash
$docker network rm redbd
```

![image-20220408230540234](ACTIVIDAD%20EVALUABLE%203.assets/image-20220408230540234.png)

