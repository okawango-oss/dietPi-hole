# dietPi-hole

Das Image dietPi-hole.img bestaht aus dem Betriebssystem dietpi v8.14. Über den dietpi-launcher wurde Pihole installiert. Die Netzwerkkonfiguration ist auf DHCP eingestellt. Dazu wurden 75 Blocklisten eingepflegt und DNSSEC für die upstream DNS Server: 2x Cloudflair und 2x Quad9 aktiviert.

Remote Zugang per ssh

- Terminal via cli:

- #ssh root@dietpi

- dietpi ##das initiale Passwort

- #dietpi-launcher ##config tool

- im Menüpunkt security das Passwort ändern

- im Menüpunkt Netzwerkadapter DHCP auf STATIC IP-Adresse ändern

Fritz.box

- Im Menü Heimnetz/Netzwerk dem dietPi-hole eine statische IP-Adresse geben.
- Im Menü Internet/Zugangsdaten/DNS-Server in der Zeile Bevorzugter DNSv4-Server die statische IP-Adresse des dietPi-hole eintragen.

Quellen:

https://dietpi.com/#downloadinfo

https://dietpi.com/docs/install/

https://pihole.net

https://docs.pi-hole.net
