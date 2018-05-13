# Implementation

## Default Implementationen

- alle Komponenten des Servers sollten `Default` Implementationen besizen


## verwendete Crates

Unter anderen wurden folgende Crates verwendet.

## serde
[serde]: #serde

Serialisation und Deserialisation von Datenstrukturen. Wird von vielen
verschiedenen Crates verwendet.
<https://crates.io/crates/serde>

## toml
[toml]: #toml

Dateisystemformat der `xmz-server` Konfiguration.
<https://crates.io/crates/toml>

## bincode

[`bincode`][bincode-crate] ist ein kompaktes, binäres Datenformat.
Die Laufzeit Informationen des `xmz-server` werden in diesem Format gespeichert.
<https://crates.io/crates/bincode>


# Links
[links]: #links

- [serde][serde-repo]
- [toml][toml-repo]


[serde-crate]: https://crates.io/crates/serde
[serde-repo]: https://github.com/serde-rs/serde
[toml-crate]: https://crates.io/crates/toml
[toml-repo]: https://github.com/alexcrichton/toml-rs
[bincode-crate]: https://crates.io/crates/bincode
[bincode-repo]: https://github.com/TyOverby/bincode
[bincode-doc]: https://docs.rs/bincode
