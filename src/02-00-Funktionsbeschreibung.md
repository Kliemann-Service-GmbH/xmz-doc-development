# Funktionsbeschreibung
[Funktionsbeschreibung]: #funktionsbeschreibung

Die **xMZ-Plattform** besteht aus einem Serverteil und einem oder mehreren so genannten
Clients. Ein Client kann zum Beispiel eine Oberfläche (die so genannte GUI) direkt an
der Messzentrale sein. Aber auch Sichtplätze oder Zugriffe via Webbrowswer werden
als Clientzugriffe bezeichnet.

## Server
[Server]: #server

Der Server startet frühest möglich nach dem Betriebsystemstart.

Im Kapitel [Verwaltung: Server](/50-01-Verwaltung-Server.html#verwaltung-server) wird erklärt wie man den Server neu starten kann.

Beim Start des Servers wird die Konfigurationsdatei gelesen. Die Konfiguration kann
unter folgenden Pfaden gespeichert sein:
  - `/boot/xMZ-Mod-Touch.hjson`
  - `xMZ-Mod-Touch.hjson` (aktuelles Verzeichnis)
Spätere Konfigurationsdateien überschreiben frühere!

Wird keine Konfigurationsdatei gefunden, startet der Server nicht, und es wird
ein Fehler ausgegeben.
Kann die Konfiguration nicht richtig ausgewertet werden startet der Server nicht.
Eine entsprechende Fehlermeldung wird auf `STDOUT` und `STDERR` ausgegeben.

Danach werden die Laufzeit Informationen gelesen `/var/cache/xmz-server`.
Diese existieren aber erst wenn der Server schon einmal erfolgreich gestartet wurde.

Anschließend wird aus der Konfigurationsdatein die Serverinstanz konstruiert.

Existiert die Server Instanz, startet diese die verschiedenen Threads.

### Server Tread: Json API

Die Serverinstanz startet ein HTTP Server mit einer JSON api die zur Komunikation
mit den Clients dient.

### Server Tread: Persistent Data

In regelmäßigen Abständen speichert der Server Laufzeit Informationen nach
`/var/cache/xmz-server`

### Server Tread: Sensoren auslesen

In diesem Thread werden alle aktiven Sensoren ausgelesen.

### Server Tread: Auswertung

In diesem Thread werden die:
- Zonen
- Laufzeit berechnent und,
- die Spannungsversorgung,
- Ladestand der Accu

ausgewertet.





# Links
[Links]: #links
