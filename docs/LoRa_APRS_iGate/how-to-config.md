---
title: "LoRa APRS iGate - Konfigurieren"
---

## Einstellungen
In der Konfigurations-Datei `data/is-code.json` sind alle Einstellungen zu hinterlegen. 
Sie wird mit ausgeliefert, enthält jedoch nur Platzhalter.

![iGate settings](/assets/docs/iGate_settings.png)

---

#### Hinweise zum JSON Format [^1]

Wir ersetzen die vorgegebenen Stellen, lassen aber alle Anführungszeichen stehen. 	(Mehr zum Format: siehe unten)

## Bedeutung der Variablen

### "callsign":

Beispiel:  `"OE1ABC-20"`

Das Amateurfunkrufzeichen des Betreibers sollte 6 Stellen nicht überschreiben. 
Gefolgt von der ID der Station. Eine Zahl muss nicht angegeben werden, es können 
aber Werte zwischen 1..36 benutzt werden. 

### "wifi":

> __"active":__ 

> `false` : das Wifi auf der Platine ist ausgeschaltet

> `true` : das Wifi wird eingeschaltet. Die Logindaten für den Accesspoint müssen folgen.

> #### "AP":

> `SSID` : Kennung/Name des Wifi-Netzes in Anführungszeichen setzen z.B: "TELECOM-1234"

> `password` : Das für dieses Netz gültige Passwort angeben

> __Beispiel für einen Accesspoint:__
>
	"AP": [
		{ "SSID":"HomeNetz", "password":"Geheim" }
	]

> __Beispiel für zwei Accesspoints:__
> 
	"AP": [
		{ "SSID":"HomeNetz", "password":"Geheim" },
		{ "SSID":"Freenetz", "password":"" }
	]

### "beacon":

Darunter versteht man Bakensendungen der Lora-Platine um den APRS-Servern zu sagen: zeig mich auf der Karte an.

> __"message":__ 

> `Bakentext` : Hier kommt alles rein, was auf der Karte als Beschreibungstext erscheinen soll. 
Empfehlung: Das Wort `LoRa` zu belassen. 
Auf der WebSeite `aprsdirect.com` kann man in den Bakentexten suchen mit `CMT:*LoRa*` und kann auf diese Weise nach Stationen filtern.

> __"position":__

> `latitude` : Längengrad des Standortes in dezimalformat z.B. 48.12345  (Dezimalpunkt benutzen!)

> `longtitude` : Breitengrad des Standortes in dezimalformat z.B. 7.67890  (Dezimalpunkt benutzen!)

> _Hinweis: Die Koordinaten lassen sich in Google-Maps direkt ablesen_ 








---

[^1]

### Hinweise zum JSON Format

- Das Format ist gut lesbar. 
- Variablen stehen in Anführungszeichen, gefolgt von einem Doppelpunkt und dem Inhalt. 
	- Eine Zahl folgt direkt, 
	- ein Text wird auch in Anführungszeichen gesetzt. 
	- Wahr/Falsch-Werte benutzen die reservierten Wörter `false` und `true`. 
	- Aus dem Beispiel oben: Bei der Variable  `"wifi"` ist es anders aus. Hier folgt ein Block in geschweiften Klammern. 
	Der besteht - eingerückt fürs Auge - wieder aus Variablen. Hinter jeder Zeile folgt ein '","' wenn weitere Variablen auf der Ebene folgen. 
	Die letzte Zeile hat kein Komma mehr. Folgt hinter eine Variable etwas in eckigen Klammern, dann bedeuted das, 
	hier können mehrere Werte als Liste folgen. Also bei `"AP":` können die Variablen mehrfach mit gleichem Namen folgen, 
	aber anderem Inhalt.  Die Zeile SSID und password in `{` `}` kann mehrfach folgen. 
	Damit kann mehr als ein Accesspoint (AP) angegeben werden. 
