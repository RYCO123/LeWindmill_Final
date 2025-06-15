# Windmill Control Panel

<img width="550" alt="Screenshot 2025-06-15 at 2 20 07 PM" src="https://github.com/user-attachments/assets/bfc1179b-0b65-464d-88f0-27ea86f34111" />

## Overview
The **Windmill Control Panel** is a Python-based application for managing the operation of a motorized windmill and music box. It provides a graphical user interface (GUI) to adjust motor speed, change direction, and monitor real-time status using a Raspberry Pi. The application also supports a LCD display for visual feedback.

---

## Features
- **Motor Control**: Start, stop, and adjust the speed of the windmill and music box motors.
- **Direction Control**: Change the direction of motor rotation.
- **GUI**: User-friendly interface built with CustomTkinter.
- **LCD Support**: Display real-time motor statistics and status.
- **Raspberry Pi GPIO Integration**: Control hardware components directly.

---

## Prerequisites
Before installing and running the program, ensure the following:
- **Raspberry Pi**: A model with GPIO support (e.g., Raspberry Pi 4, 3B+).
- **Operating System**: Raspberry Pi OS (Debian-based).
- **Python Version**: Python 3.7 or higher.

---

## Required Hardware
1. **Stepper Motors** (e.g., NEMA17)
2. **DRV8833 Motor Drivers**
3. **LCD Display**
4. **Raspberry Pi GPIO Pins**
5. Power Supply and Cables

---

## System Schematic
The control panel software was developed as part of a larger hardware project. The complete electrical design was created in Multisim.

To clarify the scope of this repository, the schematic below has been annotated to highlight the two main functional blocks: the **control interface (Raspberry Pi)** and the **actuator/display circuit (motor and LCD)**. The un-highlighted components were part of the larger assembly and are not controlled by this software.

![Annotated schematic showing the Pi interface and Motor/Display circuits]<img width="798" alt="Screenshot 2025-06-15 at 2 39 54 PM" src="https://github.com/user-attachments/assets/2210a822-e4cc-4482-911c-7b3857c542d7" />


### Key Subsystems:

*   **Blue Highlight (Control Interface):**
    *   This section shows the **Raspberry Pi GPIO pins** that serve as the software's connection to the physical world.
    *   Digital signals from these pins (e.g., `GPIO17`, `GPIO27`) are used to command the motor driver.
    *   The `GPIO2_SDA` and `GPIO3_SCL` pins provide the I2C data and clock lines for the display.

*   **Green Highlight (Actuator & Display Circuit):**
    *   This section contains the "business end" of the project—the components that the software directly controls to perform an action.
    *   It includes the `Main_Stepper` motor, its driver ICs, and the `Digital_Display_Board`.
    *   *(Note: While the schematic specifies UCC27424D drivers, the physical build used a standard DRV8833 module. The control principle of driving the motor via GPIO signals is identical.)*

---

## Installation

### Step 1: Update Raspberry Pi
Update your Raspberry Pi’s package list and upgrade installed packages:
```bash
sudo apt-get update
sudo apt-get upgrade
```

### Step 2: Install Python and Pip
Ensure Python and pip are installed:
```bash
sudo apt-get install python python-pip
```

### Step 3: Enable I2C
Enable I2C communication on your Raspberry Pi:
```bash
sudo raspi-config
```
- Navigate to **Interfacing Options > I2C** and enable it.

Install I2C tools:
```bash
sudo apt-get install i2c-tools
```

### Step 4a: Clone the Repository
Clone the project repository to your Raspberry Pi:
```bash
git clone https://github.com/RYCO123/LeWindmill_Final.git
cd LeWindmill_Final
```

### OR ###

### Step 4b: Download Files Manually
- Install all files from https://github.com/RYCO123/LeWindmill_Final.git into a folder.
- Access folder in terminal:
```bash
cd C:/path/to/folder
```

### Step 5: Install Dependencies
Install the required Python libraries:
```bash
pip install -r requirements.txt
```

---

## Usage

### Step 1: Connect Hardware
1. Wire the stepper motors, DRV8833 drivers, and LCD display to the Raspberry Pi GPIO pins as specified in your hardware documentation.
2. Ensure all connections are secure.

### Step 2: Run the Application
Start the program by running:
```bash
python LeWindmill.py
```

### Step 3: Use the Control Panel
- Adjust the **Dunk Rate** slider to set the motor speed.
- Click **Start** to activate the windmill and music box.
- Use **Pause** and **Stop** buttons to control the motor activity.
- Monitor motor status and speed on the GUI and LCD display.

---

## File Structure
```
windmill-control/
|-- LeWindmill.py          # Main program script
|-- lakers-theme.json      # Theme configuration for the GUI
|-- lebron.png             # Icon for the application
|-- requirements.txt       # List of required Python libraries
```

---

## Troubleshooting

### Common Issues
1. **I2C LCD Not Detected**:
   - Run `sudo i2cdetect -y 1` to check for the LCD address.
   - Ensure the correct address is configured in the code.

2. **GPIO Permission Denied**:
   - Run the program with elevated privileges:
     ```bash
     sudo python LeWindmill.py
     ```

3. **Missing Dependencies**:
   - Ensure all required libraries are installed using:
     ```bash
     pip3 install -r requirements.txt
     ```

4. **Motor Not Spinning**:
   - Check the wiring and power supply.
   - Verify that the GPIO pins are correctly configured in the code.
  
5. **LCD Display Showing Error**:
   - Check the wiring and power supply.
   - Verify that the GPIO pins are correctly configured in the code.
   - After checking wiring and power to LCD display, restart LeWindmill.py if error is there.
---

## Credits
Developed by **Nelson C., Ryan C., and Ethan S.** as a control panel for the Lebron Windmill.

---

## Contact
For questions or support, reach out at [rhcody@wm.edu].

