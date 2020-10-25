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



