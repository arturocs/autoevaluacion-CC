 # Ejercicios tema 5

### Ejercicio 1: Instalar `etcd3`, averiguar qué bibliotecas funcionan bien con el lenguaje que estemos escribiendo el proyecto (u otro lenguaje), y hacer un pequeño ejemplo de almacenamiento y recuperación de una clave; hacer el almacenamiento desde la línea de órdenes (con `etcdctl`) y la recuperación desde el mini-programa que hagáis.

He utilizado la biblioteca [etcd-client](https://crates.io/crates/etcd-client)

```rust
use etcd_client::{Client, Error};

#[tokio::main]
async fn main() -> Result<(), Error> {
    let mut client = Client::connect(["localhost:2379"], None).await?;
    let resp = client.get("clave", None).await?;
    let kv = resp.kvs().first().unwrap();
    println!("{{{}: {}}}", kv.key_str()?, kv.value_str()?);
    Ok(())
}
```

```bash
[arturo@arturo-ms7845 etcd]$ etcdctl put clave valor
OK
[arturo@arturo-ms7845 etcd]$ cargo run
   Compiling etcd v0.1.0 (/home/arturo/Escritorio/etcd)
    Finished dev [unoptimized + debuginfo] target(s) in 3.48s
     Running `target/debug/etcd`
{clave: valor}
```

