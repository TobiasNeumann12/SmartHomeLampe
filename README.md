# SmartHomeLampe

Die SmartHomeLampe soll die Lichtschaltung im Alltag automatisieren und nicht nur zu jeder Zeit gute Lichtverhältnisse schaffen, sondern auch für eine Energie Einsparung sorgen.


Die SmartHomeLampe besteht aus zwei Bestandteilen. Zum einen aus Sensor, Mikrocontroller, Knopfzelle und zum anderen aus einer WLAN fähigen LED. In unserem Fall benutzen wir die Philips Hue, welche über Bluetooth mit einer Bridge verbunden ist, die wiederum per Lan-Kabel im Netzwerk eingebunden ist. Den ersten Teil unseres Projektes kann man z.B. an einer Türzarge befestigen, sodass wenn jemand den Raum betritt, das Licht angeschaltet wird und wenn er ihn verlässt, wieder aus geschaltet wird. Die LED kann man dann in eine beliebige Lampe drehen und das Projekt ist einsatzbereit. Bei der Philips Hue muss man, wie bereits erwähnt zusätzlich noch die Bridge im Netzwerk anschließen.


## Hardware:

•	ESP8266 32-Bit

•	Steckbrett mit 17×10 sockets

•	HC SR501 Infrarot Bewegungsmelder

•	Knopfzelle

•	HUE Philips E27 LED-Lampe

•	HUE-Bridge



## Software:

•	Arduino

•	Node Red
     
     	node-red-contrib-huemagic muss installiert



## Inbetriebnahme

Für die aller erste Inbetriebnahme müssen zuerst die WiFi-Daten spricht SSID und Passwort des Netzwerkes, indem sich Mikrocontroller und Bridge befinden im Code in der Arduino IDE hinterlegt werden. Dann muss der Code mit den neu eingefügten Daten auf den Mikrocontroller geladen werden. Die Bridge muss per LAN-Kabel ans Netzwerk angeschlossen sein und in einer Steckdose angesteckt sein. Ab diesem Zeitpunkt funktionieren Sensor, Mikrocontroller und der Datenaustausch zwischen Mikrocontroller und MQTT Server. Wenn die hue Birne sich in einer Lampe befindet und eine Stromzufuhr hat, verbindet diese sich automatisch mit der Bridge. Um nun auch die Bridge und MQTT zu verbinden, muss Node-Red auf einem Computer, welcher ebenfalls per Lan-Kabel im Netzwerk hängt, mit dem entsprechendem Flow laufen (damit alle Funktionen verfügbar sind muss node-red-contrib-huemagic installiert sein). In diesem Flow befindet sich ein Node (Anweisungsblock) der sich Hue Licht nennt. Hier wird die IP der Bridge im Netzwerk hinterlegt und ein neuer Benutzer erstellt. Dann muss noch eine hue Lampe, die mit der Bridge verbunden ist, ausgewählt werden. Diese nennt sich Hue color lamp 1. Die Änderungen im Flow müssen noch übernommen werden und dann ist die SmartHomeLampe in einem neuen Netzwerk funktionsfähig. Wenn der Sensor Bewegung feststellt, wird der Status (An/Aus) der Lampe geändert.

Anweisung per Video: https://wp.uni-oldenburg.de/soft-skills-und-technische-kompetenz-wise20212022-projektgruppe-4/nutzerhandbuch/




### Mehr zur SmartHomeLampe unter:

https://wp.uni-oldenburg.de/soft-skills-und-technische-kompetenz-wise20212022-projektgruppe-4/


