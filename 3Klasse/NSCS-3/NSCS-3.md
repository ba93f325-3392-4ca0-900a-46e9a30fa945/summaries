# SYP 3. TEST
----------------------
# Lan Security
## Angrifssarten
### DDOS
- Botnet, bringt Server zum Absturz

### Data Breach
- Daten aus Netzwerk stehlen

### Maleware
- Malware auf PC bringen
- Lösegeld

## Lan Absicherung
### VPN
- Sichere Verbindung in unsicheren Verbindungen
### Firewall (Next Generation Firewall)
- Stateful packet inspection
- Next Generation intrusion (NGIPS)
- Advanced maleware protection (AMP)
- URL filtering

### Network Access Control (NAC)
- Authentication
- Authorization
- Accounting

### Endpoint protection
- z.B: Laptop, PC
- meist geschützt durch Antivirus oder Firewall

### AAA
- **Authentication**:
    - PC -> Server Verbindung aufnehmen
    - Überprüft Nutzer und Passwort
    - Entweder Lokal / Radius Server
- **Authorization**:
    - Rechte und Einschränkungen der User
- **Accounting**:
    - Loggt User Interaktionen

### 802.1x
- Verbindungsaufbau EAP Pakete
- Wenn erfolgreich, Port freigeben
- Auf Layer 2
- Nicht über MAC-Adressen, weil unsicher

### Angriffsvekorten
- layer 3+ sicherheitsmaßnahmen
- Layer 2 (LAN) besonders:
    - MAC Table Attacks
    - VLAN Attacks
    - DHCP Attacks
    - ARP Attacks
    - Address Spoofing

# Network Management
## SNMP
- Manager (Endgerät) sendet Anfragen an Agents (Router / Switch), liefert Daten zurück
- Agents können TRAP-Packete senden, unvorhergesehene Veränderungen mitteilen

### Management Information Base (MIB)
- TODO

## Syslog
- Speichert Userinteraktionen mit
### Severity Level
- Niedrigeres Level, Schlimmere Info
- nur <= *level* wird in LogServer geschrieben
    - Emergency -> Lvl 0
    - Alert -> Lvl 1
    - Critical -> Lvl 2
    - Error -> Lvl 3
    - Warning -> Lvl 4
    - Notification -> Lvl 5
    - Informational -> Lvl 6
    - Debugging -> Lvl 7

## NTP
- Ganz oben Atomuhr
- Unterliegenden Level erben von der Atomuhr
- Ab level 15 ungenau
- Für Netzwerke genaue Zeit wichtig zum debuggen

# WLAN Konzepte
- Standard: 802.11
- Ready To Send Paket zur Anfrage zum senden
- Clear To Send Paket zur Ack der Anfrage zum senden

## 2.4 GHz
- 2.400 - 2,4835 GHz
- sendbarer bereich 22 MHz groß
- vom Land abhängig ob 11 oder 13 Kanäle
- Nur 3 sendbare bereiche (ohne überlappungen)
- Nachbar selbe Frequenz, probleme

### Planung
- so ausrichten, dass die 3 bereiche sich nicht überlappen (in größeren Netzwerken)
### Sendeleistung
- Strahlenbelastung, Österreich max. 100mW erlaubt

## 5 GHz
- 200 mW erlaubt
- 19 überlappungsfreie Kanäle (20 MHz pro)

## Übertragungstechniken
### FHSS
- Frequenz bereich während Übertragung ändern
### DSSS
- durch *Frequenzspreizung* robuster gemacht
### OFDM
- Aufteilung der Infos auf mehrere Trägerfrequenzen

## MIMO
- Mutliple In / Multiple Out
- Kanäle parallel verwendet

## Verschlüsselung und Authentifizierung
### WEP
- Erste sicherheitsstandard, veraltet
- pre shared key (PSK) (8 zeichen, leicht hackbar)

### WPA1-WPA3 Personal
- SSID: Netzname
- Passwort: pre shared key (PSK)
- WPA2 verwendet AES (Advanced encryption standard) (Leistungsstarke Hardware benötigt)
- WPA2 MIM Attacke möglich.
- WPA3 Fehler beseitgt.

### WPA1-WPA3 Enterprise
- Radius Server
- Kümmert sich um anmeldungen (mittels Benutzer und Passwort)

# Network Design
## Three-tier layer
- Core layer
- Distribution layer
- Access layer

## Two-tier layer
- Core-Distribution layer
- Access layer

### Core Layer
- Connection to network
- Backbone

### Distribution Layer
- Connected to Core and Access Layer
- implements Routing, QualityOfService, Security
- limits layer 2 broadcast

### Access Layer
- Verbindung mit Endgeräten
- Connected to Distribution Layer

## Spine and Leaf
- Jeder Switch ist mit jedem Spine verbunden.
- Latency (less bottlenecks)
- Redundancy
- Spanning Tree Protocol (STP) (pakete nicht im kreis laufen)
