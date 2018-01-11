# Funktionsbeschreibung

Die Plattform besteht aus einem Serverteil und der Oberfläche (die so genannte
GUI).


## Server
[Server]: #server

Der Server startet frühest möglich nach dem Betriebsystemstart.

Beim Start des Servers wird die Konfigurationsdatei gelesen.

Nachdem aus der Konfigurationsdatein der Server konstruiert wurde,

startet ein http server mit einer JSON api


### Konfiguration Server
[Konfiguration Server]: #konfiguration-server

- Format der Konfigurationsdatei [hjson][hjson]
- Pfad der Konfigurationsdatei ist hard coded [`/boot/xMZ-Mod-Touch.hjson`, `xMZ-Mod-Touch.hjson`] in dieser Reihenfolge
  - optional kann der Name der Konfigurationsdatei, als Parameter, der Server Executable übergeben werden.

In der Konfigurationsdatei des Servers ist der Zeitraum des Wartunsinterval
gespeichert:


#### Konfigurationsdatei Server
[Konfigurationsdatei Server]: #konfigurationsdatei-server


### Serverstart
[Serverstart]: #serverstart

Wird keine Konfigurationsdatei gefunden, startet der Server nicht, und es wird
ein Fehler ausgegeben.

Aus der Konfiguration wird eine `ServerConfig` Struktur erstellt.

Kann die Konfiguration nicht richtig ausgewertet werden startet der Server nicht.
Eine entsprechende Fehlermeldung wird auf `STDOUT` und `STDERR` ausgegeben.


# Links
[Links]: #links

- [https://hjson.org][hjson]


[hjson]: https://hjson.org/
