# dietPi-hole

Das Image dietPi-hole.img basiert auf dem Betriebssystem dietpi v8.14. Mittels dietpi-launcher wurde Pihole aus dem selben repository installiert. Die Netzwerkkonfiguration wurde auf DHCP voreingestellt. Dazu wurden 75 Blocklisten eingepflegt und die Option DNSSEC für die vier upstream DNS Server aktiviert: 2x Cloudflare und 2x Quad9.

Hardwarevoraussetzungen: 
- Raspberrypi Versionen 2/3/4
- SD-Karte mit mehr als 8 GB Speicherplatz

Download des Image dietPi-hole.img per Browser
- Link einfügen

Flashen der SD-Karte mit dem heruntergeladenen Image
Zum Beispiel mit Balena Etcher:
- macos https://github.com/balena-io/etcher/releases/download/v1.14.3/balenaEtcher-1.14.3.dmg
- Linux https://github.com/balena-io/etcher#debian-and-ubuntu-based-package-repository-gnulinux-x86x64
- Windows https://github.com/balena-io/etcher/releases/download/v1.14.3/balenaEtcher-Setup-1.14.3.exe

Remote Zugang per ssh für macOS oder Linux
Hinweis: Dollar Zeichen ($) bedeutet als root den Befehl eingeben und mit Return abschließen
         Doppelkreuze (#) markieren Kommentare 
  Terminal:
- $wget https://... #Download des Images, falls noch nicht geschehen, ansonsten überspringen
- $ssh root@ipadresse #ip-adresse siehe Fritzbox
- dietpi #das initiale Passwort
- $dietpi-launcher #config tool
- im Menüpunkt GENAUER security das Passwort ändern
- im Menüpunkt GENAUER Netzwerkadapter DHCP auf STATIC IP-Adresse ändern

Fritz.box

- Im Menü Heimnetz/Netzwerk dem dietPi-hole eine statische IP-Adresse geben.
- Im Menü Internet/Zugangsdaten/DNS-Server in der Zeile Bevorzugter DNSv4-Server die statische IP-Adresse des dietPi-hole eintragen.

Pihole web login Passwort ändern

Terminal
- $ssh root@ip-adresse
- $pihole -a -p

- Aufruf der Pihole Seite
  - https://ip-adresse/admin
  - das neue Passwort eingebn 

Funktionstest
  
  - https://dnscheck.tools im Browser aufrufen
