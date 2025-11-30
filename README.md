[Digilab_vromi165.json](https://github.com/user-attachments/files/23839635/Digilab_vromi165.json)# DIGILAB - Node-RED LCD Clock

This project demonstrates a **digital clock** displayed on a character-based **I2C LCD** connected to a Raspberry Pi, using **Node-RED** to automate updates. The clock updates every minute and can be extended for additional features like date, weather, or custom messages.

---

## Features

- Displays current time in `HH:MM` format
- Updates automatically every minute
- Uses Node-RED for automation and Python scripts for LCD control
- Modular and easy to extend for other applications

---

## Node-RED Flow Overview

The Node-RED flow handles:

1. **Inject Node:** Triggers every minute to update the clock.
2. **Function Node:** Formats the current time into `HH:MM`.
3. **Exec Node:** Calls the Python script (`write.py`) to write the time to the LCD.
4. **Debug Nodes:** Monitor `stdout` and `stderr` for troubleshooting.

**Node red flow:**

[Uploadi[
    {
        "id": "5b0441296d355d95",
        "type": "tab",
        "label": "Clock digilab",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "inject_clock",
        "type": "inject",
        "z": "5b0441296d355d95",
        "name": "Trigger Every Minute",
        "props": [
            {
                "p": "payload"
            }
        ],
        "repeat": "60",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "payload": "",
        "payloadType": "date",
        "x": 300,
        "y": 360,
        "wires": [
            [
                "function_format_time"
            ]
        ]
    },
    {
        "id": "function_format_time",
        "type": "function",
        "z": "5b0441296d355d95",
        "name": "Format Time",
        "func": "var date = new Date();\nvar hours = date.getHours();\nvar minutes = date.getMinutes();\nif(hours < 10) { hours = '0' + hours; }\nif(minutes < 10) { minutes = '0' + minutes; }\nmsg.payload = hours + ':' + minutes;\nreturn msg;",
        "outputs": 1,
        "timeout": "",
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 520,
        "y": 360,
        "wires": [
            [
                "exec_lcd"
            ]
        ]
    },
    {
        "id": "exec_lcd",
        "type": "exec",
        "z": "5b0441296d355d95",
        "command": "/usr/bin/python3 /home/admin/lcd/write.py --line 1 --message",
        "addpay": "payload",
        "append": "",
        "useSpawn": "false",
        "timer": "",
        "winHide": false,
        "name": "Write to LCD",
        "x": 750,
        "y": 360,
        "wires": [
            [
                "debug_stdout"
            ],
            [
                "debug_stderr"
            ],
            []
        ]
    },
    {
        "id": "debug_stdout",
        "type": "debug",
        "z": "5b0441296d355d95",
        "name": "stdout",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "x": 980,
        "y": 320,
        "wires": []
    },
    {
        "id": "debug_stderr",
        "type": "debug",
        "z": "5b0441296d355d95",
        "name": "stderr",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "x": 980,
        "y": 360,
        "wires": []
    }
]ng Digilab_vromi165.json…]()

