# Implementation

In den folgenden Unterkapiteln wird die Implementierung der einzelnen Teile der
Funktionsbeschreibung erläutert.

Unter anderen wurden folgende Crates verwendet.

## failure
[failure]: #failure

Mit dem `failure` Crate werden die Fehler und Ausnahmen gehändelt die wärend des Betriebs des Servers und seiner Komponenten auftreten können. Z.b. "Konfigurationsdatei kann nicht gelesen werden" oder "Fehler beim Schreiben der Laufzeit Daten"

Git Repository: [https://github.com/withoutboats/failure][failure]

## config-rs
[config-rs]: #config-rs

Mit `config` wird die Konfigurations gehandelt.

## serde
[serde]: #serde

Serialisation und Deserialisation von Datenstrukturen. Wird von `config` und
`failure` verwendet.

## toml
[toml]: #toml

Dateisystemformat der xmz-server Konfiguration.


# Links
[links]: #links

- [config][config-repo]
- [failure][failure-repo]
- [serde][serde-repo]
- [toml][toml-repo]


[config-repo]: https://github.com/mehcode/config-rs
[failure-repo]: https://github.com/withoutboats/failure
[serde-repo]: https://github.com/serde-rs/serde
[toml-repo]: https://github.com/alexcrichton/toml-rs
