# redmatic-flow-sysinfo

Dieser Node Red Flow ist speziell für [RedMatic](https://github.com/hobbyquaker/RedMatic) und stellt verschiedene Systeminformationen der CCU Zentrale zur Verfügung:

 - Allgemeine Systeminformationen wie hostname, IP, kernel version, etc.
 - CPU Last
 - Speicher (RAM) Information
 - Festplattenspeicher
 - CCU Duty Cycle
 - CCU RSSI
 - UNREACH Devices
 - Automatische Bestätigung von STICKY_UNREACH
 - Überwachung von /var/log/messages und Anzeige der letzen 20 Fehlermeldungen

## Zusätzliche Nodes
Für die Systeminformationen wird zusätzlich die [Node OS](https://flows.nodered.org/node/node-red-contrib-os) benötigt.

## Flow

<img src="https://raw.githubusercontent.com/Sineos/redmatic-flow-sysinfo/master/src_readme/flow.png" width="400"/>

### Import Flow
Den Inhalt von [flow.md](https://raw.githubusercontent.com/Sineos/redmatic-flow-sysinfo/master/flow.md) kopieren und in Node-Red importieren.

## Dashboard

<img src="https://raw.githubusercontent.com/Sineos/redmatic-flow-sysinfo/master/src_readme/dash.png" width="400"/>
