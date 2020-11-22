## Ejercicio 1. Buscar alguna demo interesante de Docker y ejecutarla localmente, o en su defecto, ejecutar la imagen anterior y ver cómo funciona y los procesos que se llevan a cabo la primera vez que se ejecuta y las siguientes ocasiones.

 ![](./Tema3/1.png)

Si se vuelve a ejecutar el comando,  el pulpo aparece directamente sin necesidad de descargar la imagen.



## Ejercicio 2. Tomar algún programa simple, “Hola mundo” impreso desde el intérprete de línea de órdenes, y comparar el tamaño de las imágenes de diferentes sistemas operativos base, Fedora, CentOS y Alpine, por ejemplo.

![](./Tema3/2.png)



## Ejercicio 3. Crear a partir del contenedor anterior una imagen persistente con *commit*.

![](./Tema3/3.png)

## Ejercicio 4. Examinar la estructura de capas que se forma al crear imágenes nuevas a partir de contenedores que se hayan estado ejecutando



![](./Tema3/4.png)

## Ejercicio 5. Crear un volumen y usarlo, por ejemplo, para escribir la salida de un programa determinado.

![](./Tema3/5.png)



## Ejercicio 6. Reproducir los contenedores creados anteriormente usando un `Dockerfile`.

Para reproducir el contenedor del ejercicio anterior he utilizado el siguiente dockerfile

```
FROM alpine
RUN ls -la > salida
```

![](./Tema3/6.png)