# Funktionsbeschreibung: Server
[Funktionsbeschreibung: Server]: #funktionsbeschreibung-server

Der Server startet so früh wie möglich nach dem Start des Betriebssystem.

Beim Start des Servers wird dessen Version (`$CARGO_PKG_VERSION`) auf `STDOUT` ausgegeben.

Beispiel Ausgabe des Servers:

```bash
xmz-server: 2.0.0
```

Im Kapitel [Verwaltung: Server](/50-01-Verwaltung-Server.html#verwaltung-server) wird erklärt wie man den Server neu starten, und den Status des Servers prüfen kann.

## Funktionsbeschreibung Konfiguration Server

Wie in der [Implementation: Serverkonfiguration](03-01-02-Serverkonfiguration.md) beschreiben, werden zur Konfiguration der Serverkomponenten Umbgebungsvariablen verwendet.

Es existieren 2 Arten möglicher Environment Variablen:

* `ROCKET_` - diese sind für die Rocket Kom

Die Umgebungsvariablen können "von Hand" beim Start der `xmz-server` Anwendung übergeben werden. In Produktivsystemen werden die Variablen via des systemd Unit Files übergeben.

```conf
# xmz-server.service
#
# systemd Unit für die xMZ-Plattform
#
[Unit]
Description="Server der xMZ-Platform"
After=weston.service

[Service]
Type=simple
Environment=XDG_RUNTIME_DIR=/run/user/0
Environment=XMZ_HARDWARE=0.1.0
Environment=LANG=de_DE.UTF-8
Environment="ROCKET_ENV=prod"
Environment="ROCKET_ADDRESS=127.0.0.1"
Environment="ROCKET_PORT=1337"
Environment="ROCKET_LOG=critical"
ExecStart=/usr/bin/xmz-server
Restart=always
RestartSec=10s
```

Die Fehler werden auf `STDERR` ausgegeben

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
