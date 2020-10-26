## Ejercicio 1: Buscar una aplicación de ejemplo, preferiblemente propia, y deducir qué patrón es el que usa. ¿Qué habría que hacer para evolucionar a un patrón tipo microservicios?

 

He elegido como aplicación FreedomBox, un sistema que permite al usuario crear fácilmente un servidor privado en el que instalar múltiples aplicaciones como servidores de chat, llamadas, comparticion de archivos.

Freedombox utiliza una arquitectura de microkernel en la que el usuario puede instalar distintas aplicaciones que funcionan como módulos que añaden distintas funcionalidades. Aunque permita la instalación de aplicaciones desde un menú, dichas aplicaciones no tienen una integración muy fuerte con la interfaz, ya que generalmente se trata de programas independientes integrados en freedombox.

Para hacer que freedombox utilice una arquitectura de microservicios habría que separar las aplicaciones en distintos servicios con los que la interfaz principal intercambiase información. De esta forma obtendríamos un sistema mas escalable.



## Ejercicio 2: En la aplicación que se ha usado como ejemplo en el ejercicio anterior, ¿podría usar diferentes lenguajes? ¿Qué almacenes de datos serían los más convenientes? 



La aplicación elegida anteriormente, Freedombox, ya usa múltiples lenguajes. Como cada aplicación es un programa, este puede estar escrito en cualquier lenguaje.

Freedombox actualmente usa sqlite como almacén de datos, ya que no está diseñado para atender un gran tráfico de usuarios. En caso de de que se necesitase manejar un volumen mas alto de usuarios, seria conveniente cambiar a una base de datos mas avanzada, probablemente una base de datos NoSQL ya que con la variedad de aplicaciones que el sistema maneja, una base de datos SQL desperdiciaría mucho espacio

