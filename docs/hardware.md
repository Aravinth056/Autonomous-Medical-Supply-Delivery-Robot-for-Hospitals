# Hardware Components

## 📌 Hardware Overview

The MEDIROUTE prototype consists of a microcontroller, sensors, motor driver, DC geared motors, battery, display, switches, chassis and a medical supply storage compartment.

The hardware system is responsible for destination selection, path detection, obstacle detection, motor control, status indication and movement of the robot.

---

## 🧩 Components List

| No. | Component | Quantity | Main Function |
|-----|-----------|----------|---------------|
| 1 | Arduino UNO | 1 | Main controller |
| 2 | IR Sensor - Path Detection | 1 | Detects the predefined path |
| 3 | IR Sensor - Obstacle Detection | 1 | Detects obstacles |
| 4 | DC Geared Motor | 2 | Drives the robot |
| 5 | Motor Driver Module | 1 | Controls motor speed and direction |
| 6 | I2C LCD Display 16×2 | 1 | Displays robot status |
| 7 | Zone Selection Push Buttons | 7 | Selects destination zones |
| 8 | Rechargeable Battery | 1 | Supplies electrical power |
| 9 | Robot Chassis | 1 | Supports the complete system |
| 10 | Wheels | 2 | Provides movement |
| 11 | Medical Supply Storage Compartment | 1 | Carries medical supplies |

---

## 1. Arduino UNO

The Arduino UNO is the main controller of the robot.

It processes the sensor inputs and controls the motors, LCD display and navigation system.

### Specification

- Microcontroller: ATmega328P
- Operating Voltage: 5 V
- Digital I/O Pins: 14
- Analog Input Pins: 6

### Function

- Reads sensor inputs
- Processes navigation logic
- Controls the motor driver
- Controls the LCD display
- Reads zone selection switches
- Controls the overall robot operation

---

## 2. IR Sensor - Path Detection

The path-detection IR sensor is used to detect the predefined path marked on the test track.

The sensor continuously detects the path and helps the robot follow the required route.

### Function

- Detects the marked path
- Helps maintain the robot on the route
- Detects path positions
- Supports destination navigation

---

## 3. IR Sensor - Obstacle Detection

A separate IR sensor is used for obstacle detection.

When an obstacle is detected, the Arduino sends a command to stop the motors.

### Function

- Detects obstacles in the robot's path
- Sends obstacle information to Arduino UNO
- Stops the robot when an obstacle is detected
- Allows the robot to resume movement after the obstacle is removed

---

## 4. DC Geared Motors

Two DC geared motors are used to drive the robot.

One motor is used for the left side and the other motor is used for the right side.

The motors provide the required movement for:

- Forward movement
- Reverse movement
- Left turning
- Right turning
- Stopping

The differential-drive arrangement allows the robot to control the left and right wheels independently.

### Specification

- Type: DC geared motor
- Operating Voltage: 12 V
- Quantity: 2

---

## 5. Motor Driver Module

The motor driver is used to interface the Arduino UNO with the DC motors.

It receives control signals from the Arduino and controls the direction and speed of the motors.

### Function

- Controls motor direction
- Controls motor speed
- Drives both DC motors
- Provides independent left and right motor control

---

## 6. I2C LCD Display

A 16×2 I2C LCD display is used to provide information about the robot's operating condition.

### Display Information

The LCD can display:

- Project title
- Initialization status
- Selected zone
- Path column
- Obstacle warning
- Robot stopped status
- Zone reached status
- Speed information

### Specification

- Display: 16×2 LCD
- Interface: I2C
- Operating Voltage: 5 V

---

## 7. Zone Selection Push Buttons

Seven push buttons are used for destination selection.

The inputs represent:

- Zone 1
- Zone 2
- Zone 3
- Zone 4
- Zone 5
- Zone 6
- Home

The selected zone is processed by the Arduino UNO and the robot follows the corresponding navigation sequence.

---

## 8. Rechargeable Battery

A rechargeable battery provides electrical power to the robot.

The battery supplies power to the motors and electronic control system.

### Function

- Powers the DC motors
- Powers the Arduino UNO
- Powers the sensors
- Powers the LCD display
- Provides portable operation

The project report specifies a 7.4 V Li-ion battery pack for the prototype power supply.

---

## 9. Robot Chassis

The chassis forms the main mechanical structure of the robot.

It supports:

- Motors
- Wheels
- Battery
- Arduino UNO
- Sensors
- Motor driver
- LCD display
- Push buttons
- Medical supply compartment

The prototype uses a lightweight two-tier structure.

### Lower Tier

Contains:

- Drive motors
- Wheels
- Battery

### Upper Tier

Contains:

- Arduino UNO
- Electronic components
- LCD display
- Medical supply compartment

---

## 10. Wheels

The robot uses rubber wheels for movement.

The wheels are connected to the DC geared motors and provide traction on the test surface.

### Function

- Provides robot movement
- Supports differential steering
- Provides traction on the predefined path

---

## 11. Medical Supply Storage Compartment

A dedicated storage compartment is provided on the robot to carry lightweight medical supplies.

It is designed to carry items such as:

- Medicine trays
- Dressing kits
- Sample containers
- Other small medical supplies

The current prototype uses a simple compartment for payload testing.

For actual hospital deployment, the compartment would need to be upgraded to a secure, lockable and sanitizable enclosure.

---

# ⚡ Power System

The prototype uses a 7.4 V rechargeable Li-ion battery.

The power system provides electrical energy to the robot's motors and control electronics.

Basic power flow:

```text
Rechargeable Battery
        │
        ├──────────────→ Motor Driver
        │                    │
        │                    └──→ DC Motors
        │
        └──→ Voltage Regulation
                     │
                     └──→ Arduino UNO
                              │
                              ├──→ IR Sensors
                              ├──→ LCD
                              └──→ Zone Selection Buttons
