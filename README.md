# Dokumentation der xMZ-Plattform (Development Version)

[![Build Status](https://travis-ci.org/Kliemann-Service-GmbH/xmz-doc-development.svg?branch=development)](https://travis-ci.org/Kliemann-Service-GmbH/xmz-doc-development)

## Quellcode auschecken

Dieses Repository ist Teil der [xMZ-Plattform][xmz]. Es wird empfohlen alle Komponenten
auszuchecken.

Der Quellcode kann mit folgendem Git Befehl herunter geladen werden.
Der Parameter `--recursive` sorgt dafür das alle Komponenten (git submodule)
ebenfalls herunter geladen werden.

```bash
git clone --recursive https://github.com/Kliemann-Service-GmbH/xMZ-Plattform.git
```

Alternative kann auch nur dieses Repository ausgecheckt werden.

```bash
git clone https://github.com/Kliemann-Service-GmbH/xmz-doc-development.git
```


## lokale Kopie aus den Quellen übersetzen

```bash
mdbook build
```

Wenn die Quellen bearbeitet werden sollen dann ist der folgende Befehl nützlich.

```bash
mdbook serve
```

`mdbook serve` buildet die Dokumente automatisch neu und startet einen Webserver
der unter der Adresse [https//localhost:3000](http://localhost:3000) erreichbar
ist.


# Links

* https://github.com/Kliemann-Service-GmbH/xMZ-Plattform

[xmz]: https://github.com/Kliemann-Service-GmbH/xMZ-Plattform
