# DIGILAB - Node-RED LCD Clock

This project demonstrates a **digital clock** displayed on a character-based **I2C LCD** connected to a Raspberry Pi, using **Node-RED** to automate updates. The clock updates every minute and can be extended for additional features like date, weather, or custom messages.

---

## Features

- Displays current time in `HH:MM` format
- Updates automatically every minute
- Uses Node-RED for automation and Python scripts for LCD control
- Modular and easy to extend for other applications

---

## Node-RED Flow

The flow triggers every minute, formats the current time as `HH:MM`, and sends it to the LCD using the Python script `write.py`.

**Flow JSON:** You can download and import the Node-RED flow from:

[clock_flow.json](./clock_flow.json)

> ⚠️ Make sure your Python scripts are located in `/home/admin/lcd/` and are executable.

---

## Hardware Requirements

- Raspberry Pi with GPIO pins  
- I2C Character LCD (16x2 or 20x4) with PCF8574 backpack  
- Jumper wires to connect LCD to Pi  

**Connections:**

| LCD Pin | Raspberry Pi Pin |
|---------|----------------|
| SDA     | GPIO 2          |
| SCL     | GPIO 3          |
| VCC     | 5V              |
| GND     | GND             |

---

## Software Requirements

- Raspberry Pi OS (or compatible Linux)  
- Python 3  
- `python3-smbus` library  
- Node-RED installed on Raspberry Pi  
- I2C enabled via `raspi-config`

---

## Python Scripts

Place these scripts in `/home/admin/lcd/`:

- `base.py` – handles low-level LCD communication  
- `init.py` – initializes and clears the LCD  
- `write.py` – writes text to a specific line  
- `backlight.py` – controls the backlight  
- `cursor.py` – controls cursor visibility, blink, and display  

---

## Usage

1. Connect your LCD and enable I2C on the Raspberry Pi.  
2. Place Python scripts in `/home/admin/lcd/`.  
3. Import the Node-RED flow (`clock_flow.json`).  
4. Deploy the flow — the LCD will display the current time, updating every minute.  
5. Optional: extend the flow to show seconds, date, or other dynamic content.

---

## License

This project is licensed under the **MIT License**. See [LICENSE](https://github.com/vromi165/DIGILAB/blob/main/LICENSE) for details.

---

## Project Planning

View the project planning and progress here: [DIGILAB Project Board](https://github.com/users/vromi165/projects/2)

---

## Contributing

Feel free to fork the repository, improve the flow or scripts, and submit pull requests.

---

## Contact

Created by [vromi165](https://github.com/vromi165)
