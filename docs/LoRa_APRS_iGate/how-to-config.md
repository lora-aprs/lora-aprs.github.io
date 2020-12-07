---
title: "LoRa APRS iGate - richtig Konfigurieren"
---

Ist der Code geladen, dann müssen ein paar Anpassungen gemacht werden in der Konfigurations-Datei `data/is-code.json`:

![iGate settings](/assets/docs/iGate_settings.png)

Vorab ein Wort zum Format der JSON Datei:
   Das Format ist gut lesbar. Man legt Variablen an in Anführungszeichen, gefolgt von einem Doppelpunkt und dem Inhalt. Eine Zahl folgt direkt, ein Text wird wieder in Anführungszeichen gesetzt. Wahr/Falsch-Werte benutzen die reservierten Wörter `false` und `true`. Bei der Variable "wifi" ist es anders aus. Hier folgt ein Block in geschweiften Klammern. Der besteht - eingerückt fürs Auge - wieder aus Variablen. Hinter jeder Zeile folgt ein "," wenn weitere Variablen auf der Ebene folgen. Die letzte Zeile hat kein Komma mehr.  Folgt hinter eine Variable etwas in [ ] Klammern, dann bedeuted das, hier können mehrere Werte als Liste folgen. Also bei `"AP":` können die Variablen mehrfach mit gleichem Namen folgen, aber anderem Inhalt.  Die Zeile SSID und password in { } kann mehrfach folgen. Damit kann mehr als ein Accesspoint (AP) angegeben werden. 

Bedeutung der Variablen
===

"callsign":
====
Beispiel:  `"OE1ABC-20"`
Das Amateurfunkrufzeichen des Betreibers sollte 6 Stellen nicht überschreiben. 
Gefolgt von der ID der Station. Eine Zahl muss nicht angegeben werden, es können aber Werte zwischen 1..36 benutzt werden. 

"wifi":
====
"active":
=====

