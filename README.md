# dietPi-hole

Das Image dietPi-hole.img basiert auf dem Betriebssystem dietpi v8.14 und über den dietpi-launcher wurde Pihole installiert. Die Netzwerkkonfiguration ist auf DHCP voreingestellt. Dazu wurden 75 Blocklisten eingepflegt und die Funktion DNSSEC für die vier upstream DNS Server: 2x Cloudflair und 2x Quad9 aktiviert.

Remote Zugang per ssh

- Terminal:

- #ssh root@ipadresse ##siehe Fritzbox

- dietpi ##das initiale Passwort

- #dietpi-launcher ##config tool

- im Menüpunkt security das Passwort ändern

- im Menüpunkt Netzwerkadapter DHCP auf STATIC IP-Adresse ändern

Fritz.box

- Im Menü Heimnetz/Netzwerk dem dietPi-hole eine statische IP-Adresse geben.
- Im Menü Internet/Zugangsdaten/DNS-Server in der Zeile Bevorzugter DNSv4-Server die statische IP-Adresse des dietPi-hole eintragen.

Pihole web login Passwort ändern

Terminal
- #ssh root@ip-adresse
- #pihole -a -p

- Aufruf der Pihole Seite
  - https://ip-adresse/admin
  - das neue Passwort eingebn 

Funktionstest
  
  - https://dnscheck.tools
