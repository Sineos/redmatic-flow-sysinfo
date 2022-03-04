[
    {
        "id": "721e71e2.b201b8",
        "type": "tab",
        "label": "System"
    },
    {
        "id": "54d60add.25a174",
        "type": "inject",
        "z": "721e71e2.b201b8",
        "name": "Every 30 sec",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "30",
        "crontab": "",
        "once": true,
        "onceDelay": "",
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 140,
        "y": 60,
        "wires": [
            [
                "d2c19fd4.fa69f"
            ]
        ]
    },
    {
        "id": "1d9fe1f6.713cfe",
        "type": "ui_gauge",
        "z": "721e71e2.b201b8",
        "name": "CPU Load 1",
        "group": "6719ae8b.ab2f18",
        "order": 1,
        "width": "0",
        "height": "0",
        "gtype": "gage",
        "title": "1 Minute",
        "label": "load",
        "format": "{{value | number:2}}",
        "min": 0,
        "max": "4",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "className": "",
        "x": 710,
        "y": 180,
        "wires": []
    },
    {
        "id": "6f42956b.8d6e5c",
        "type": "ui_gauge",
        "z": "721e71e2.b201b8",
        "name": "CPU Load 2",
        "group": "6719ae8b.ab2f18",
        "order": 2,
        "width": "3",
        "height": "3",
        "gtype": "gage",
        "title": "5 Minutes",
        "label": "load",
        "format": "{{value | number:2}}",
        "min": 0,
        "max": "4",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "className": "",
        "x": 710,
        "y": 220,
        "wires": []
    },
    {
        "id": "3a2a5aec.9a9086",
        "type": "ui_gauge",
        "z": "721e71e2.b201b8",
        "name": "CPU Load 3",
        "group": "6719ae8b.ab2f18",
        "order": 4,
        "width": "3",
        "height": "3",
        "gtype": "gage",
        "title": "15 Minutes",
        "label": "load",
        "format": "{{value | number:2}}",
        "min": 0,
        "max": "4",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "className": "",
        "x": 710,
        "y": 260,
        "wires": []
    },
    {
        "id": "f07a6f0f.ff3ce8",
        "type": "ui_gauge",
        "z": "721e71e2.b201b8",
        "name": "Memory Usage",
        "group": "44fa2766.cd3658",
        "order": 1,
        "width": "0",
        "height": "0",
        "gtype": "gage",
        "title": "1 Minute",
        "label": "Usage [%]",
        "format": "{{value | number:2}}",
        "min": 0,
        "max": "100",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "className": "",
        "x": 700,
        "y": 460,
        "wires": []
    },
    {
        "id": "6f0fd6c8.4113f8",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Bytes to KB / MB / GB ...",
        "func": "function formatBytes(bytes, decimals) {\n  if(bytes === 0) return '0 Bytes';\n  const k = 1000,\n      dm = decimals || 2,\n      sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],\n      i = Math.floor(Math.log(bytes) / Math.log(k));\n  return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];\n}\n\nmsg.payload = formatBytes(msg.payload.totalmem);\nreturn msg;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 410,
        "y": 500,
        "wires": [
            [
                "4503002d.7210c"
            ]
        ]
    },
    {
        "id": "1727d1e7.42487e",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Bytes to KB / MB / GB ...",
        "func": "function formatBytes(bytes, decimals) {\n  if(bytes === 0) return '0 Bytes';\n  const k = 1000,\n      dm = decimals || 2,\n      sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],\n      i = Math.floor(Math.log(bytes) / Math.log(k));\n  return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];\n}\n\nmsg.payload = formatBytes(msg.payload.freemem);\nreturn msg;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 410,
        "y": 540,
        "wires": [
            [
                "42b8cf33.554e8"
            ]
        ]
    },
    {
        "id": "4503002d.7210c",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "44fa2766.cd3658",
        "order": 2,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "Total Memory",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 700,
        "y": 500,
        "wires": []
    },
    {
        "id": "42b8cf33.554e8",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "44fa2766.cd3658",
        "order": 3,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "Free Memory",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 710,
        "y": 540,
        "wires": []
    },
    {
        "id": "e62d6130.9604d8",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Seconds to d/h/min/s",
        "func": "let seconds = msg.payload.uptime;\nconst msg2 = {};\n\nconst days = Math.floor(seconds / (3600 * 24));\nseconds -= days * 3600 * 24;\nconst hrs = Math.floor(seconds / 3600);\nseconds -= hrs * 3600;\nconst mnts = Math.floor(seconds / 60);\nseconds -= mnts * 60;\nmsg2.payload = days + 'd / ' + hrs +'h / ' + mnts + 'min / ' + seconds + 's';\n\nreturn msg2;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 1322,
        "y": 180,
        "wires": [
            [
                "412ae744.d6845"
            ]
        ]
    },
    {
        "id": "412ae744.d6845",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 1,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "Uptime",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 1620,
        "y": 180,
        "wires": []
    },
    {
        "id": "e2d3a82c.dbb738",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 2,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "Hostname",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 1610,
        "y": 220,
        "wires": []
    },
    {
        "id": "2a18f44d.51f19c",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 4,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "Platform",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 1620,
        "y": 260,
        "wires": []
    },
    {
        "id": "8a5dabcb.1404a8",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 5,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "Arch",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 1630,
        "y": 300,
        "wires": []
    },
    {
        "id": "12055fd2.6ed998",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 6,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "Kernel",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 1630,
        "y": 340,
        "wires": []
    },
    {
        "id": "5b3958fa.4b1cc",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 7,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "No. of Cores",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 1610,
        "y": 400,
        "wires": []
    },
    {
        "id": "ddb8da22.25c0a",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 8,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "CPU",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 1630,
        "y": 440,
        "wires": []
    },
    {
        "id": "a40d1209.b57a2",
        "type": "ui_chart",
        "z": "721e71e2.b201b8",
        "name": "CPU Load - Historical",
        "group": "6719ae8b.ab2f18",
        "order": 0,
        "width": "0",
        "height": "0",
        "label": "24 Hours",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "86400",
        "cutout": "",
        "useOneColor": false,
        "useUTC": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "outputs": 1,
        "useDifferentColor": false,
        "className": "",
        "x": 680,
        "y": 140,
        "wires": [
            []
        ]
    },
    {
        "id": "277e3e0.6afe3c2",
        "type": "ui_chart",
        "z": "721e71e2.b201b8",
        "name": "Memory - 24 Hours",
        "group": "44fa2766.cd3658",
        "order": 0,
        "width": "0",
        "height": "0",
        "label": "24 Hours",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "86400",
        "cutout": "",
        "useOneColor": false,
        "useUTC": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "outputs": 1,
        "useDifferentColor": false,
        "className": "",
        "x": 690,
        "y": 420,
        "wires": [
            []
        ]
    },
    {
        "id": "f1f96121.1bf3b",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "CPU Load",
        "info": "",
        "x": 100,
        "y": 180,
        "wires": []
    },
    {
        "id": "22afdb11.4fa68c",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "Memory Usage",
        "info": "",
        "x": 120,
        "y": 440,
        "wires": []
    },
    {
        "id": "a0a27b6a.c82ca8",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "System Information",
        "info": "",
        "x": 1012,
        "y": 140,
        "wires": []
    },
    {
        "id": "7342f7e9.b955c8",
        "type": "OS",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 1092,
        "y": 300,
        "wires": [
            [
                "59413f83.02fe58",
                "661135f0.4b17d4",
                "8c21bc5a.fa1068",
                "149574ba.11116b"
            ]
        ]
    },
    {
        "id": "a9e91047.21ce48",
        "type": "Uptime",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 1082,
        "y": 180,
        "wires": [
            [
                "e62d6130.9604d8"
            ]
        ]
    },
    {
        "id": "ad9342a8.43498",
        "type": "CPUs",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 1092,
        "y": 420,
        "wires": [
            [
                "fc2cffc2.bcf3",
                "547cc5b3.c3e6dc"
            ]
        ]
    },
    {
        "id": "2531ebe3.98525c",
        "type": "Loadavg",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 180,
        "y": 220,
        "wires": [
            [
                "305b161a.b94ada",
                "27a89a3a.b44c1e",
                "f9ee339c.de0bf"
            ]
        ]
    },
    {
        "id": "6985eb41.81f08c",
        "type": "Memory",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 200,
        "y": 480,
        "wires": [
            [
                "6f0fd6c8.4113f8",
                "1727d1e7.42487e",
                "277e7f52.44b01"
            ]
        ]
    },
    {
        "id": "305b161a.b94ada",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "CPU Load 1 min",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.loadavg.0",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 440,
        "y": 180,
        "wires": [
            [
                "1d9fe1f6.713cfe",
                "a40d1209.b57a2"
            ]
        ]
    },
    {
        "id": "43c7216a.58de68",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Extract RSSI values",
        "func": "const rssi = msg.payload,\n             DBValues = [];\n\nlet msg2 = {},\n    centrals = [];\n\n// Identify available centrals: CCU, Gatesways, etc\n// If multiple centrals exist then the \"BidCoS-RF\" object exists\nif (rssi['BidCoS-RF']) {\n  centrals = Object.keys(rssi['BidCoS-RF']);\n} else {\n  // Object is unordered: Make sure we do not catch the CCU\n  const temp0 = Object.keys(rssi)[0];\n  const temp1 = Object.keys(rssi)[1];\n  if (Object.keys(rssi[temp0]).length === 1) {\n    centrals = (Object.keys(rssi[temp0]));\n  } else if (Object.keys(rssi[temp1]).length === 1) {\n    centrals = (Object.keys(rssi[temp1]));\n  } else {\n    node.error('No central identified');\n  }\n}\n\nfor (const central of centrals) {\n  for (const MyDevice of Object.keys((rssi)[central])) {\n    if (MyDevice !== 'BidCoS-RF') {\n      const device = {\n        central: central,\n        device: MyDevice,\n        down: (rssi[central][MyDevice][1] === 65536)? 'N/A':rssi[central][MyDevice][1],\n        up: (rssi[central][MyDevice][0] === 65536)? 'N/A':rssi[central][MyDevice][0]\n      };\n      DBValues.push(device);\n    }\n  }\n}\n\nmsg2 = {\n  payload: DBValues,\n  topic: msg.topic\n};\n\nreturn msg2;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 420,
        "y": 640,
        "wires": [
            [
                "6982e9d1.146ed"
            ]
        ]
    },
    {
        "id": "3bdb7a25.4a12be",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "CCU Signal Strength",
        "info": "",
        "x": 130,
        "y": 600,
        "wires": []
    },
    {
        "id": "84d9db66.3c127",
        "type": "ccu-rpc",
        "z": "721e71e2.b201b8",
        "name": "",
        "ccuConfig": "38263145.35ea0e",
        "iface": "BidCos-RF",
        "method": "listBidcosInterfaces",
        "params": "[]",
        "topic": "${CCU}/${Interface}/${Method}",
        "x": 1072,
        "y": 640,
        "wires": [
            [
                "15e18e55.7728e2"
            ]
        ]
    },
    {
        "id": "934645d.5a566b8",
        "type": "ui_chart",
        "z": "721e71e2.b201b8",
        "name": "Duty Cycle (1 hour)",
        "group": "4bbfb1c3.d86a",
        "order": 2,
        "width": 0,
        "height": 0,
        "label": "Duty Cycle (1 hour)",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "0",
        "ymax": "100",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "useUTC": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "outputs": 1,
        "useDifferentColor": false,
        "className": "",
        "x": 1570,
        "y": 620,
        "wires": [
            []
        ]
    },
    {
        "id": "f9ee339c.de0bf",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "CPU Load 5 min",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "msg.payload.loadavg.1",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 440,
        "y": 220,
        "wires": [
            [
                "6f42956b.8d6e5c"
            ]
        ]
    },
    {
        "id": "27a89a3a.b44c1e",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "CPU Load 15 min",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.loadavg.2",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 430,
        "y": 260,
        "wires": [
            [
                "3a2a5aec.9a9086"
            ]
        ]
    },
    {
        "id": "59413f83.02fe58",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.hostname",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1342,
        "y": 220,
        "wires": [
            [
                "e2d3a82c.dbb738"
            ]
        ]
    },
    {
        "id": "661135f0.4b17d4",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.platform",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1342,
        "y": 260,
        "wires": [
            [
                "2a18f44d.51f19c"
            ]
        ]
    },
    {
        "id": "8c21bc5a.fa1068",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.arch",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1342,
        "y": 300,
        "wires": [
            [
                "8a5dabcb.1404a8"
            ]
        ]
    },
    {
        "id": "149574ba.11116b",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.release",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1342,
        "y": 340,
        "wires": [
            [
                "12055fd2.6ed998"
            ]
        ]
    },
    {
        "id": "fc2cffc2.bcf3",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "$count($$.payload.cpus)",
                "tot": "jsonata"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1342,
        "y": 400,
        "wires": [
            [
                "5b3958fa.4b1cc"
            ]
        ]
    },
    {
        "id": "277e7f52.44b01",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.memusage",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 440,
        "y": 440,
        "wires": [
            [
                "277e3e0.6afe3c2",
                "f07a6f0f.ff3ce8"
            ]
        ]
    },
    {
        "id": "39865922.9fea3e",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "CCU Duty Cycle",
        "info": "",
        "x": 1002,
        "y": 600,
        "wires": []
    },
    {
        "id": "547cc5b3.c3e6dc",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.cpus.0.model",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1342,
        "y": 440,
        "wires": [
            [
                "ddb8da22.25c0a"
            ]
        ]
    },
    {
        "id": "d749f03d.a757a8",
        "type": "NetworkIntf",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 190,
        "y": 340,
        "wires": [
            [
                "4f96d45b.c30f3c"
            ]
        ]
    },
    {
        "id": "23ba2d65.42ebe2",
        "type": "Drives",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 1112,
        "y": 540,
        "wires": [
            [
                "3401234.56986dc"
            ]
        ]
    },
    {
        "id": "3401234.56986dc",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Reformat payload",
        "func": "function formatBytes(bytes, decimals) {\n  if(bytes === 0) return '0 Bytes';\n  const k = 1024,\n      dm = decimals || 2,\n      sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],\n      i = Math.floor(Math.log(bytes) / Math.log(k));\n  return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];\n}\n\nconst myArray = msg.payload;\nconst msg2 = {},\n    msg3 = {};\n\n// Reformat values to human readable\nconst newArray = myArray.map(function(v) {\n  return {\n    filesystem: v.filesystem,\n    size: formatBytes(v.size * 1024),\n    used: formatBytes(v.used * 1024),\n    available: formatBytes(v.available * 1024),\n    usedPercent: (v.capacity * 100).toFixed(0),\n    mount: v.mount\n  };\n});\nmsg2.payload = newArray;\n\n// Find '/usr/local'\nconst index = newArray.findIndex((x) => x.mount ==='/usr/local');\nmsg3.payload = newArray[index].usedPercent;\n\nreturn [msg2, msg3];\n",
        "outputs": 2,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 1332,
        "y": 540,
        "wires": [
            [
                "1f8dd99c.60645e"
            ],
            [
                "27ac74b1.18397c"
            ]
        ]
    },
    {
        "id": "27ac74b1.18397c",
        "type": "ui_gauge",
        "z": "721e71e2.b201b8",
        "name": "Disk Usage /usr/local",
        "group": "86c746d.7ab5db8",
        "order": 1,
        "width": "0",
        "height": "0",
        "gtype": "gage",
        "title": "/usr/local",
        "label": "Usage [%]",
        "format": "{{value | number:0}}",
        "min": 0,
        "max": "100",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "75",
        "seg2": "90",
        "className": "",
        "x": 1580,
        "y": 560,
        "wires": []
    },
    {
        "id": "4f703f6b.65213",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 3,
        "width": "0",
        "height": "0",
        "name": "",
        "label": "IP",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 730,
        "y": 340,
        "wires": []
    },
    {
        "id": "4f96d45b.c30f3c",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.networkInterfaces.eth0[0].address",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 440,
        "y": 340,
        "wires": [
            [
                "4f703f6b.65213"
            ]
        ]
    },
    {
        "id": "4a564c82.fe8564",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "Network Information",
        "info": "",
        "x": 130,
        "y": 300,
        "wires": []
    },
    {
        "id": "5fc7d08f.35363",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "Disk Information",
        "info": "",
        "x": 1002,
        "y": 500,
        "wires": []
    },
    {
        "id": "d2c19fd4.fa69f",
        "type": "link out",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "2905a362.32561c",
            "4c7acda3.e2b934",
            "700d0c79.9b3ba4",
            "865a64c1.dde128",
            "aaaa5b37.2cd678",
            "ad902d7f.3b30a",
            "c312f300.5a6f1",
            "d1b4ba2f.12b558",
            "d9a7811a.8e557"
        ],
        "x": 255,
        "y": 60,
        "wires": []
    },
    {
        "id": "2905a362.32561c",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 55,
        "y": 220,
        "wires": [
            [
                "2531ebe3.98525c"
            ]
        ]
    },
    {
        "id": "4c7acda3.e2b934",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 937,
        "y": 180,
        "wires": [
            [
                "a9e91047.21ce48"
            ]
        ]
    },
    {
        "id": "ad902d7f.3b30a",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 937,
        "y": 300,
        "wires": [
            [
                "7342f7e9.b955c8"
            ]
        ]
    },
    {
        "id": "d9a7811a.8e557",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 937,
        "y": 420,
        "wires": [
            [
                "ad9342a8.43498"
            ]
        ]
    },
    {
        "id": "865a64c1.dde128",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 55,
        "y": 340,
        "wires": [
            [
                "d749f03d.a757a8"
            ]
        ]
    },
    {
        "id": "700d0c79.9b3ba4",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 55,
        "y": 480,
        "wires": [
            [
                "6985eb41.81f08c"
            ]
        ]
    },
    {
        "id": "d1b4ba2f.12b558",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 937,
        "y": 540,
        "wires": [
            [
                "23ba2d65.42ebe2"
            ]
        ]
    },
    {
        "id": "aaaa5b37.2cd678",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 55,
        "y": 640,
        "wires": [
            [
                "fae4a20b.43cab8"
            ]
        ]
    },
    {
        "id": "c312f300.5a6f1",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "Inject30sec",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 937,
        "y": 640,
        "wires": [
            [
                "84d9db66.3c127"
            ]
        ]
    },
    {
        "id": "470b812a.842fe8",
        "type": "ccu-rpc-event",
        "z": "721e71e2.b201b8",
        "name": "UNREACH",
        "iface": "BidCos-RF",
        "ccuConfig": "38263145.35ea0e",
        "rooms": "",
        "roomsRx": "str",
        "functions": "",
        "functionsRx": "str",
        "device": "",
        "deviceRx": "str",
        "deviceName": "",
        "deviceNameRx": "str",
        "deviceType": "",
        "deviceTypeRx": "str",
        "channel": "",
        "channelRx": "str",
        "channelName": "",
        "channelNameRx": "str",
        "channelType": "MAINTENANCE",
        "channelTypeRx": "str",
        "channelIndex": "",
        "channelIndexRx": "str",
        "datapoint": "UNREACH",
        "datapointRx": "str",
        "change": true,
        "working": false,
        "cache": true,
        "topic": "${deviceName}",
        "x": 100,
        "y": 760,
        "wires": [
            [
                "d97bb44b.9dc928",
                "1e6c3c3f.56ab14"
            ]
        ]
    },
    {
        "id": "34d182a2.cd93ee",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "CCU (STICKY) UNREACH ",
        "info": "",
        "x": 150,
        "y": 720,
        "wires": []
    },
    {
        "id": "c36f11c1.a56ea",
        "type": "ccu-rpc-event",
        "z": "721e71e2.b201b8",
        "name": "STICKY_UNREACH",
        "iface": "BidCos-RF",
        "ccuConfig": "38263145.35ea0e",
        "rooms": "",
        "roomsRx": "str",
        "functions": "",
        "functionsRx": "str",
        "device": "",
        "deviceRx": "str",
        "deviceName": "",
        "deviceNameRx": "str",
        "deviceType": "",
        "deviceTypeRx": "str",
        "channel": "",
        "channelRx": "str",
        "channelName": "",
        "channelNameRx": "str",
        "channelType": "MAINTENANCE",
        "channelTypeRx": "str",
        "channelIndex": "",
        "channelIndexRx": "str",
        "datapoint": "STICKY_UNREACH",
        "datapointRx": "str",
        "change": false,
        "working": false,
        "cache": true,
        "topic": "${CCU}/${Interface}/${channelName}/${datapoint}",
        "x": 130,
        "y": 840,
        "wires": [
            [
                "1e6c3c3f.56ab14"
            ]
        ]
    },
    {
        "id": "1e6c3c3f.56ab14",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Log and Auto Ack",
        "func": "const msg2 = {};\nif (msg.payload === true &&\n    msg.datapoint === 'STICKY_UNREACH' &&\n    flow.get('unreachAutoAck', 'fileContext')) {\n  msg2.payload = `var dpAl = dom.GetObject(\"AL-${msg.channel}.${msg.datapoint}\");\n                dpAl.AlReceipt();`;\n  msg2.ts = (new Date(msg.ts)).toLocaleString('de-DE');\n  msg2.logMsg = 'ST_UR ack: ' + msg.deviceName;\n  return msg2;\n} else if (msg.payload === true &&\n           msg.datapoint === 'STICKY_UNREACH' &&\n           !flow.get('unreachAutoAck')) {\n  msg2.payload = null;\n  msg2.ts = (new Date(msg.ts)).toLocaleString('de-DE');\n  msg2.logMsg = msg.deviceName + ' is ST_UR';\n  return msg2;\n} else if (msg.payload === true && msg.datapoint === 'UNREACH') {\n  msg2.payload = null;\n  msg2.ts = (new Date(msg.ts)).toLocaleString('de-DE');\n  msg2.logMsg = 'UR: ' + msg.deviceName;\n  return msg2;\n} else if (msg.payload === false && msg.datapoint === 'UNREACH') {\n  msg2.payload = null;\n  msg2.ts = (new Date(msg.ts)).toLocaleString('de-DE');\n  msg2.logMsg = 'REACH: ' + msg.deviceName;\n  return msg2;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 370,
        "y": 840,
        "wires": [
            [
                "d52e8a70.e0a338",
                "c9bd1cf8.6ed038"
            ]
        ]
    },
    {
        "id": "fec5644b.ee045",
        "type": "ccu-script",
        "z": "721e71e2.b201b8",
        "name": "Execute AlReceipt",
        "script": "",
        "ccuConfig": "38263145.35ea0e",
        "topic": "${CCU}/${Interface}/",
        "x": 770,
        "y": 880,
        "wires": [
            []
        ]
    },
    {
        "id": "a0ba1733.3f27d",
        "type": "ui_switch",
        "z": "721e71e2.b201b8",
        "name": "Auto ACK S_UNREACH",
        "label": "Auto Acknowledge STICKY_UNREACH",
        "tooltip": "",
        "group": "40844f8.1cf98b",
        "order": 1,
        "width": "6",
        "height": "1",
        "passthru": true,
        "decouple": "false",
        "topic": "autoAck",
        "topicType": "str",
        "style": "",
        "onvalue": "true",
        "onvalueType": "bool",
        "onicon": "",
        "oncolor": "",
        "offvalue": "false",
        "offvalueType": "bool",
        "officon": "",
        "offcolor": "",
        "animate": true,
        "className": "",
        "x": 430,
        "y": 920,
        "wires": [
            [
                "d53a62a4.771478"
            ]
        ]
    },
    {
        "id": "d56511cf.ac0d1",
        "type": "ui_template",
        "z": "721e71e2.b201b8",
        "group": "40844f8.1cf98b",
        "name": "Log all UNREACH",
        "order": 4,
        "width": "6",
        "height": "6",
        "format": "<h3>(STICKY) UNREACH Event Log</h3>\n<table>\n  <tbody>\n    <tr>\n      <td><strong>Time Stamp</strong></td>\n      <td><strong>Device</strong></td>\n    </tr>\n    <tr ng-repeat=\"value in msg.payload\">\n      <td>{{value.ts}}</td>\n      <td>{{value.logMsg}}</td>\n    </tr>\n  </tbody>\n</table>",
        "storeOutMessages": true,
        "fwdInMessages": false,
        "resendOnRefresh": false,
        "templateScope": "local",
        "className": "",
        "x": 770,
        "y": 840,
        "wires": [
            []
        ]
    },
    {
        "id": "d52e8a70.e0a338",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Rotate Log",
        "func": "let dashboardLog = context.get('dashboardLog')|| [];\n\ndashboardLog.push(msg);\nif (dashboardLog.length > 20) {\n  // Delete oldest message if > 20\n  dashboardLog.shift();\n}\n\nif (msg.resetLog) {\n  dashboardLog = [];\n}\n\n// store the value back\ncontext.set('dashboardLog', dashboardLog);\n\n// make it part of the outgoing msg object\nmsg = {};\nmsg.payload = dashboardLog;\nreturn msg;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 570,
        "y": 840,
        "wires": [
            [
                "d56511cf.ac0d1"
            ]
        ]
    },
    {
        "id": "d97bb44b.9dc928",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Log Currently UNREACH",
        "func": "const msg2 = {};\nlet unreachCount = context.get('unreachCount') || 0;\n\nif (msg.payload === true) {\n  unreachCount += 1;\n  context.set('unreachCount', unreachCount);\n  msg2.topic = msg.topic;\n  msg2.addLog = true;\n  msg2.payload = unreachCount;\n  msg2.ts = (new Date(msg.ts)).toLocaleString('de-DE');\n  msg2.deviceName = msg.deviceName;\n  return msg2;\n} else if (msg.payload === false) {\n  unreachCount -= 1;\n  context.set('unreachCount', unreachCount);\n  msg2.payload = unreachCount;\n  msg2.topic = msg.topic;\n  msg2.delLog = true;\n  return msg2;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 350,
        "y": 760,
        "wires": [
            [
                "a74849f2.c5f9c8"
            ]
        ]
    },
    {
        "id": "a74849f2.c5f9c8",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Rotate Log",
        "func": "'use strict';\n// Set the maximum length of the log\nconst logMaxLength = 20;\n\n// To dynamically add and remove entries\n// an identifier to distinguish the entries\n// needs to be set. Typically 'topic' is used\nconst logIdentifier = 'topic';\n\n\nlet dashboardLog = context.get('dashboardLog')|| [];\n\nif (!msg.delLog) {\n  dashboardLog.push(msg);\n  if (dashboardLog.length > logMaxLength) {\n  // Delete oldest message if > 20\n    dashboardLog.shift();\n  }\n} else if (msg.delLog) {\n//  if (dashboardLog.findIndex((v) => v[logIdentifier] === msg[logIdentifier])) {\n  dashboardLog.splice(dashboardLog.findIndex((v) => v[logIdentifier] === msg[logIdentifier]), 1);\n//  }\n}\n\nif (msg.resetLog) {\n  dashboardLog = [];\n}\n\n// store the value back\ncontext.set('dashboardLog', dashboardLog);\n\n// make it part of the outgoing msg object\nmsg = {};\nmsg.payload = dashboardLog;\nreturn msg;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 570,
        "y": 760,
        "wires": [
            [
                "b3f94a49.8789d"
            ]
        ]
    },
    {
        "id": "b3f94a49.8789d",
        "type": "ui_template",
        "z": "721e71e2.b201b8",
        "group": "40844f8.1cf98b",
        "name": "Log UR Devices",
        "order": 3,
        "width": "6",
        "height": "6",
        "format": "<h3>Currently UNREACH Devices</h3>\n<table>\n  <tbody>\n    <tr>\n      <td><strong>Time Stamp</strong></td>\n      <td><strong>Device</strong></td>\n    </tr>\n    <tr ng-repeat=\"value in msg.payload\">\n      <td>{{value.ts}}</td>\n      <td>{{value.deviceName}}</td>\n    </tr>\n  </tbody>\n</table>",
        "storeOutMessages": true,
        "fwdInMessages": false,
        "resendOnRefresh": false,
        "templateScope": "local",
        "className": "",
        "x": 780,
        "y": 760,
        "wires": [
            []
        ]
    },
    {
        "id": "c9bd1cf8.6ed038",
        "type": "switch",
        "z": "721e71e2.b201b8",
        "name": "not null",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "nnull"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 1,
        "x": 580,
        "y": 880,
        "wires": [
            [
                "fec5644b.ee045"
            ]
        ]
    },
    {
        "id": "1ee6074e.956ce1",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "resetLog",
                "pt": "msg",
                "to": "payload",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 550,
        "y": 960,
        "wires": [
            [
                "6a2f8fc5.791508"
            ]
        ]
    },
    {
        "id": "238b52bf.b6169e",
        "type": "ui_button",
        "z": "721e71e2.b201b8",
        "name": "",
        "group": "40844f8.1cf98b",
        "order": 2,
        "width": "6",
        "height": "1",
        "passthru": false,
        "label": "Reset Logs",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "",
        "icon": "",
        "payload": "true",
        "payloadType": "bool",
        "topic": "",
        "topicType": "str",
        "x": 110,
        "y": 960,
        "wires": [
            [
                "1ee6074e.956ce1"
            ]
        ]
    },
    {
        "id": "693adfa4.9b4a78",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "logReset",
        "links": [
            "6a2f8fc5.791508"
        ],
        "x": 435,
        "y": 800,
        "wires": [
            [
                "a74849f2.c5f9c8",
                "d52e8a70.e0a338"
            ]
        ]
    },
    {
        "id": "6a2f8fc5.791508",
        "type": "link out",
        "z": "721e71e2.b201b8",
        "name": "logReset",
        "links": [
            "693adfa4.9b4a78"
        ],
        "x": 700,
        "y": 960,
        "wires": []
    },
    {
        "id": "3b77e1a4.fd8716",
        "type": "switch",
        "z": "721e71e2.b201b8",
        "name": "Filter Errors",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "regex",
                "v": "^.*Error\\:.*",
                "vt": "str",
                "case": true
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 1,
        "x": 1210,
        "y": 800,
        "wires": [
            [
                "93870c97.d4095"
            ]
        ]
    },
    {
        "id": "93870c97.d4095",
        "type": "counter",
        "z": "721e71e2.b201b8",
        "name": "Count Errors",
        "init": "0",
        "step": "1",
        "lower": "",
        "upper": "",
        "mode": "increment",
        "outputs": 2,
        "x": 1390,
        "y": 800,
        "wires": [
            [
                "2c79e224.516d7e"
            ],
            [
                "e570c8c5.d2137",
                "73aa8f33.1ffab"
            ]
        ]
    },
    {
        "id": "2c79e224.516d7e",
        "type": "ui_gauge",
        "z": "721e71e2.b201b8",
        "name": "Show Error Count",
        "group": "109dc147.190c8f",
        "order": 11,
        "width": "6",
        "height": "4",
        "gtype": "gage",
        "title": "Error Count",
        "label": "Fehler",
        "format": "{{value}}",
        "min": 0,
        "max": "100",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "className": "",
        "x": 1590,
        "y": 780,
        "wires": []
    },
    {
        "id": "e570c8c5.d2137",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Rotate Log",
        "func": "let dashboardLog = context.get('dashboardLog')|| [];\nconst msg2 = {};\n\ndashboardLog.push(msg);\nif (dashboardLog.length > 20) {\n  // Delete oldest message if > 20\n  dashboardLog.shift();\n  //dashboardLog.length = 20;\n}\n\nif (msg.resetlog) {\n  dashboardLog = [];\n}\n\n// store the value back\ncontext.set('dashboardLog', dashboardLog);\n\n// make it part of the outgoing msg object\nmsg2.payload = dashboardLog.reverse();\nreturn msg2;\n",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 1570,
        "y": 860,
        "wires": [
            [
                "30ea94e7.a134dc"
            ]
        ]
    },
    {
        "id": "aaca1586.e7f59",
        "type": "join",
        "z": "721e71e2.b201b8",
        "name": "Prepare Message",
        "mode": "custom",
        "build": "string",
        "property": "payload",
        "propertyType": "msg",
        "key": "topic",
        "joiner": "\\r\\n",
        "joinerType": "str",
        "accumulate": false,
        "timeout": "",
        "count": "5",
        "reduceRight": false,
        "reduceExp": "",
        "reduceInit": "",
        "reduceInitType": "num",
        "reduceFixup": "",
        "x": 1750,
        "y": 820,
        "wires": [
            [
                "3d15ebf0.f953f4"
            ]
        ]
    },
    {
        "id": "3d15ebf0.f953f4",
        "type": "e-mail",
        "z": "721e71e2.b201b8",
        "server": "smtp.gmail.com",
        "port": "465",
        "secure": true,
        "tls": false,
        "name": "",
        "dname": "Send Email",
        "x": 1930,
        "y": 820,
        "wires": []
    },
    {
        "id": "28946e0.d7af792",
        "type": "comment",
        "z": "721e71e2.b201b8",
        "name": "Monitor var/log/messages",
        "info": "",
        "x": 1030,
        "y": 720,
        "wires": []
    },
    {
        "id": "bcc65720.30194",
        "type": "ui_button",
        "z": "721e71e2.b201b8",
        "name": "Reset Error Count",
        "group": "109dc147.190c8f",
        "order": 12,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Reset",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "",
        "icon": "",
        "payload": "true",
        "payloadType": "bool",
        "topic": "",
        "topicType": "str",
        "x": 1010,
        "y": 760,
        "wires": [
            [
                "4a243311.c4dd1c"
            ]
        ]
    },
    {
        "id": "4a243311.c4dd1c",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "Set Reset Message",
        "rules": [
            {
                "t": "set",
                "p": "reset",
                "pt": "msg",
                "to": "true",
                "tot": "bool"
            },
            {
                "t": "set",
                "p": "topic",
                "pt": "msg",
                "to": "Reset Error Count",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1230,
        "y": 760,
        "wires": [
            [
                "93870c97.d4095"
            ]
        ]
    },
    {
        "id": "fb28037c.3bbd3",
        "type": "ui_button",
        "z": "721e71e2.b201b8",
        "name": "Clear DashLog",
        "group": "109dc147.190c8f",
        "order": 14,
        "width": 0,
        "height": 0,
        "passthru": false,
        "label": "Clear Error Log",
        "tooltip": "",
        "color": "",
        "bgcolor": "",
        "className": "",
        "icon": "",
        "payload": "true",
        "payloadType": "bool",
        "topic": "",
        "topicType": "str",
        "x": 1000,
        "y": 860,
        "wires": [
            [
                "37fa680c.330b8"
            ]
        ]
    },
    {
        "id": "37fa680c.330b8",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "Set Reset Message",
        "rules": [
            {
                "t": "set",
                "p": "resetlog",
                "pt": "msg",
                "to": "true",
                "tot": "bool"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1230,
        "y": 860,
        "wires": [
            [
                "e570c8c5.d2137"
            ]
        ]
    },
    {
        "id": "e466140e.07ec08",
        "type": "ui_switch",
        "z": "721e71e2.b201b8",
        "name": "",
        "label": "Send Email With Logged Errors",
        "tooltip": "",
        "group": "109dc147.190c8f",
        "order": 10,
        "width": 0,
        "height": 0,
        "passthru": true,
        "decouple": "false",
        "topic": "",
        "topicType": "str",
        "style": "",
        "onvalue": "true",
        "onvalueType": "bool",
        "onicon": "",
        "oncolor": "",
        "offvalue": "false",
        "offvalueType": "bool",
        "officon": "",
        "offcolor": "",
        "animate": true,
        "className": "",
        "x": 1050,
        "y": 900,
        "wires": [
            [
                "59d96c62.3e9824"
            ]
        ]
    },
    {
        "id": "59d96c62.3e9824",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "errorEmail",
                "pt": "flow",
                "to": "payload",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1310,
        "y": 900,
        "wires": [
            []
        ]
    },
    {
        "id": "73aa8f33.1ffab",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Send Email?",
        "func": "if (flow.get('errorEmail')) {\n  return msg;\n}",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 1570,
        "y": 820,
        "wires": [
            [
                "aaca1586.e7f59"
            ]
        ]
    },
    {
        "id": "33ade3c2.c8918c",
        "type": "ui_text",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "order": 9,
        "width": 0,
        "height": 0,
        "name": "Monitor /var/log/messages",
        "label": "<h3>Monitor /var/log/messages</h3>",
        "format": "",
        "layout": "row-left",
        "className": "",
        "x": 1040,
        "y": 940,
        "wires": []
    },
    {
        "id": "30ea94e7.a134dc",
        "type": "ui_template",
        "z": "721e71e2.b201b8",
        "group": "109dc147.190c8f",
        "name": "Recent Errors",
        "order": 13,
        "width": "6",
        "height": "4",
        "format": "<ul>\n <li ng-repeat=\"x in msg.payload\">\n <font color=\"red\">{{x.topic}}</font>\n    <ul>\n        <li>{{x.payload}}</li>\n    </ul>\n </li>\n</ul>",
        "storeOutMessages": false,
        "fwdInMessages": false,
        "resendOnRefresh": false,
        "templateScope": "local",
        "className": "",
        "x": 1760,
        "y": 860,
        "wires": [
            []
        ]
    },
    {
        "id": "fae4a20b.43cab8",
        "type": "ccu-rpc",
        "z": "721e71e2.b201b8",
        "name": "",
        "ccuConfig": "38263145.35ea0e",
        "iface": "BidCos-RF",
        "method": "rssiInfo",
        "params": "[]",
        "topic": "${CCU}/${Interface}/${Method}",
        "x": 200,
        "y": 640,
        "wires": [
            [
                "43c7216a.58de68"
            ]
        ]
    },
    {
        "id": "d53a62a4.771478",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "#:(file)::unreachAutoAck",
                "pt": "flow",
                "to": "payload",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 750,
        "y": 920,
        "wires": [
            []
        ]
    },
    {
        "id": "d5d9b78e.8f4008",
        "type": "inject",
        "z": "721e71e2.b201b8",
        "name": "",
        "repeat": "",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "#:(file)::unreachAutoAck",
        "payloadType": "flow",
        "x": 160,
        "y": 920,
        "wires": [
            [
                "a0ba1733.3f27d"
            ]
        ]
    },
    {
        "id": "95f86589.b6c37",
        "type": "tail",
        "z": "721e71e2.b201b8",
        "name": "",
        "filetype": "text",
        "split": "true",
        "filename": "/var/log/messages",
        "inputs": 0,
        "x": 1010,
        "y": 800,
        "wires": [
            [
                "3b77e1a4.fd8716"
            ]
        ]
    },
    {
        "id": "b30e50c8.b1e23",
        "type": "ui_table",
        "z": "721e71e2.b201b8",
        "group": "b533a88a.2e9378",
        "name": "RSSI Table",
        "order": 2,
        "width": "6",
        "height": "11",
        "columns": [],
        "outputs": 1,
        "cts": true,
        "x": 750,
        "y": 640,
        "wires": [
            []
        ]
    },
    {
        "id": "6982e9d1.146ed",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "ui_control",
        "rules": [
            {
                "t": "set",
                "p": "ui_control",
                "pt": "msg",
                "to": "{\"tabulator\":{\"columnResized\":\"function(column){var newColumn = {field: column._column.field, visible: column._column.visible, width: column._column.width, widthFixed: column._column.widthFixed, widthStyled: column._column.widthStyled};this.send({topic:this.config.topic,ui_control:{callback:'columnResized',columnWidths:newColumn}});}\",\"columnMoved\":\"function(column, columns){var newColumns=[];columns.forEach(function (column) {newColumns.push({'field': column._column.field});});this.send({topic:this.config.topic,ui_control:{callback:'columnMoved',columns:newColumns}});}\",\"layout\":\"fitColumns\",\"columns\":[{\"title\":\"Device\",\"field\":\"device\",\"formatter\":\"function(cell, formatterParams, onRendered){return cell.getValue();}\"},{\"title\":\"<div style='text-align:center'><i class='fa fa-arrow-circle-up' aria-hidden='true'></i></div>\",\"align\":\"center\",\"field\":\"up\",\"formatter\":\"function(cell, formatterParams){ var html_excel = 'style=\\\"color:#00cc44\\\"></i>'; var html_good = 'style=\\\"color:#66ff66\\\"></i>'; var html_aver = 'style=\\\"color:#ff8c66\\\"></i>'; var html_bad = 'style=\\\"color:#ff6666\\\"></i>'; var html='<i class=\\\"fa fa-circle fa-fw\\\" '; var value = cell.getValue(); if (value >= -50) { value = value + html + html_excel} else if (value <= -51 && value >= -100) { value = value + html + html_good; } else if (value <= -101 && value >= -120) { value = value + html + html_aver; } else if (value <= -120) { value = value + html + html_bad}; return value;}\"},{\"title\":\"<div style='text-align:center'><i class='fa fa-arrow-circle-down' aria-hidden='true'></i></div>\",\"field\":\"down\",\"align\":\"center\",\"formatter\":\"function(cell, formatterParams){ var html_excel = 'style=\\\"color:#00cc44\\\"></i>'; var html_good = 'style=\\\"color:#66ff66\\\"></i>'; var html_aver = 'style=\\\"color:#ff8c66\\\"></i>'; var html_bad = 'style=\\\"color:#ff6666\\\"></i>'; var html='<i class=\\\"fa fa-circle fa-fw\\\" '; var value = cell.getValue(); if (value >= -50) { value = value + html + html_excel} else if (value <= -51 && value >= -100) { value = value + html + html_good; } else if (value <= -101 && value >= -120) { value = value + html + html_aver; } else if (value <= -120) { value = value + html + html_bad}; return value;}\"}],\"movableColumns\":true,\"groupBy\":\"central\"},\"customHeight\":55}",
                "tot": "json"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 600,
        "y": 640,
        "wires": [
            [
                "b30e50c8.b1e23"
            ]
        ]
    },
    {
        "id": "1f8dd99c.60645e",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "ui_control",
        "rules": [
            {
                "t": "set",
                "p": "ui_control",
                "pt": "msg",
                "to": "{\"tabulator\":{\"columnResized\":\"function(column){var newColumn = {field: column._column.field, visible: column._column.visible, width: column._column.width, widthFixed: column._column.widthFixed, widthStyled: column._column.widthStyled};this.send({topic:this.config.topic,ui_control:{callback:'columnResized',columnWidths:newColumn}});}\",\"columnMoved\":\"function(column, columns){var newColumns=[];columns.forEach(function (column) {newColumns.push({'field': column._column.field});});this.send({topic:this.config.topic,ui_control:{callback:'columnMoved',columns:newColumns}});}\",\"layout\":\"fitColumns\",\"columns\":[{\"title\":\"Mount\",\"field\":\"mount\",\"formatter\":\"function(cell, formatterParams, onRendered){return cell.getValue();}\"},{\"title\":\"<div style='text-align:center'>Size</i></div>\",\"align\":\"center\",\"field\":\"size\",\"formatter\":\"function(cell, formatterParams, onRendered){return cell.getValue();}\"},{\"title\":\"<div style='text-align:center'>Used</i></div>\",\"field\":\"used\",\"align\":\"center\",\"formatter\":\"function(cell, formatterParams, onRendered){return cell.getValue();}\"},{\"title\":\"<div style='text-align:center'>Free</i></div>\",\"field\":\"available\",\"align\":\"center\",\"formatter\":\"function(cell, formatterParams, onRendered){return cell.getValue();}\"},{\"title\":\"<div style='text-align:center'>Used %</i></div>\",\"field\":\"usedPercent\",\"align\":\"center\",\"formatter\":\"function(cell, formatterParams){ var html_excel = 'style=\\\"color:#00cc44\\\"></i>'; var html_aver = 'style=\\\"color:#ff8c66\\\"></i>'; var html_bad = 'style=\\\"color:#ff6666\\\"></i>'; var html='<i class=\\\"fa fa-circle fa-fw\\\" '; var value = cell.getValue(); if (value <= 75) { value = value + '%' + html + html_excel} else if (value >= 76 && value < 94) { value = value + '%' + html + html_aver; } else if (value >= 95) { value = value + '%' + html + html_bad}; return value;}\"}],\"movableColumns\":true,\"groupBy\":\"\"},\"customHeight\":55}",
                "tot": "json"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1540,
        "y": 520,
        "wires": [
            [
                "5492165d.78661"
            ]
        ]
    },
    {
        "id": "5492165d.78661",
        "type": "ui_table",
        "z": "721e71e2.b201b8",
        "group": "86c746d.7ab5db8",
        "name": "Disk Usage",
        "order": 2,
        "width": "8",
        "height": "9",
        "columns": [],
        "outputs": 1,
        "cts": true,
        "x": 1690,
        "y": 520,
        "wires": [
            []
        ]
    },
    {
        "id": "15e18e55.7728e2",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Extract DC values",
        "func": "const DutyCycle = msg.payload,\n      OutMsgs = [],\n      msg2 = {};\n\nfor (const element of DutyCycle) {\n  const result = {\n    topic: element['ADDRESS'],\n    payload: element['DUTY_CYCLE']\n  };\n  OutMsgs.push(result);\n  // The default central (i.e. the CCU) will be returned on the second output\n  if (element['DEFAULT'] === true) {\n    msg2.topic = element['ADDRESS'];\n    msg2.payload = element['DUTY_CYCLE'];\n  }\n}\n\nreturn [OutMsgs, msg2];\n\n",
        "outputs": 2,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "x": 1330,
        "y": 640,
        "wires": [
            [
                "934645d.5a566b8",
                "933be049.370c28"
            ],
            []
        ]
    },
    {
        "id": "933be049.370c28",
        "type": "ui_chart",
        "z": "721e71e2.b201b8",
        "name": "Duty Cycle (Current)",
        "group": "4bbfb1c3.d86a",
        "order": 1,
        "width": 0,
        "height": 0,
        "label": "Duty Cycle (Current)",
        "chartType": "horizontalBar",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "0",
        "ymax": "100",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "useUTC": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "outputs": 1,
        "useDifferentColor": false,
        "className": "",
        "x": 1580,
        "y": 660,
        "wires": [
            []
        ]
    },
    {
        "id": "6719ae8b.ab2f18",
        "type": "ui_group",
        "name": "CPU Load",
        "tab": "189e0ea3.dd5dd1",
        "order": 4,
        "disp": true,
        "width": "6"
    },
    {
        "id": "44fa2766.cd3658",
        "type": "ui_group",
        "name": "Memory",
        "tab": "189e0ea3.dd5dd1",
        "order": 5,
        "disp": true,
        "width": "6"
    },
    {
        "id": "109dc147.190c8f",
        "type": "ui_group",
        "name": "System Information",
        "tab": "189e0ea3.dd5dd1",
        "order": 1,
        "disp": true,
        "width": "6"
    },
    {
        "id": "38263145.35ea0e",
        "type": "ccu-connection",
        "name": "localhost",
        "host": "localhost",
        "regaEnabled": true,
        "bcrfEnabled": true,
        "iprfEnabled": true,
        "virtEnabled": true,
        "bcwiEnabled": false,
        "cuxdEnabled": false,
        "regaPoll": true,
        "regaInterval": "30",
        "rpcPingTimeout": "60",
        "rpcInitAddress": "192.168.178.18",
        "rpcServerHost": "192.168.178.18",
        "rpcBinPort": "2047",
        "rpcXmlPort": "2048",
        "tls": false,
        "inSecure": false,
        "authentication": false,
        "username": "",
        "password": "",
        "queueTimeout": "5000",
        "queuePause": "250",
        "contextStore": "default"
    },
    {
        "id": "4bbfb1c3.d86a",
        "type": "ui_group",
        "name": "CCU Duty Cycle",
        "tab": "189e0ea3.dd5dd1",
        "order": 2,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "86c746d.7ab5db8",
        "type": "ui_group",
        "name": "Disk",
        "tab": "189e0ea3.dd5dd1",
        "order": 6,
        "disp": true,
        "width": "8",
        "collapse": false
    },
    {
        "id": "40844f8.1cf98b",
        "type": "ui_group",
        "name": "UNREACH",
        "tab": "189e0ea3.dd5dd1",
        "order": 3,
        "disp": true,
        "width": "6",
        "collapse": false
    },
    {
        "id": "b533a88a.2e9378",
        "type": "ui_group",
        "name": "CCU RSSI",
        "tab": "189e0ea3.dd5dd1",
        "order": 7,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "189e0ea3.dd5dd1",
        "type": "ui_tab",
        "name": "System",
        "icon": "computer",
        "order": 7
    }
]