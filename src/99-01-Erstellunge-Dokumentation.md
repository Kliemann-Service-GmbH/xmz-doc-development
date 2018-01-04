# Erstellung der Dokumentation

Die Dokumentation wird via [Github Pages][gh-pages] gehostet.
Branch `gh-pages`
URL `https://$USERNAME.github.io/$REPOSITORY`

Gebaut mit [TravisCI][travis]

Travis ist die Quelle des allseits beliebten Badges wie diese ![Travis Buildstatus][travis-status]

## Installation mdBook

Wie auf der [mdBook Projektseite][mdbook] beschrieben wird vorab die Software mdBook auf dem lokalen Entwickler PC installiert.

```bash
cargo install mdbook
```

## Dateisystemlayout erstellen

Als nächstes wird ein Verzeichis erstellt das den Quellcode des mdBook enthält.

```bash
mkdir xmz-doc
```

## Git Repository erstellen

Wie alle Komponenten der [xMZ-Plattform][xmz] wird auch der Quellcode des mdBook in der Versionskontrolle GIT, auf Github gehalten.

Wir erstellen also nun erst einmal ein lokales, leeres Git Repository

```bash
cd xmz-doc
git init .
```

## mdBook initalisieren

Nun wird ein leeres mdBook initalisiert. Hierbei werden ein paar grundlegende Dateien angelegt.

Die Frage ob eine `.gitignore` Datei angelegt werden soll muss mit **ja (y)** beantwortet werden.

```bash
mdbook init .
```

## Git Repo füllen

Das Dateisystemlayout sollte nun in etwa so aussehen:

```bash
$ tree
.
├── book
├── book.toml
├── LICENSE
├── README.md
└── src
    ├── chapter_1.md
    └── SUMMARY.md

2 directories, 5 files
```

Die Dateien `README.md` und `LICENSE` habe ich manuell eingefügt, dieser Schritt ist optional.

Mit dem Befehl

```bash
git add .
```

werden nun die Dateien in die Git Versionskontrolle aufgenommen. Das heist Dateien und Ordner die in der `.gitignore` Datei gelistet sind werden ignoriert.

Anschließend wir mit dem Befehl,

```bash
git commit -a -m "Erster Commit, mdBook Grundstruktur"
```

dieser Stand in die Änderungsliste aufgenommen.

## Git Repo auf Github veröffentlichen

Als nächstes legen wir auf [Github.com][github] ein Repository an.


```bash
git remote add origin git@github.com:Kliemann-Service-GmbH/xmz-doc.git
```

```bash
git push -u origin master
```

Das Repository ist nun unter der URL https://github.com/Kliemann-Service-GmbH/xmz-doc erreichbar.

## Repo in Travis aktivieren

Als nächstes müssen wir das Github Repository in [Travis][travis] aktivieren.

Dazu öffnen wir die URL https://travis-ci.org/ im Browser.



### Travis einbinden

```bash
```

```bash
```

```bash
```

```bash
```

```bash
```

```bash
```

```bash
```


### Travis Berechtigungen

![][00]

![][01]

![][02]

![][03]

![][04]

![][05]

![][06]

**Schließe das Fenster nicht!** Der Token ist nur in diesem Moment sichtbar. Im nächsten Befehl musst du `$YOUR_TOKEN` durch den grün hinterlegten Token ersetzen.

```bash
travis encrypt GH_TOKEN=$YOUR_TOKEN --add env.global
```

Jetzt kann das Fester mit dem Token geschlossen werden. Der letzte Befehl hat die Datei `.travis.yml` verändert und eine `secure:` Sektion angefügt.

Die Datei `.travis.yml` wird nun auch in die Versionskontrolle aufgenommen.

```bash
git add .travis.yml
git commit -m "Add Travis"
git push
```

### Travis Results

Nun sollte unter der URL https://$YOUR_GITHUB_USER.github.io/$YOUR_REPO das gerenderte mdBook aufzurufen sein.

Die Github Einstellungen findet man unter //Settings// -> //Github Pages//

![][07]


# Links

* https://github.com
* https://travis-ci.org
*

[blog]: https://hoverbear.org/2015/03/07/rust-travis-github-pages/
[gh-pages]: https://pages.github.com/
[travis]: https://travis-ci.org
[mdbook]: https://github.com/rust-lang-nursery/mdBook
[github]: https://github.com



[travis-status]: images/Erstellung-Dokumentation/travis-unknown.svg
[00]: images/Erstellung-Dokumentation/00-Settings.png
[01]: images/Erstellung-Dokumentation/01-click-Developer-settings.png
[02]: images/Erstellung-Dokumentation/02-click-Personal-access-tokens.png
[03]: images/Erstellung-Dokumentation/03-click-Generate-new-token.png
[04]: images/Erstellung-Dokumentation/04-fill-in-Token-description.png
[05]: images/Erstellung-Dokumentation/05-tick-public_repo.png
[06]: images/Erstellung-Dokumentation/06-click-Generate-token.png
[07]: images/Erstellung-Dokumentation/07-search-Settings-Github-Pages-your-side-should-up-and-running-now.png