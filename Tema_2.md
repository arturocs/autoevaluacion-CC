## Ejercicio 1: Instalar alguno de los entornos virtuales de `node.js` (o de cualquier otro lenguaje con el que se esté familiarizado) y, con ellos, instalar la última versión existente, la versión *minor* más actual de la 4.x y lo mismo para la 0.11 o alguna impar (de desarrollo). 



He elegido Eust y su gestor de versiones rustup, ya que estoy familiarizado con el y mi proyecto va a ser escrito en este lenguaje. Para instalar rustup basta con ejecutar:

```shell
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Para instalar la ultima versión estable de rust hay que ejecutar:

```sh
$ rustup install stable
```

Ya que la ultima versión de rust es la 1.47, no es posible instalar una versión 4.x, por ello he optado por simplemente instalar una version de rust de hace un año ejecutando:

```shell
$ rustup install 1.38.0
```

Las versión de desarrollo de rust se llama rust nightly y para instalarla la última hay que usar:

```shell
$ rustup install nightly
```



## Ejercicio 2: Crear una descripción del módulo usando `package.json`. En caso de que se trate de otro lenguaje, usar el método correspondiente. 

En el caso de Rust, para crear un nuevo "modulo" hay que usar la herramienta cargo.  Mediante el comando `cargo new --lib apuestas` creamos un nuevo proyecto con la siguiente estructura de archivos:

```shell
.
└── Porra
    ├── Cargo.toml
    └── src
        └── lib.rs
```

El archivo `Cargo.toml` seria el equivalente al `package.json`

```toml
[package]
name = "apuestas"
version = "0.1.0"
authors = ["Mi nombre <Mi email>"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]

```



## Ejercicio 3: Descargar el repositorio de ejemplo anterior, instalar las herramientas necesarias (principalmente Scala y sbt) y ejecutar el ejemplo desde `sbt`. Alternativamente, buscar otros marcos para REST en Scala tales como Finatra o Scalatra y probar los ejemplos que se incluyan en el repositorio.

Para instalar sbt he usado los repositorios de mi distribución Linux ya que así me libro de problemas con las dependencias. Para instalarlo he ejecutado:

```shell
$ sudo pacman -S sbt
```

Para evitar problemas con sbt hay que cambiar a la versión 8 de java, para ello hay que ejecutar:

```shell
$ sudo archlinux-java set java-8-openjdk/jre
```

Y comprobamos los resultados:

```shell
$ archlinux-java status
Available Java environments:
  java-11-openjdk
  java-14-openjdk
  java-8-openjdk (java-8-openjdk/jre default)

```

Una vez instalado sbt descargamos el proyecto de ejemplo y en su raíz ejecutamos sbt. Cuando termine se abrirá un prompt en el que podemos escribir `test` para ejecutar los tests de la aplicación y `re-start` para ejecutarla.

Al ejecutar los tests vemos que los pasa sin problemas:

```
...
[info] Total for specification MyServiceSpec
[info] Finished in 126 ms
[info] 5 examples, 0 failure, 0 error
[info]  
[info] Passed: Total 6, Failed 0, Errors 0, Passed 6
[success] Total time: 17 s, completed 26-oct-2020 13:18:02
```

Una vez ejecutada la aplicación vemos que es accesible desde `localhost:8080`

```
> re-start
[info] Application my-project not yet started
[info] Starting application my-project in the background ...
my-project Starting info.CC_MII.Boot.main()
[success] Total time: 0 s, completed 26-oct-2020 13:21:04
> my-project [INFO] [10/26/2020 13:21:04.876] [on-spray-can-akka.actor.default-dispatcher-3] [akka://on-spray-can/user/IO-HTTP/listener-0] Bound to localhost/127.0.0.1:8080
my-project [WARN] [10/26/2020 13:21:51.289] [on-spray-can-akka.actor.default-dispatcher-5] [akka://on-spray-can/user/IO-HTTP/listener-0/1] Illegal request, responding with status '501 Not Implemented': Unsupported HTTP method

```

Si abrimos `localhost:8080` en el navegador vemos que devuelve un archivo json:

```json
["routes", "get,put"]
```

Sin embargo en el repositorio podemos encontrar una serie de ejemplos sobre su uso:

```shell
$ curl -X PUT http://localhost:8080/0/0/Uno
{
  "local": 0,
  "visitante": 0,
  "quien": "Uno"
}

$ curl -X PUT http://localhost:8080/0/1/Otro
{
  "local": 0,
  "visitante": 1,
  "quien": "Otro"
}

$ curl -X PUT http://localhost:8080/3/1/Aquel
{
  "local": 3,
  "visitante": 1,
  "quien": "Aquel"
}

$ curl http://localhost:8080/Aquel 
{
  "local": 3,
  "visitante": 1,
  "quien": "Aquel"
}
```



## Ejercicio 4: Para la aplicación que se está haciendo, escribir una serie de aserciones y probar que efectivamente no fallan. Añadir tests para una nueva funcionalidad, probar que falla y escribir el código para que no lo haga. A continuación, ejecutarlos desde *mocha* (u otro módulo de test de alto nivel), usando descripciones del test y del grupo de test de forma correcta. Si hasta ahora no has subido el código que has venido realizando a GitHub, es el momento de hacerlo, porque lo vamos a necesitar un poco más adelante

Siguiendo el ejemplo de los apuntes del tema 2, he escrito esta aplicación para gestionar apuestas en Rust. El código principal puede verse [aquí](https://github.com/arturocs/apuestas-CC/blob/master/src/apuesta.rs).

Para los tests he usado `cargo test`, la herramienta de tests de Rust. El código de los tests puede verse [aquí](https://github.com/arturocs/apuestas-CC/blob/master/src/lib.rs).

Resultado de los tests:

 ```shell
$ cargo test
    Finished test [unoptimized + debuginfo] target(s) in 0.00s
     Running target/debug/deps/apuestas-216c5b767d97ee24

running 6 tests
test tests::apuesta_to_string ... ok
test tests::cambiar_apuesta ... ok
test tests::comprobar_empate ... ok
test tests::comprobar_ganador ... ok
test tests::creacion_de_apuesta ... ok
test tests::parsear_resultado ... ok

test result: ok. 6 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out

   Doc-tests apuestas

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
 ```



## Ejercicio 5:

#### 1. Darse de alta. Muchos están conectados con GitHub por lo que puedes usar directamente el usuario ahí. A través de un proceso de autorización, acceder al contenido e incluso informar del resultado de los tests.

He elegido travis, para ello me he dado de alta en el siguiente [enlace](https://travis-ci.org/).

####  2. Activar el repositorio en el que se vaya a aplicar la integración continua. Travis permite hacerlo directamente desde tu configuración; en otros se dan de alta desde la web de GitHub.

Una iniciada sesión con github en travis, basta con seleccionar el repositorio en el que se quiera activar la integración continua.

#### 3. Crear un fichero de configuración para que se ejecute la integración y añadirlo al repositorio.

He usado este fichero `.travis.yml` ya que según la documentación oficial de travis, contiene la configuración recomendada por los desarrolladores de rust.

```yaml
language: rust
rust:
  - stable
  - beta
  - nightly
jobs:
  allow_failures:
    - rust: nightly
  fast_finish: true
```



Una vez creado este fichero, travis ejecutará los tests del proyecto cada vez que este se actualice