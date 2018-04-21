# Implementation: Bootstrapping, Konfiguration und Laufzeit Informationen

![Flussdiagramm Bootrapping, Konfiguration][xmz-server-start]


## Datenformat Laufzeit Information

Die Laufzeit Informationen werden unter `/var/cache/xmz-server/status` im
[`bincode`][bincode-repo] Format gespeichert.

Die initiale Konfiguration `/boot/xmz-server.toml` wird im [`toml`][toml-repo] Datenformat
gespeichert.


### Speicherort: Laufzeit Informationen

- `/var/cache/xmz-server/status`

### Speicherort: Initale Konfiguration, Bootstrapping

-  `/boot/xmz-server.toml`


# Links
[Links]: #links

- [TOML Repository][toml-repo]
- [Bincode Repository][bincode-repo]


[toml-repo]: https://github.com/alexcrichton/toml-rs
[bincode-repo]: https://github.com/TyOverby/bincode

<!-- Bilder -->

[xmz-server-start]: images/xmz-server-start.svg
