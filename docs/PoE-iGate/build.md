---
title: "PoE iGate - Build"
---

Folgendes Werkzeug braucht ihr zum Bau des PoE iGate's:
* Lötkolben
* Lötzinn
* kleine Flachzange
* Entlötlize (für das LoRa Modem wenn ihr es selber lötet)

Löten der Stiftleisten am TTGO PoE Board
===

Zunächst müssen wir das PoE Board vorbereiten dazu müssen wir zwei Stiftleisten anlöten. Zu erst sollte die große zwei Zeilige Leiste löten:

![PoE Stiftleiste](/assets/docs/build/1_poe_stiftleiste.png)

Danach können wir auf der Unterseite die kleine Stiftleiste anlöten:

![PoE Stiftleiste](/assets/docs/build/2_poe_stiftleiste.png)


Löten des LoRa Boards
===

LoRa Modem (SMD)
---

Zunächst sollte man das LoRa Modem anlöten.

![modem](/assets/docs/build/3_modem_no_solder.png)

Man sollte als erster das Modem auf der PCB ausrichten. Wichtig ist hier das der Antennenanschluss mit dem Aufdruck auf der PCB zusammen passt.

Man lötet nun mit viel Zinn alle Pads an - Spart hier nicht am Zinn und schaut das ihr eine gute Verbindung habt. Aufpassen muss man hier, das die Pads aber nicht mit der Überdachung verbunden werden.

Das schaut dann zb. so aus:

![modem](/assets/docs/build/4_modem_solder.png)

Verwendet nun die Entlötlize um das überflüssige Zinn aufzusaugen. Die Lötverbindungen sollten dann schöner und mit weniger Zinn ausschauen. Überprüft nun auch mit einem Multimeter ob Verbindungen zwischen den Pads bestehen.


LCD Versorgung
---

![modem](/assets/docs/build/5_lcd_look.png)

Unter den Löchern für das LCD sind ein paar Pads um VCC und GND für das LCD zur Verfügung zu stellen. Durch diese Pad's können verschiedenen LCD's verwendet werden (VCC und GND vertauscht).
Überprüft zunächst euer LCD und lötet dann die jeweiligen Pad's zusammen. Mit einem Multimeter sollte dann die Verbindung überprüft werden.

![modem](/assets/docs/build/6_lcd_solder.png)


Buchsenleiste
---

Auf der Unterseite der PCB sollte nun die Buchsenleiste angelötet werden.
Hier verwende ich ein paar Stiftleisten um die Buchsenleiste zusammen zu halten und zu stabilisieren:

![modem](/assets/docs/build/7_pinheader_support.png)

Wenn man jetzt die PCB umdreht steht sie sehr schief da, hier lege ich einfach eine Pinzete unter.
Lötet zunächst nur 2 Pin's an.

![modem](/assets/docs/build/8_pinheader_solder_first.png)

Schaut euch nun an ob die Buchsenleiste gerade auf der PCB sitzt, wenn nicht könnt ihr einen Pin erwärmen und mit dem Finger auf die Buchsenleiste drücken um sie gerade auf der PCB zu haben. Spielt euch hier so lange mit den zwei Pin's bis sie passt.
Lötet nun den rest der Buchsenleiste fest.

![modem](/assets/docs/build/9_status.png)


Taster
---

Die zwei Taster können nun eingesetzt werden - sie halten schon ziemlich gut von alleine und müssen nur mehr auf der Rückseite verlötet werden.

![modem](/assets/docs/build/10_taster.png)


LCD
---

Nun könnt ihr auch das LCD verlöten.

![modem](/assets/docs/build/11_with_lcd.png)

Danach bist du mit dem LoRa Board fertig!

![modem](/assets/docs/build/12_status.png)


Zusammenbau
===

Nun könnt ihr zwei Distanzbolzen und zwei Muttern verwenden um auf der Seite des Ethernet-Anschlusses Füße anzubringen.
Danach könnt ihr die restlichen Distanzbolzen verwenden um das LoRa Board auf dem PoE Board zu befestigen.
Zieht die Bolzen aber nicht gleich ganz fest an - hier spießt es oft zwischen den Boards. Leichter ist es sie später an zu ziehen. Mit Muttern wird auch das LoRa Board befestigt.

![modem](/assets/docs/build/13_finished.png)
![modem](/assets/docs/build/14_finished.png)
