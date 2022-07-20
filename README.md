# SmartHomeLampe
Erstellen einer Smart Home Lampe, die mittels eines Bewegungssensors gesteuert wird.
Vor Benutzung Variablen anpassen:

ssid (Zeile 11) muss dem Namen des genutzten Netzwerks entsprechen
und
password (Zeile 12) muss dem Sicherheitsschluessel des genutzten Netzwerks entsprechen
damit die WLAN-Verbindung hergestellt werden kann

Die Parameter in den Zeilen 24-27 sind fuer die Verbindung mit dem MQTT-Broker wichtig;
mqtt_server enthaelt den Serverlink
mqtt_port enthaelt das Port
mqtt_user enthaelt den Nutzernamen des genutzten Accounts
mqtt_pw enthaelt das Passwort des genutzten Accounts

In Zeile 31 wird eine Variable instanziert die weiter unten im Code zur Speicherung des Lampen Status dient

In Zeile 33-34 sind die Topics definiert



Die WLAN-Verbindung wird in der Methode setup_wifi() (Zeile 46) hergestellt;
Es werden Punkte ausgegeben, bis die Verbindung steht
Bei erfolgreicher Verbindung wird die IP-Adresse des Arduino ausgegeben

Die Methode  callback() (Zeile 65) verarbeitet eine übergebene byte-codierte Message, die unter einem gegebenen Topic gepublished wurde, zu einem String und printed diesen aus. Außerdem wird in Zeile 75 der Lampen Status in der Variable lampeStatus gespeichert



Die Verbindung zu dem MQTT-Broker wird in der methode reconnect() (Zeile 84) hergestellt;
Eine erfolgreiche Verbindung wird durch die Ausgabe von "connected" angezeigt
Bei Verbindungsabbruch wird automatisch eine erneute Verbindung versucht, bis die Verbindung wieder steht
Nach erfolgreichem Wiederverbinden wird dies als Nachricht published und neu subscribed



Zeile 108 markiert den Beginn der Funktionalitaet des Controllers

setup()  (Zeile 108) stellt die WLAN-Verbindung her und nutzt die oben definierten Parameter, um den korrekten Server anzusteuern

loop() (Zeile 121 ) ist fuer das Aufrechterhalten der MQTT-Verbindung zustaendig. Außerdem werden hier die Daten des Bewegungssensors empfangen und verarbeitet. In Zeile 130 wird unteranderem die callback() Methode aufgerufen, dadurch kann in der if-Abfrage der aktuelle Status der Lampe genutzt werden. Je nachdem ob die Lampe an oder aus ist wird ein String gepublished. Dieser ist entweder "ON" die Lampe ist aus und soll angehen oder "OFF" die Lampe ist an und soll ausgschaltet werden.
