---
title: "Website - Add content"
---

Um neuen Inhalt auf die Webseite zu bringen sind ein paar kleine Schritte notwendig.
Wenn du bei der Github Organisation [lora-aprs](https://github.com/lora-aprs) Rechte hast, kannst du direkt mit einem Tool deiner Wahl alle Repository auschecken. Solltest du das nicht sein, kannst du um die Rechte bitten, oder die Repository einfach clonen und dann von deinem persönlichen Repository clonen. Vergiss dann bitte nicht einen Pull Request zu erstellen.

Alle hier enthaltenen Befehle werden für die Kommandozeile gezeigt. Natürlich kannst du ein Git-Tool deiner Wahl benützen.

Github checkout und Docker
===

Um das Repository aus zu checken und in das Projekt zu gehen verwende folgende Befehle:

```
git clone https://github.com/lora-aprs/lora-aprs.github.io.git
cd lora-aprs.github.io
```

Mittels Docker **kann** (nicht muss) kann die Webseite getestet werden. Ich verwende hierzu diesen Befehl:

```
docker run --rm --volume="$PWD:/srv/jekyll" -p 4000:4000 -it jekyll/jekyll jekyll serve --watch
```

Unter [http://localhost:4000](http://localhost:4000) kann die Webseite nun angesehen werden.

Wird eine Markdown Datei geändert, wird automatisch die Webseite neu erstellt und ist somit innerhalb von wenigen Sekunden sofort anzusehen.

Eine statische Seite erstellen (zb. Dokumentation)
===

Alle Datein für die Dokumentation sind unter `docs` zu finden. Dort wurde bereits für jedes Projekt ein eigener Ordner erstellt in dem dann die dazugehörigen Markdown Datein abgelegt werden.
Dort kann nun einfach eine neue Datei angelegt werden mit der Endung `.md`. Weiters ist dabei zu beachten das ein Header in der Datei erstellt wird. Hier ein Beispiel von dieser Seite:

```
---
title: "Website - Add content"
---
```

Um die neue Seite auch links in der Navigation zu haben muss noch die Datei `_data/navigation.yml` angepasst werden.


Einen neuen Blogeintrag erstellen
===

Die Blogeinträge sind im Ordner `_posts` zu finden. Dort wird eine neue Datei mit dem Namen in diesem Format erstellt: `<JAHR>-<MONAT>-<TAG>-<Titel>.md`
Der Header von Blogeinträgen ist ein wenig umfangreicher:

```
---
title: "LoRa32 iGate build up in Leonding/AT"
tags:
  - iGate
  - LoRa32
author: OE5BPA
---
```

Neben einem Titel und verschiedenen Tags ist auch der Author wichtig. Dort sollte einfach sein persönliches Rufzeichen verwendet werden.
Erstellt man seinen ersten Eintrag im Blog, sollte man sich noch in der Datei `_data/authors.yml` als Author hinzufügen. Alle Einträge in dieser Datei sind natürlich freiwillig. Als Minimum wird jedoch so ein Eintrag vorgeschalgen (Beispiel):

```
OE5BPA:
  name        : "Peter Buchegger"
  bio         : "OE5BPA"
  avatar      : "/assets/images/bio-photo.jpg"
```

Der Pfad im `avatar` kann so belassen werden wenn kein eigenes Bild hochgeladen werden möchte. Sonst kann dort auch der Pfad zu einem Foto von sich verwendet werden.

Weiter mit Git
===

Ist man mit seinen Änderungen zufrieden kann ein neuer Commit erstellt werden:

```
git commit -m "<MESSAGE>"
```

`<MESSAGE>` ist dabei die Commit-Nachricht die zu dem Commit hinterlegt wird.

Mit `git push` werden die Änderungen auf Github hochgeladen und der Server verarbeitet die Änderungen weiter.
