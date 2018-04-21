# Funktionsbeschreibung: Server
[Funktionsbeschreibung: Server]: #funktionsbeschreibung-server

Der Server startet so früh wie möglich nach dem Start des Betriebssystem.

Beim Start des Servers wird dessen Version (`$CARGO_PKG_VERSION`) auf `STDOUT` ausgegeben.

Im Kapitel [Verwaltung: Server](/50-01-Verwaltung-Server.html#verwaltung-server) wird erklärt wie man den Server neu starten, und den Status des Servers prüfen kann.

## Bootstrapping, Konfiguration und Laufzeit Informationen

Beim allerersten Start des Servers wird die Server Instanz aus einer initialen Konfigurationsdatein erstellt. Dies wird auch als **Bootstrapping** bezeichnet.

Konnte aus dieser ersten Konfiguration eine funktionale Server Intanz gestartet werden, wird eine Datei mit den Laufzeit Informationen (der aktuelle Zustand des Servers) erzeugt.

Alle weiteren Starts des Servers verwenden diese Laufzeit Informationen.

Dies gewährleistet das Daten wie die Laufzeit "persistent" gespeichert werden können (d.h. das diese nicht nach einem Neustart verloren gehen).

**Kann keine Instanz erstellt werden ist das ein Critical Fehler!!** Der Server startet in diesem Fall nicht!

### Datei: Initale Konfiguration, Bootstrapping

-  `/boot/xmz-server.toml`

### Datei: Laufzeit Informationen

- `/var/cache/xmz-server/status`



## Konfiguration Server

Wie in der [Implementation: Serverkonfiguration](/03-01-02-Implementation-Serverkonfiguration.html) beschreiben, werden zur Konfiguration der Serverkomponenten Umbgebungsvariablen verwendet.

Es gibt verschiedene Arten dieser Environment Variablen:

- `ROCKET_` - diese sind für die Rocket Kom

Die Umgebungsvariablen können "von Hand" beim Start der `xmz-server` Anwendung übergeben werden. In Produktivsystemen werden die Variablen via des systemd Unit Files übergeben.

<details>
<summary>
Click to show `xmz-server.service`
</summary>

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
</details>

## Fehlerbehandlung

Die Fehler können auf `STDERR` ausgegeben werden.

### Server Tread: json API

Die Serverinstanz startet ein HTTP Server (`rocket`) mit einer json API die zur Komunikation mit weiteren Komponenten (GUI, Websites) dient.

### Server Tread: Persistent Data

In regelmäßigen Abständen speichert der Server die aktuellen Laufzeit Informationen unter: `/var/cache/xmz-server/status`

### Server Tread: Sensoren auslesen

Die Serverinstanz starete ein internen Thread der alle konfigurierten Sensoren abfragt.

### Server Tread: Auswertung

In diesem Thread werden folgende Komponenten ausgewertet:

- Zonen
- Laufzeit berechnent und,
- die Spannungsversorgung,
- Ladestand der Accu



# Links
[Links]: #links
