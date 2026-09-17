# Software

## 📌 Software Overview

The software system controls the autonomous operation of the MEDIROUTE medical supply delivery robot.

The Arduino UNO is used as the main controller. The program receives inputs from the sensors and destination-selection buttons, processes the navigation logic, and controls the motors and LCD display.

The software is designed to perform path following, obstacle detection, destination-based navigation, stopping, and return-to-home operation.

---

## 💻 Software Used

| Software / Platform | Purpose |
|---------------------|---------|
| Arduino IDE | Program development and uploading |
| Embedded C / Arduino Programming | Robot control logic |
| Arduino UNO | Main controller |
| I2C LCD Library | LCD display control |
| Motor Control Logic | DC motor movement |
| Sensor Input Logic | Path and obstacle detection |

---

## 🧠 Main Software Functions

The robot software performs the following functions:

- System initialization
- Destination selection
- Path detection
- Path following
- Obstacle detection
- Motor control
- Turning control
- Destination detection
- Robot stopping
- Return-to-home operation
- LCD status indication

---

## 🔄 Software Flow

```text
START
  ↓
Initialize Arduino
  ↓
Initialize Sensors
  ↓
Initialize Motors
  ↓
Initialize LCD
  ↓
Read Destination
  ↓
Select Zone
  ↓
Start Navigation
  ↓
Read Sensors
  ↓
Check Obstacle
  ↓
Obstacle Detected?
 ┌───────────────┴───────────────┐
 YES                             NO
 ↓                                ↓
Stop Motors                 Follow Path
 ↓                                ↓
Wait for Obstacle           Check Destination
Clear                             ↓
 ↓                         Destination Reached?
Resume Navigation            ┌────┴────┐
                             YES       NO
                              ↓         ↓
                            STOP     Continue
                              ↓
                         Delivery Complete
                              ↓
                           Return Home
                              ↓
                             STOP
