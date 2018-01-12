# Verwaltung: Server
[Verwaldung: Server]: #verwaltung-server

Über eine serielle Schnittstelle oder eine SSH Verbindung kann der Server
verwaltet werden.
Dazu können die systemd Werkszeuge `systemctl` und `journalctl` verwendet werden.

## Server Status
[Server Status]: #server-status

```bash
systemctl status xmz-server
```

## Server stoppen

```bash
systemctl stop xmz-server
```

## Server starten

```bash
systemctl start xmz-server
```

Alternative kann auch der `restart` Befehl verwendet werden. Hier wird der Server
vorab beendet, wenn er im Moment aktiv ist, und anschließend neu gestartet.

```bash
systemctl restart xmz-server
```
