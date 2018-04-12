# Funktionsbeschreibung: Server
[Funktionsbeschreibung: Server]: #funktionsbeschreibung-server

Der Server startet so früh wie möglich nach dem Start des Betriebssystem.

Beim Start des Servers wird dessen Version (`$CARGO_PKG_VERSION`) auf `STDOUT` ausgegeben.

Im Kapitel [Verwaltung: Server](/50-01-Verwaltung-Server.html#verwaltung-server) wird erklärt wie man den Server neu starten, und den Status des Servers prüfen kann.

## Implementationsdetails

- alle Komponenten des Servers sollten `Default` Implementationen besizen

## Bootstrapping; erster Start

- ist keine Laufzeit Information `/var/cache/xmz-server/status` vorhanden muss der Server aus der Bootstrapping Datei `/boot/xmz.toml` erstellt werden.
  - **Kann keine Instanz erstellt werden ist das ein Critical Fehler!!** Der Server startet in diesem Fall nicht!

## Funktionsbeschreibung Konfiguration Server

Wie in der [Implementation: Serverkonfiguration](/03-01-02-Implementation-Serverkonfiguration.html) beschreiben, werden zur Konfiguration der Serverkomponenten Umbgebungsvariablen verwendet.

Es existieren 2 Arten möglicher Environment Variablen:

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

Die Fehler werden auf `STDERR` ausgegeben

## Laufzeit Imformationen

Laufzeit Informationen werden unter `/var/cache/xmz-server/status` gespeichert.

**Das Dateiformat von `/var/cache/xmz-server/status` ist noch nicht entschieden!**

`/var/cache/xmz-server/status` existiert erst wenn der Server einmal, erfolgreich aus der Konfigurationsdatei `/boot/xmz-server.toml` erzeugt und gestartet wurde.

### Server Tread: json API

Die Serverinstanz startet ein HTTP Server (`rocket`) mit einer json API die zur Komunikation mit weiteren Komponenten (GUI, Websites) dient.

### Server Tread: Persistent Data

In regelmäßigen Abständen speichert der Server Laufzeit Informationen nach
`/var/cache/xmz-server/status`

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
