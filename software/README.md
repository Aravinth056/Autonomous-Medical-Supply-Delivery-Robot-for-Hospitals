# Software

The MediRoute robot uses an Arduino UNO to control the sensors, motors, LCD, and delivery operation.

## Software Used

- Arduino IDE
- Arduino Programming / Embedded C
- Arduino UNO (ATmega328P)

## Main Software Functions

- Reads the left and right IR sensors for line following
- Controls the left and right DC gear motors
- Detects obstacles using the HC-SR04 ultrasonic sensor
- Stops the robot when an obstacle is detected
- Displays robot status on the 16x2 LCD
- Uses a push button to start or stop the system
- Controls the robot using differential drive

## Control Flow

```text
IR Sensors
    ↓
Arduino UNO
    ↓
Line Following Decision
    ↓
Motor Driver (L298N)
    ↓
DC Gear Motors


## for obstacle detection

HC-SR04 Ultrasonic Sensor
          ↓
      Arduino UNO
          ↓
   Obstacle Detected?
       ↙         ↘
     YES          NO
      ↓            ↓
 Stop Motors    Continue
      ↓
LCD: "Obstacle! Wait"

