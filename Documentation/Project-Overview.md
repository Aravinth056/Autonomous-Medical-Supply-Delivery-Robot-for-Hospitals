# MediRoute — Project Overview

## 1. Introduction

MediRoute is an autonomous medical supply delivery robot developed for hospital indoor logistics.

The project addresses the repetitive transportation of medicines, consumables and other lightweight medical supplies between hospital departments.

The prototype was developed as a low-cost autonomous mobile robot capable of following a predefined corridor route, detecting obstacles and carrying a small medical payload.

---

## 2. Problem Statement

Hospitals require frequent movement of medical supplies between pharmacies, stores, nursing stations and wards.

Manual transportation requires nurses and support staff to repeatedly travel between departments. This increases workload and consumes time that could otherwise be used for patient-care activities.

The proposed robot provides an autonomous alternative for fixed-route transportation of lightweight medical supplies.

---

## 3. Objectives

The main objectives are:

1. Design and fabricate a low-cost autonomous mobile robot.
2. Implement line-following navigation using IR sensors.
3. Implement obstacle detection using an ultrasonic sensor.
4. Provide a dedicated medical supply storage compartment.
5. Provide LCD-based operating status.
6. Provide simple push-button operation.
7. Evaluate navigation accuracy.
8. Evaluate obstacle response.
9. Evaluate payload carrying capability.
10. Evaluate battery performance.

---

## 4. Scope

The project covers:

* Mechanical robot design
* Chassis fabrication
* Embedded hardware selection
* Circuit design
* Sensor integration
* Motor control
* Line-following navigation
* Obstacle detection
* Medical payload transportation
* CAD modelling
* Prototype testing
* Hospital dispatch website concept

The prototype was tested on a simulated hospital corridor.

The project does not cover:

* Full clinical deployment
* Hospital certification
* Regulatory approval
* Complete hospital information-system integration
* Full SLAM-based navigation
* Real-world hospital deployment

---

## 5. Proposed System

The robot consists of:

* Arduino UNO controller
* Two IR sensors
* HC-SR04 ultrasonic sensor
* L298N motor driver
* Two DC gear motors
* 7.4 V Li-ion battery
* 7805 voltage regulator
* 16×2 LCD
* Push button
* Two-tier chassis
* Medical storage compartment

---

## 6. Basic Operation

The robot first initializes the control system.

After activation, it continuously checks the ultrasonic sensor for obstacles.

If the path is clear, the IR sensors determine the robot's position relative to the marked line.

The Arduino adjusts the left and right motor speeds to maintain the robot on the predefined path.

If an obstacle is detected within the programmed safety distance, both motors are stopped.

After the obstacle is removed, normal navigation resumes.

---

## 7. Prototype Testing

The prototype was evaluated through:

* Obstacle detection testing
* Line-following testing
* Turning and stopping testing
* Payload testing
* Battery performance testing

The reported navigation tests used a 3 m path, while payload tests showed stable operation up to approximately 400 g.

---

## 8. Expected Application

The concept is intended for routine indoor transportation of lightweight materials such as:

* Medicines
* Medical supplies
* Laboratory samples
* Documents
* Dressing materials

---

## 9. Future Development

Future development identified in the project includes:

* IoT monitoring
* RFID destination identification
* Camera-based navigation
* SLAM
* Indoor mapping
* Hospital information-system integration
* Secure medical storage

