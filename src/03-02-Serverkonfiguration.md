# Serverkonfiguration
[Serverkonfiguraiton]: #serverkonfiguration

Die Konfiguration des Servers erfolgt nach dem so genannten "Layered configuration system". Diese Idee stammt aus den "Vorgaben" der [12-factor] Anwendunge


- Format der Konfigurationsdatei [hjson][hjson]
- Pfad der Konfigurationsdatei ist hard coded [`/boot/xMZ-Mod-Touch.hjson`, `xMZ-Mod-Touch.hjson`] in dieser Reihenfolge
  - optional kann der Name der Konfigurationsdatei, als Parameter, der Server Executable übergeben werden.

Aus der Konfiguration wird eine `ServerConfig` Struktur erstellt.

Der Name der Konfiguration kann über den Parameter `-c` bzw. `--config=` festgelegt werden.

In der Konfigurationsdatei des Servers ist der Zeitraum des Wartunsinterval
gespeichert:






# Links
[Links]: #links

- [12-factor]
- [https://hjson.org][hjson]


[12-factor]: https://12factor.net/config
[hjson]: https://hjson.org/
