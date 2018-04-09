# Web und json API
[Web und json API]: #web-und-json-api


## Datenstruktur

Die internen Datenstrukturen wie zum Beispiel der Server oder die Sensoren sind in einzelen Modulen zusammengefasst.

```rust
mod server {
    use std::sync::{Arc, Mutex};
    use sensor::Sensor;

    pub struct Server {
        pub uptime: u32,
        pub sensors: Vec<Arc<Mutex<Sensor>>>,
    }

    impl Server {
        pub fn new() -> Self {
            Server { uptime: 1, sensors: vec![], }
        }
    }
}
```

```rust
mod sensor {
  pub struct Sensor;
}
```

Diese **internen** Strukturen werden nicht 1:1 über die Json API nach außen
dargestellt.

Es existiert ein eigenes Rust Modul `api` in dem Kopien der internen
Datenstrukturen zu finden sind. Die Wandlung von intern nach extern erfolgt
mit den [Rust Traist From und Into][rustbyexample-conversion].

```rust
mod api {
    pub mod server {
        use ::server::Server as InternalServer;

        #[derive(Serialize, Deserialize, Debug)]
        pub struct Server {
            uptime: u32,
        }

        impl From<InternalServer> for Server {
            fn from(server: InternalServer) -> Self {
                Server {
                    uptime: server.uptime,
                }
            }
        }
    }
}
```



Der komplette Beispielcode sieht so aus.

```rust
#[macro_use]
extern crate serde_derive;

extern crate serde;
extern crate serde_json;

mod server {
    use std::sync::{Arc, Mutex};
    use sensor::Sensor;

    pub struct Server {
        pub uptime: u32,
        pub sensors: Vec<Arc<Mutex<Sensor>>>,
    }

    impl Server {
        pub fn new() -> Self {
            Server { uptime: 1, sensors: vec![], }
        }
    }
}

mod sensor {
  pub struct Sensor;
}

mod api {
    pub mod server {
        use ::server::Server as InternalServer;

        #[derive(Serialize, Deserialize, Debug)]
        pub struct Server {
            uptime: u32,
        }

        impl From<InternalServer> for Server {
            fn from(server: InternalServer) -> Self {
                Server {
                    uptime: server.uptime,
                }
            }
        }
    }
}

fn main() {
    use api::server::Server as ExtServer;
    use server::Server;

    let server = Server::new();

    println!("{:?}", serde_json::to_string::<ExtServer>(&server.into()).unwrap());
}
```

Die Idee stammt unter anderem von diesem [Blog Post][blog-object-shadowing].




# Links
[Links]: #links

- [https://commiebstrd.github.io/rustlang/serde/json/2018/03/01/object-shadowing.html][blog-object-shadowing]
- [https://rustbyexample.com/conversion/from_into.html][rustbyexample-conversion]





<!-- Manuals Tutorials, Blogs -->

[rustbyexample-conversion]: https://rustbyexample.com/conversion/from_into.html
[blog-object-shadowing]: https://commiebstrd.github.io/rustlang/serde/json/2018/03/01/object-shadowing.html
