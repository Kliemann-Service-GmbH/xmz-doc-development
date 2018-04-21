# Implementation

## Default Implementationen

- alle Komponenten des Servers sollten `Default` Implementationen besizen


## verwendete Crates

Unter anderen wurden folgende Crates verwendet.

## serde
[serde]: #serde

Serialisation und Deserialisation von Datenstrukturen. Wird von `config` und
`failure` verwendet.

## toml
[toml]: #toml

Dateisystemformat der xmz-server Konfiguration.

## bincode

[`bincode`][bincode-crate] ist ein kompaktes, binäres Datenformat. Die Laufzeit Informationen des `xmz-server` werden in diesem Format gespeichert.


# Links
[links]: #links

- [serde][serde-repo]
- [toml][toml-repo]


[serde-repo]: https://github.com/serde-rs/serde
[toml-repo]: https://github.com/alexcrichton/toml-rs
[bincode-crate]: https://crates.io/crates/bincode
[bincode-repo]: https://github.com/TyOverby/bincode
[bincode-doc]: https://docs.rs/bincode
