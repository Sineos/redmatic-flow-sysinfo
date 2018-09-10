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
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "repeat": "30",
        "crontab": "",
        "once": true,
        "onceDelay": "",
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
        "x": 690,
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
        "x": 690,
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
        "x": 690,
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
        "x": 680,
        "y": 460,
        "wires": []
    },
    {
        "id": "6f0fd6c8.4113f8",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Bytes to KB / MB / GB ...",
        "func": "function formatBytes(bytes, decimals) {\n  if(bytes === 0) return '0 Bytes';\n  var k = 1024,\n      dm = decimals || 2,\n      sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],\n      i = Math.floor(Math.log(bytes) / Math.log(k));\n  return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];\n}\n\nmsg.payload = formatBytes(msg.payload.totalmem);\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
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
        "func": "function formatBytes(bytes, decimals) {\n  if(bytes === 0) return '0 Bytes';\n  var k = 1024,\n      dm = decimals || 2,\n      sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],\n      i = Math.floor(Math.log(bytes) / Math.log(k));\n  return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];\n}\n\nmsg.payload = formatBytes(msg.payload.freemem);\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
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
        "x": 680,
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
        "x": 690,
        "y": 540,
        "wires": []
    },
    {
        "id": "e62d6130.9604d8",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Seconds to d/h/min/s",
        "func": "var seconds = msg.payload.uptime\nvar msg2 = {};\n\nvar days = Math.floor(seconds / (3600*24));\nseconds  -= days*3600*24;\nvar hrs   = Math.floor(seconds / 3600);\nseconds  -= hrs*3600;\nvar mnts = Math.floor(seconds / 60);\nseconds  -= mnts*60;\nmsg2.payload = days + \"d / \" + hrs +\"h / \" + mnts + \"min / \" + seconds + \"s\";\n\nreturn msg2;",
        "outputs": 1,
        "noerr": 0,
        "x": 1240,
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
        "x": 1520,
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
        "x": 1510,
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
        "x": 1520,
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
        "x": 1530,
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
        "x": 1530,
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
        "x": 1510,
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
        "x": 1530,
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
        "useOldStyle": false,
        "x": 660,
        "y": 140,
        "wires": [
            [],
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
        "useOldStyle": false,
        "x": 670,
        "y": 420,
        "wires": [
            [],
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
        "x": 930,
        "y": 140,
        "wires": []
    },
    {
        "id": "7342f7e9.b955c8",
        "type": "OS",
        "z": "721e71e2.b201b8",
        "name": "",
        "x": 1010,
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
        "x": 1000,
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
        "x": 1010,
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
        "id": "5ab12bc9.a0b8b4",
        "type": "ccu-rpc",
        "z": "721e71e2.b201b8",
        "name": "",
        "ccuConfig": "38263145.35ea0e",
        "iface": "BidCos-RF",
        "method": "rssiInfo",
        "params": "",
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
        "id": "43c7216a.58de68",
        "type": "function",
        "z": "721e71e2.b201b8",
        "name": "Extract RSSI values",
        "func": "'use strict';\nvar rssi = msg.payload;\nvar myRSSIObj = {},\n    myDBValues = [],\n    ccu = '',\n    msg2 = {};\n\n//ccu = Object.keys(rssi)[Object.keys(rssi).length-1];\nccu = Object.keys(rssi).find(function(key) {\n  return key.endsWith('0');\n});\n\nfor (var key of Object.keys(rssi)) {\n  if (key !== ccu) {\n    myDBValues.push(rssi[key][ccu][1]);\n    myDBValues.push(rssi[ccu][key][0]);\n    myRSSIObj[key] = myDBValues;\n    myDBValues = [];\n  }\n}\n\nmsg2 = {\n  payload: myRSSIObj,\n  topic: msg.topic,\n  ccu: ccu\n};\n\nreturn msg2;\n",
        "outputs": 1,
        "noerr": 0,
        "x": 420,
        "y": 640,
        "wires": [
            [
                "5fd974a1.743d8c"
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
        "x": 990,
        "y": 640,
        "wires": [
            [
                "598712df.312fb4"
            ]
        ]
    },
    {
        "id": "934645d.5a566b8",
        "type": "ui_chart",
        "z": "721e71e2.b201b8",
        "name": "Chart",
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
        "useOldStyle": false,
        "x": 1530,
        "y": 621,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "dee433fb.ab2e98",
        "type": "ui_gauge",
        "z": "721e71e2.b201b8",
        "name": "Gauge",
        "group": "4bbfb1c3.d86a",
        "order": 1,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "Duty Cycle",
        "label": "%",
        "format": "{{value}}",
        "min": 0,
        "max": "100",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "30",
        "seg2": "70",
        "x": 1530,
        "y": 661,
        "wires": []
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
        "x": 1260,
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
        "x": 1260,
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
        "x": 1260,
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
        "x": 1260,
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
        "x": 1260,
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
        "x": 920,
        "y": 600,
        "wires": []
    },
    {
        "id": "598712df.312fb4",
        "type": "change",
        "z": "721e71e2.b201b8",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload[0].DUTY_CYCLE",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1260,
        "y": 640,
        "wires": [
            [
                "934645d.5a566b8",
                "dee433fb.ab2e98"
            ]
        ]
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
        "x": 1260,
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
        "x": 1030,
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
        "func": "'use strict';\nfunction formatBytes(bytes, decimals) {\n  if(bytes === 0) return '0 Bytes';\n  var k = 1024,\n      dm = decimals || 2,\n      sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],\n      i = Math.floor(Math.log(bytes) / Math.log(k));\n  return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];\n}\n\nvar myArray = msg.payload;\nvar msg2 = {}, \n    msg3 = {};\n\n// Reformat values to human readable\nvar newArray = myArray.map(function(v) {\n  return {\n    filesystem: v.filesystem,\n    size: formatBytes(v.size * 1024),\n    used: formatBytes(v.used * 1024),\n    available: formatBytes(v.available * 1024),\n    usedPercent: (v.capacity * 100),\n    mount: v.mount\n  };\n});\nmsg2.payload = newArray;\n\n// Find '/usr/local'\nvar index = newArray.findIndex(x => x.mount ==='/usr/local');\nmsg3.payload = newArray[index].usedPerecent;\n\nreturn [msg2, msg3];",
        "outputs": 2,
        "noerr": 0,
        "x": 1250,
        "y": 540,
        "wires": [
            [
                "98458e0d.043298"
            ],
            [
                "27ac74b1.18397c"
            ]
        ]
    },
    {
        "id": "98458e0d.043298",
        "type": "ui_template",
        "z": "721e71e2.b201b8",
        "group": "86c746d.7ab5db8",
        "name": "Disk Free",
        "order": 3,
        "width": "8",
        "height": "12",
        "format": "<script>\n'use strict';\nfunction diskColor() {\n  $('#myTableDisk td.myUsage').each(function(){\n    if (parseInt($(this).text()) <= 75) {\n      $(this).css('background-color', '#00cc44');\n    } else if (parseInt($(this).text()) >= 76 && parseInt($(this).text()) <= 90) {\n      $(this).css('background-color', '#ff8c66');\n    } else if (parseInt($(this).text()) >= 91) {\n      $(this).css('background-color', '#ff6666');\n    }\n  });\n}\n\n(function(scope){\n  scope.$watch('msg', function(msg) {\n    if (msg != null) {\n      diskColor();\n    }\n  });\n}(scope));\n\nangular.element(document).ready(function() {\n  diskColor();\n});\n</script>\n\n<h3>Disk Free</h3>\n<table id=\"myTableDisk\" width=\"100%\" border=\"1\">\n  <tbody>\n    <tr>\n      <th scope=\"col\">Mount</th>\n      <th scope=\"col\">Size</th>\n      <th scope=\"col\">Used</th>\n      <th scope=\"col\">Free</th>\n      <th scope=\"col\">Use %</th>\n    </tr>\n    <tr ng-repeat=\"mount in msg.payload\">\n      <th align=\"left\" scope=\"row\">{{mount.mount}}</th>\n      <td align=\"right\">{{mount.size}}</td>\n      <td align=\"right\">{{mount.used}}</td>\n      <td align=\"right\">{{mount.available}}</td>\n      <td align=\"right\" class=\"myUsage\">{{mount.usedPercent}}</td>\n    </tr>\n  </tbody>\n</table>\n",
        "storeOutMessages": true,
        "fwdInMessages": false,
        "templateScope": "local",
        "x": 1520,
        "y": 520,
        "wires": [
            []
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
        "x": 1480,
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
        "x": 710,
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
        "x": 920,
        "y": 500,
        "wires": []
    },
    {
        "id": "d2c19fd4.fa69f",
        "type": "link out",
        "z": "721e71e2.b201b8",
        "name": "",
        "links": [
            "2905a362.32561c",
            "4c7acda3.e2b934",
            "ad902d7f.3b30a",
            "d9a7811a.8e557",
            "865a64c1.dde128",
            "700d0c79.9b3ba4",
            "d1b4ba2f.12b558",
            "aaaa5b37.2cd678",
            "c312f300.5a6f1"
        ],
        "x": 255,
        "y": 60,
        "wires": []
    },
    {
        "id": "2905a362.32561c",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "",
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
        "name": "",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 855,
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
        "name": "",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 855,
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
        "name": "",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 855,
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
        "name": "",
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
        "name": "",
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
        "name": "",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 855,
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
        "name": "",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 55,
        "y": 640,
        "wires": [
            [
                "5ab12bc9.a0b8b4"
            ]
        ]
    },
    {
        "id": "c312f300.5a6f1",
        "type": "link in",
        "z": "721e71e2.b201b8",
        "name": "",
        "links": [
            "d2c19fd4.fa69f"
        ],
        "x": 855,
        "y": 640,
        "wires": [
            [
                "84d9db66.3c127"
            ]
        ]
    },
    {
        "id": "5fd974a1.743d8c",
        "type": "ui_template",
        "z": "721e71e2.b201b8",
        "group": "4bbfb1c3.d86a",
        "name": "RSSI Table",
        "order": 3,
        "width": "6",
        "height": "8",
        "format": "<script>\n'use strict';\nfunction RSSIcolor() {\n  $('#myTable td.myDB').each(function(){\n    if (parseInt($(this).text()) >= -45) {\n      $(this).css('background-color', '#00cc44');\n    } else if (parseInt($(this).text()) <= -46 && parseInt($(this).text()) >= -85) {\n      $(this).css('background-color', '#66ff66');\n    } else if (parseInt($(this).text()) <= -86 && parseInt($(this).text()) >= -100) {\n      $(this).css('background-color', '#ff8c66');\n    } else if (parseInt($(this).text()) <= -101) {\n      $(this).css('background-color', '#ff6666');\n    }\n  });\n}\n\n(function(scope){\n  scope.$watch('msg', function(msg) {\n    if (msg != null) {\n      RSSIcolor();\n    }\n  });\n}(scope));\n\nangular.element(document).ready(function() {\n  RSSIcolor();\n});\n</script>\n\n<h3>RSSI Values</h3>\n<table id=\"myTable\" width=\"100%\" border=\"1\">\n  <tbody>\n    <tr>\n      <th scope=\"col\">&nbsp;</th>\n      <th colspan=\"2\" scope=\"col\">{{msg.ccu}}</th>\n    </tr>\n    <tr ng-repeat=\"(key, value) in msg.payload\" >\n      <th scope=\"row\">{{key}}</th>\n      <td class=\"myDB\" align=\"center\">{{value[0]}}</td>\n      <td class=\"myDB\" align=\"center\">{{value[1]}}</td>\n    </tr>\n  </tbody>\n</table>",
        "storeOutMessages": true,
        "fwdInMessages": true,
        "templateScope": "local",
        "x": 690,
        "y": 640,
        "wires": [
            []
        ]
    },
    {
        "id": "6719ae8b.ab2f18",
        "type": "ui_group",
        "z": "",
        "name": "CPU Load",
        "tab": "189e0ea3.dd5dd1",
        "order": 2,
        "disp": true,
        "width": "6"
    },
    {
        "id": "44fa2766.cd3658",
        "type": "ui_group",
        "z": "",
        "name": "Memory",
        "tab": "189e0ea3.dd5dd1",
        "order": 3,
        "disp": true,
        "width": "6"
    },
    {
        "id": "109dc147.190c8f",
        "type": "ui_group",
        "z": "",
        "name": "System Information",
        "tab": "189e0ea3.dd5dd1",
        "order": 1,
        "disp": true,
        "width": "6"
    },
    {
        "id": "38263145.35ea0e",
        "type": "ccu-connection",
        "z": "",
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
        "rpcInitAddress": "127.0.0.1",
        "rpcServerHost": "127.0.0.1",
        "rpcBinPort": "2047",
        "rpcXmlPort": "2048",
        "contextStore": "memory"
    },
    {
        "id": "4bbfb1c3.d86a",
        "type": "ui_group",
        "z": "",
        "name": "CCU",
        "tab": "189e0ea3.dd5dd1",
        "disp": true,
        "width": "6",
        "collapse": false
    },
    {
        "id": "86c746d.7ab5db8",
        "type": "ui_group",
        "z": "",
        "name": "Disk",
        "tab": "189e0ea3.dd5dd1",
        "disp": true,
        "width": "8",
        "collapse": false
    },
    {
        "id": "189e0ea3.dd5dd1",
        "type": "ui_tab",
        "z": "",
        "name": "System",
        "icon": "computer"
    }
]
