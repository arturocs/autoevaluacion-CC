## Buscar una aplicación de ejemplo, preferiblemente propia, y deducir qué patrón es el que usa. ¿Qué habría que hacer para evolucionar a un patrón tipo microservicios?

 

He elegido como aplicación FreedomBox, un sistema que permite al usuario crear fácilmente un servidor privado en el que instalar múltiples aplicaciones como servidores de chat, llamadas, comparticion de archivos.



Freedombox utiliza una arquitectura de microkernel en la que el usuario puede instalar distintas aplicaciones que funcionan como módulos que añaden distintas funcionalidades. Aunque permita la instalación de aplicaciones desde un menú, dichas aplicaciones no tienen una integración muy fuerte con la interfaz, ya que generalmente se trata de programas independientes integrados en freedombox.



Para hacer que freedombox utilice una arquitectura de microservicios habría que separar las aplicaciones en distintos servicios con los que la interfaz principal intercambiase información. De esta forma obtendríamos un sistema mas escalable.

