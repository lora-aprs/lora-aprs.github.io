---
title: "LoRa APRS iGate - Quick-Start Guide"
---

Um den Source Code zu bekommen muss man auf [github.com](https://github.com/lora-aprs/LoRa_APRS_iGate) gehen und dort das Repository herunterladen. Das geht ganz einfach über den grünen Code Button und "Download Zip". Benützer die sich mit git auskennen können natürlich auch das Repository clonen.

![github code](/assets/docs/github_code.png)

PlatformIO kann direkt auf der Webseite von [PlatformIO](https://platformio.org/) herunter geladen werden. Dort muss nur auf den grünnen Button mit "Install PlatformIO now" gedrückt werden. Danach muss es natürlich noch installiert werden.
Wenn man Visual Studio Code bereits installiert hat, kann das PlatformIO Module auch über den Plugin Manager installiert werden.

Nun kann der Source Code in Visual Studio Code geöffnet werden.

Einstellungen
===

Zunächst müssen ein paar Anpassungen gemacht werden in der Datei `data/is-code.json`:

![iGate settings](/assets/docs/iGate_settings.png)

1. Latitude und Longitude müssen immer ausgefüllt werden. Wenn man seine Koordinaten nicht im Kopf hat, einfach Google Maps aufmachen, einen rechtsklick auf den gewünschten Ort und 'was ist da?' anklicken.
2. Diese Einstellungen müssen verändert werden wenn man ein iGate verwenden möchte:
    1. das `active` in `wifi` und `aprs_is` muss von `false` auf `true` gesetzt werden.
    2. es muss die SSID und das Passwort der WLan-Verbindung eingegeben werden.
3. Diese Einstellungen müssen verändert werden um einen Digi zu erhalten:
    1. das `active` in `digi` muss von `false` auf `true` gesetzt werden.

Es ist nicht zu empfehlen gleichzeitig ein iGate und einen Digi laufen zu lassen. In einer späteren Version wird das überprüft und es werden nur mehr die Einstellungen des iGates laufen (vermutlich wird der Digi Mode dann aktiv wenn keine WLan Verbindung aufgebaut werden kann - mal sehen).

Richtige Board auswählen
===

Nun muss noch das richtige Board ausgewählt werden, jedes Board ist nämlich ein bisschen anders verdrahtet (die GPIOs werden anders verwendet) oder besitzt zusätzliche Komponenten.

Dies kann in der Statusleiste wo derzeit noch `Default` steht geändert werden.

![choos board](/assets/docs/choos_board.png)

Kompilieren und flashen
===

Nun sind alle Vorbereitungen abgeschlossen und wir können den Source Code kompilieren und auf das Board flashen.
Dazu drücken wir auf den Pfeil der nach rechts zeigt in der Statusleiste.
**ACHTUNG:** Nach dem flashen der Firmware muss auch noch die Konfiguration geflashed werden, das sind zwei einzelne Schritte!

![statusleiste](/assets/docs/statusleiste.png)

In der Statusleiste können folgende Dinge schnell erledigt werden:
1. Kompilieren der Firmware
2. Flashen der Firmware
3. Aufräumen der temporären und der kompilierten Daten
4. Serial Monitor

Flashen der Konfiguration
===

Um die Konfiguration zu flashen muss ein Filesystem geflashed werden.
Dazu führt man folgende Schritte aus:

1. links auf das Alien klicken
2. dann das jeweilige Board auswählen
3. im Untermenü wird jetzt `Platform` erweitert
4. dort klickt man auf `Upload Filesystem Image`

![upload_filesystem](/assets/docs/upload_filesystem.png)

**ACHTUNG:** Es kann manchmal passieren das der upload fehl schlägt. Dann einfach so lange probieren bis es passt.
