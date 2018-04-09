# Serverkonfiguration
[Serverkonfiguraiton]: #serverkonfiguration

Die Konfiguration des Servers erfolgt nach dem so genannten "Layered configuration system". Diese Idee stammt aus den "Vorgaben" der [12-factor] Anwendungen.

"Layered configuration" bedeutet das es mehrer Konfigurationsdateien geben kann.
Eine Basis Konfiguration kann mit einer oder mehreren Konfigurationsdateien überschrieben werden.



- Format der Konfigurationsdatei [toml][toml]
- Pfad der Konfigurationsdatei ist hard coded [`/boot/xmz.toml`, `xmz.toml`] in dieser Reihenfolge
  - optional kann der Name der Konfigurationsdatei, als Parameter, der Server Executable übergeben werden.

Aus der Konfiguration wird eine `ServerConfig` Struktur erstellt.

Der Name der Konfiguration kann über den Parameter `-c` bzw. `--config=` festgelegt werden.

In der Konfigurationsdatei des Servers ist der Zeitraum des Wartunsinterval
gespeichert:






# Links
[Links]: #links

- [12-factor]
- [https://github.com/alexcrichton/toml-rs][toml]


[12-factor]: https://12factor.net/config
[toml]: https://github.com/alexcrichton/toml-rs
