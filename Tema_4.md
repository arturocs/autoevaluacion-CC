## Ejercicio 1:

#### 1. Darse de alta. Muchos están conectados con GitHub por lo que puedes  autentificarte directamente desde ahí. A través de un proceso de autorización, puedes acceder al contenido e incluso informar del resultado de los tests a GitHub.

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



## Ejercicio 2: Configurar integración continua para nuestra aplicación usando Travis o algún otro sitio.

Para mi proyecto he usado esta configuración de travis:

```yaml
language: rust
rust:
  - stable
jobs:
  fast_finish: true
cache: cargo
script:
  - make test
```

