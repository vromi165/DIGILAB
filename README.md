# DIGILAB - Node-RED LCD Clock

This project demonstrates a **digital clock** displayed on a character-based **I2C LCD** connected to a Raspberry Pi, using **Node-RED** to automate updates. The clock updates every minute.

---

## Features

- Displays current time in `HH:MM` format
- Updates automatically every minute
- Uses Node-RED for automation and Python scripts for LCD control
- Modular and easy to extend for other applications

---

## Node-RED Flow

The flow triggers every minute, formats the current time as `HH:MM`, and sends it to the LCD.

**Flow JSON:** You can download and import the Node-RED flow from:

[clock_flow.json](./clock_flow.json)

> ⚠️ Make sure your Python scripts are located in `/home/admin/lcd/` and are executable.

---

## Hardware Requirements

- Raspberry Pi with GPIO pins  
- I2C Character LCD (16x2 or 20x4) with PCF8574 backpack  
- Jumper wires to connect LCD to Pi  

---


## License

This project is licensed under the **MIT License**. See [LICENSE](https://github.com/vromi165/DIGILAB/blob/main/LICENSE) for details.

---

## Project Planning

View the project planning and progress here: [DIGILAB Project Board](https://github.com/users/vromi165/projects/2)

---

## Contact

Created by [vromi165](https://github.com/vromi165)
