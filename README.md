# SmartHomeLampe
Erstellen einer Smart Home Lampe, die mittels eines Bewegungsmelders gesteuert wird.
Vor Benutzung Variablen anpassen:

ssid (Zeile 12) muss dem Namen des genutzten Netzwerks entsprechen
und
password (Zeile 13) muss dem Sicherheitsschluessel des genutzten Netzwerks entsprechen
damit die WLAN-Verbindung hergestellt werden kann

Die Parameter in den Zeilen 25-28 sind fuer die Verbindung mit dem MQTT-Broker wichtig;
mqtt_server enthaelt den Serverlink
mqtt_port enthaelt das Port
mqtt_user enthaelt den Nutzernamen des genutzten Accounts
mqtt_pw enthaelt das Passwort des genutzten Accounts

In Zeile 32-33 sind die Topics definiert



Die WLAN-Verbindung wird in der Methode setup_wifi() (Zeile 44) hergestellt;
Es werden Punkte ausgegeben, bis die Verbindung steht
Bei erfolgreicher Verbindung wird die IP-Adresse des Arduino ausgegeben



Die Verbindung zu dem MQTT-Broker wird in der methode reconnect() hergestellt;
Eine erfolgreiche Verbindung wird durch die Ausgabe von "connected" angezeigt
Bei Verbindungsabbruch wird automatisch eine erneute Verbindung versucht, bis die Verbindung wieder steht
Nach erfolgreichem Wiederverbinden wird dies als Nachricht published und neu subscribed
