# dietPi-hole


Das Image dietPi-hole.img basiert auf dem Betriebssystem dietpi v8.14. Mittels dietpi-launcher wurde Pihole aus dem selben Repository installiert. Die Netzwerkkonfiguration wurde auf DHCP voreingestellt. Dazu wurden 75 Blocklisten eingepflegt und die Option DNSSEC für die vier upstream DNS Server aktiviert: 2x Cloudflare und 2x Quad9. Benefits des Piholes sind signifikante performance Verbesserungen von ca. 800 ms auf nur noch 50 ms bis 70 ms für die IP-Addressen Auflösung. Die Sicherheit wird verbessert, da sogenanntes "DNS CNAME cloaking" deutlich reduziert wird.

Hardwarevoraussetzungen: 
  - Raspberrypi Versionen 2/3/4
  - SD-Karte mit mehr als 4 GB Speicherplatz

Download des Images dietPi-hole.img per Browser
  - Link only by invitation und temporär verfügbar. 

Empfehlung:
  - SD-Karte vorher prüfen. https://www.maketecheasier.com/check-sd-card-speed-capacity/#fake-flash-test
  - Firewall iptable rules erstellen und aktivieren.
  - Optional: DNS Anfragen nur vom Pi-hole erlauben. https://docs.pi-hole.net/routers/fritzbox-de/

Flashen der SD-Karte mit dem heruntergeladenen Image.
Zum Beispiel mit Balena Etcher:
  - macos https://github.com/balena-io/etcher/releases/download/v1.14.3/balenaEtcher-1.14.3.dmg
  - Linux https://github.com/balena-io/etcher#debian-and-ubuntu-based-package-repository-gnulinux-x86x64
  - Windows https://github.com/balena-io/etcher/releases/download/v1.14.3/balenaEtcher-Setup-1.14.3.exe

Remote Zugang per ssh für macOS, Linux oder Windows, nachdem der Raspi das erste mal hochfährt. 
Hinweis: Das Dollar Zeichen ($) bedeutet: als root den Befehl eingeben und mit Return abschließen, das
         Doppelkreuz (#) markiert Kommentare 

  Terminal/Putty:
  - $ssh root@ip-adress #ip-adress siehe Fritzbox
  - dietpi #das initiale Passwort
  - $dietpi-launcher #config tool https://dietpi.com/docs/dietpi_tools/
  - im Menüpunkt DietPi Config/Network options Adapters: DHCP auf STATIC ip-adress ändern
  - im Menüpunkt DietPi Config/Security options: das Passwort ändern

Fritz.box

  - Im Menü Heimnetz/Netzwerk dem dietPi-hole eine statische ip-adress geben.
  - Im Menü Internet/Zugangsdaten/DNS-Server in der Zeile Bevorzugter DNSv4-Server die statische ip-adress des dietPi-hole eintragen.

Pihole web login Passwort ändern

  Terminal/Putty:
  - $ssh root@ip-adress
  - $pihole -a -p # anschließend das neue Passwort eingeben

Aufruf der Pihole Seite
  - http://ip-adress/admin
  - das neue Passwort eingebn 

Funktionstest DNSSEC
  
  - https://dnscheck.tools im Browser aufrufen #die unteren drei Blöcke sollten grün sein (DNSSEC), in der unteren Statusleiste -> links unten in der Ecke: sollte ein Wert zwischen 50 ms und 70 ms (Performance) angezeigt werden.

Funktionstest Blocklisten und normales surfen

   Terminal/Putty:
  - $dig @localhost doubleclick.net #darf keine ip-adress anzeigen, stattdessen 0.0.0.0
  - $dig @localhost ard.de #sollte die ip-adress der ARD anzeigen

Updates:
  - Es wird automatisch auf updates geprüft, aber nicht automatisch das update eingespielt (Empfehlung der Pihole Entwickler). Man erkennt ein verfügbares update an der blinkenden Versionsangabe auf der admin Seite, ganz unten nach der Anmeldung auf http://ip-adress/admin 

  Terminal/Putty:
  - $pihole -up #eingeben, dann wird Pihole entsprechend aktualisiert
  - Die Blocklisten werden täglich und automatisch aktualisiert
