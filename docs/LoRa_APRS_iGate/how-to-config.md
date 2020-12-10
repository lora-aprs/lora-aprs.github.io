---
title: "LoRa APRS iGate - Konfigurieren"
---

## Einstellungen
In der Konfigurations-Datei `data/is-code.json` sind alle Einstellungen zu hinterlegen. 
Sie wird mit ausgeliefert, enthält jedoch nur Platzhalter.

![iGate settings](/assets/docs/iGate_settings.png)

---

#### Hinweise zum JSON Format [1]

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

Darunter versteht man Bakensendungen der Lora-Platine um den APRS-Servern zu sagen: zeig mich auf der Karte an. Der Text und die Position die mit ausgesendet werden kann wird hier zentral abgelegt und später bei "aprs_is" oder im Mode "digi" benutzt.

> __"message":__ 

> `Bakentext` : Aussendungen über HF. Hier kommt alles rein, was auf der Karte als Beschreibungstext erscheinen soll. Die Bake muss von einem Lora-Gateway gehört und ins Internet zu einem APRS-Server weitergegeben werden.
Empfehlung: Das Wort `LoRa` zu belassen. 
Auf der WebSeite `aprsdirect.com` kann man in den Bakentexten suchen mit `CMT:*LoRa*` und kann auf diese Weise nach Stationen filtern.

> __"position":__

> `latitude` : Längengrad des Standortes in dezimalformat z.B. 48.12345  (Dezimalpunkt benutzen!)

> `longtitude` : Breitengrad des Standortes in dezimalformat z.B. 7.67890  (Dezimalpunkt benutzen!)

> _Hinweis: Die Koordinaten lassen sich in Google-Maps direkt ablesen_ 

### "aprs_is":

Hier sind die Daten gesammelt, die für eine Internetverbindung zu einem APRS-InternetServer
benötigt werden. Wenn das "aktiv" geschaltet wird, muss auch "wifi" aktiv sein.

> __"active":__ 

> `false` : es wird keine Verbindung zu einem APRS Server hergestellt

> `true` : Verbindung wird mit den nachfolgenden Daten über das aktive Wifi hergestellt

> __"password":__ 

> Es ist ein Passwort nötig um eine schreibene Verbindung zu einem APRS-Server herzustellen.
Das Passwort errechnet sich aus dem unter "callsign" angegebenen Rufzeichen (ohne die angehängte Zahl) und besteht aus 5 Ziffern. 

> __"server":__ 

> Name oder IP-Adresse eines Internet-Servers. Hinter den Adressen wie "euro..." oder "dl.." verstecken sich meistens viele Rechner, die zufällig die Verbindung übernehmen. Für kurze Übertragungszeiten sollte ein Servername aus der örtlichen Nähe benutzt werden z.B. `"euro.aprs2.net"`

> __"port":__ 

> Der Internetserver kann auf verschiedenen Ports angesprochenen werden. Wenn dir das nichts sagt, benutze immer den Standartport `14580`

> __"beacon":__

> `false` : es wird keine Bake zum APRS Server gesendet

> `true` : es wird eine Bake gesendet. Das Intervall wird in Minuten angegeben. Der Text wird aus dem Abschnitt `"beacon":"message"` entnommen. Die Bake wird nicht über HF ausgesendet sondern nur ins Internet

> __"beacon_timeout":__

> Zahl in Minuten.  Empfehlung: Werte zwischen >= 15 und <=30 Minuten benutzen

### "digi":

Läuft das Teil als Digipeater (Digitales Relais. Empfängt und sendet ohne Internetzugang), sind die nachfolgenden Angaben wichtig. 

> __"active":__ 

> `false` : Der Modus "Digi" ist deaktiviert. 

> `true` : Der Modus "Digi" ist aktiviert. NIE (!) gleichzeitig mit `"aprs_is":"active"` zusammen auf `true` setzen. Das ist aktuell noch ein undefinierter Zustand.

> __"forward_timeout":__

> Zahl in Sekunden. Ein gehörtes Paket wird nach 5 Sekunden wieder abgestrahlt (wenn es kein Duplikat ist). Dieser Wert ist experimentell erarbeitet.

> __"beacon":__

> Es wird angegeben, ob eine Bake über HF ausgesendet werden soll. Der Text wird aus dem Abschnitt `"beacon":"message"` entnommen.

> __"beacon_timeout":__

> Zahl in Minuten.  Empfehlung: Werte zwischen >= 15 und <=30 Minuten benutzen. Bei Batteriebetrieb einkalkulieren, dass jede Aussendung ca. 4 Sekunden lang ca. 200 mA (bei einem Lora-Chip mit 20 dBm/100 mW). Das Intervall dann seltener nutzen (höher einstellen). 


### "lora":

Die hier angegebenen Werte dienen der Initialisierung des LoRa-Bausteins. Das ändern der Werte spreading_factor, signal_bandwidth und coding_rate4 führen zu Inkompatibilitäten mit anderen Aussendungen/Empfängern. Diese Werte wurden für Lora-Aprs als optimal erforscht und sollten immer beibehalten werden.

> __"frequency_rx":__ <br>
> __"frequency_tx":__

> Die hier hinterlegte Frequenz `433775000` ist mit der IARU abgestimmt und sollte wie die 2m Frequenz für APRS 144.800 nicht verändert werden.

> __"power":__

> Der Wert ist in dBm anzugeben. Vorgabe `20` ist die maximale Leistung eines 20 dBm Chips (100 mW). Die Leistung kann hier für Testzwecke reduziert werden. 

> __"spreading_factor":__ 12,<br>
> __"signal_bandwidth":__ 125000,<br>
> __"coding_rate4":__ 5

> Diese Werte sind für die Initialisierung des Lora-Chips notwendig. Änderungen führen zu Inkompatibilitäten mit anderen Einrichtungen.

### "display":

Um das Display abschalten zu können (Stromverbrauch oder um Einbrennen zu verhindern), werden diese Werte gesetzt. 

> __"always_on":__

> `false` : Das Display geht schlafen. 

> `true` : Die Anzeige ist standardmäßig dauerhaft aktiv. 

> __"timeout":__

> Zahl in Sekunden. Das Display schaltet wenn `always_on:false` eingestellt, nach dieser Zeit aus. Erwacht nur, wenn eine Taste insofern vorhanden auf der Platine gedrückt wird oder eine Aktion über einen Pin erfolgte.

> __overwrite_pin":__

> Zahl als Portnummer. `0` = keine Aktion definiert. Sonst ist eine Pin-Nummer der Platine zu hinterlegen. Weitere Bedeutung ist vom Entwickler zu erfragen.


### "ftp":

Ist das `wifi` aktiviert und hat eine Verbindung ins heimische Netzwerk, kann mit einem FTP-Programm (Filetransfer-Programm) eine Verbindung zum Verzeichnis mit der Config-Datei auf der Platine hergestellt werden. Die Config-Datei kann dann vom PC aus runtergeladen, modifiziert und wieder hochgeladen werden. Die neue Config-Datei wird jedoch erst beim nächsten Reset der Platine geladen. 

> __"active":__

> `false` : FTP ist abgeschaltet. Die Platine hört auch bei bestehender Wifi-Verbindung nicht auf Anfragen

> `true` : Der FTP-Zugang ist auf der Platine aktiv und hört auf Anfragen (unverschlüsseltes FTP)

> #### "user":

> Für eine Zugriffskontrolle eingehender Anfragen, wird nach einem Benutzernamen und einem Passwort gefragt 

> `name` :  Das hier hinterlegte ist später bei "user" anzugeben.
> `password` : Dieses Passwort muss der Benutzer dann verwenden

> __Beispiel für einen Accesspoint:__
>
	"user": [
		{ "name":"ftpuser", "password":"Geheim" }
	]








---

__Fußnote:__

### [1] Hinweise zum JSON Format

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

---
