# redmatic-flow-sysinfo

[German version of the ReadMe](https://github.com/Sineos/redmatic-flow-sysinfo/blob/master/README_DE.md) 

A Node Red flow especially for [RedMatic](https://github.com/hobbyquaker/RedMatic) to display system and CCU information:

 - General system information like hostname, IP, kernel version, etc.
 - CPU load
 - Memory information
 - Disk free information
 - CCU Duty Cycle
 - CCU RSSI

## Additional Nodes

For the system information the [Node OS](https://flows.nodered.org/node/node-red-contrib-os) is used.
Additionally the Node-RED [counter node](https://flows.nodered.org/node/node-red-contrib-counter) is required.

## Flow

<img src="https://raw.githubusercontent.com/Sineos/redmatic-flow-sysinfo/master/src_readme/flow.png" width="400"/>

### Import Flow

Copy content of the [raw flow.md](https://raw.githubusercontent.com/Sineos/redmatic-flow-sysinfo/master/flow.md) file and import via clipboard

## Dashboard

<img src="https://raw.githubusercontent.com/Sineos/redmatic-flow-sysinfo/master/src_readme/dash.png" width="400"/>
