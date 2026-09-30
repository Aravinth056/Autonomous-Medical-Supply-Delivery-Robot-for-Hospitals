
# Hardware Components

## 1. Arduino UNO

**Quantity:** 1

The Arduino UNO based on the ATmega328P acts as the main controller.

It receives sensor inputs, processes navigation logic, controls the motor driver and updates the LCD display.

### Main role

* Sensor processing
* Navigation control
* Motor control
* Obstacle response
* LCD status control

---

## 2. IR Sensor Modules

**Quantity:** 2

The two IR sensors are mounted at the front underside of the robot.

They detect the marked path and provide left/right position information to the Arduino.

The difference between the left and right sensor states is used for steering correction.

---

## 3. HC-SR04 Ultrasonic Sensor

**Quantity:** 1

The ultrasonic sensor is mounted at the front of the robot.

It measures the distance between the robot and an obstacle.

The prototype uses a preset safety threshold of approximately 15 cm.

When an obstacle enters the safety zone, the robot stops.

---

## 4. L298N Motor Driver

**Quantity:** 1

The L298N dual H-bridge motor driver interfaces the Arduino with the two DC gear motors.

It allows independent control of:

* Left motor
* Right motor
* Motor direction
* Motor speed through PWM

---

## 5. DC Gear Motors

**Quantity:** 2

Two 12 V DC gear motors provide the driving force.

The gear reduction increases available torque while maintaining controlled movement.

Independent motor control enables differential steering.

---

## 6. Li-ion Battery

**Quantity:** 1

A 7.4 V rechargeable Li-ion battery pack provides power to the robot.

The battery supplies:

* Motor driver
* Motors
* Voltage regulator

---

## 7. 7805 Voltage Regulator

The 7805 regulator provides a regulated 5 V supply for the low-voltage electronics.

The report describes a separate power path for the motor system and control electronics.

---

## 8. 16×2 LCD Display

The LCD provides local operating information.

Example messages described in the project include:

```text
System Ready
Delivering
Obstacle! Wait
Delivery Complete
```

---

## 9. Push Button

The push button provides simple local start/stop control.

It allows the robot to switch between the waiting and delivery states.

---

## 10. Medical Storage Compartment

The compartment carries the medical payload during transportation.

The prototype uses a simple open-top structure.

A future version could use a lockable and sanitizable enclosure.

---

## 11. Chassis

The chassis is a lightweight two-tier structure fabricated using cardboard reinforced with acrylic sheet.

The lower level contains the drive system and battery.

The upper level contains electronics and the medical storage compartment.
