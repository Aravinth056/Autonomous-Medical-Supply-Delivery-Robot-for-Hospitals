# 🤖 MediRoute — Autonomous Medical Supply Delivery Robot for Hospitals

> **A low-cost autonomous mobile robot for transporting medical supplies through predefined hospital corridor routes.**

![Project Type](https://img.shields.io/badge/Project-Mechanical%20Engineering-blue)
![Robot](https://img.shields.io/badge/Robot-Autonomous%20Mobile%20Robot-green)
![Controller](https://img.shields.io/badge/Controller-Arduino%20UNO-orange)
![Navigation](https://img.shields.io/badge/Navigation-IR%20Line%20Following-yellow)
![Obstacle Detection](https://img.shields.io/badge/Obstacle%20Detection-HC--SR04-red)
![Status](https://img.shields.io/badge/Status-Prototype%20Validated-success)

---

## 📌 Project Overview

**MediRoute** is an autonomous medical supply delivery robot designed to transport medicines and other lightweight medical supplies between designated locations inside a hospital.

The project was developed as a **scaled prototype** to demonstrate autonomous movement, line-following navigation, obstacle detection, payload transportation, and hospital dispatch workflow.

The robot follows a predefined corridor path using infrared sensors. An Arduino UNO processes sensor information and controls the two DC gear motors through an L298N motor driver. An ultrasonic sensor is used to detect obstacles in front of the robot and stop the robot when an obstacle enters the preset safety distance.

A dedicated storage compartment is provided on the robot chassis to carry medical supplies during transportation.

---

## 🎯 Problem Statement

Hospitals require continuous movement of medicines, consumables, laboratory samples, and other small medical supplies between departments.

This work is commonly performed manually by nurses and support staff. Repeated transportation increases staff workload and consumes time that could otherwise be used for patient-care activities.

The project therefore explores a low-cost autonomous system capable of transporting lightweight medical supplies along a fixed hospital corridor route while detecting obstacles and stopping safely.

---

## 💡 Proposed Solution

MediRoute combines:

* Autonomous line-following navigation
* Infrared path detection
* Ultrasonic obstacle detection
* Differential-drive movement
* Arduino UNO control
* DC geared motors
* Dedicated medical-supply storage
* LCD-based status indication
* Push-button operation
* Hospital dispatch workflow concept

The prototype was tested on a simulated hospital corridor track using marked paths and deliberately placed obstacles.

---

## ⭐ Key Features

* 🤖 Autonomous corridor navigation
* 🛣️ IR-based line following
* 🚧 Ultrasonic obstacle detection
* 🛑 Automatic obstacle stopping
* ⚙️ Differential-drive mechanism
* 📦 Medical supply storage compartment
* 📺 16×2 LCD status display
* 🔘 Push-button start/stop control
* 🔋 Rechargeable Li-ion battery operation
* 🧪 Experimental performance testing
* 🌐 MediRoute hospital dispatch website concept
* 🧩 CAD-based robot design
* 💰 Low-cost prototype fabrication

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │   Hospital Staff     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ MediRoute Website    │
                    │ Dispatch Interface   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Dispatch / Control   │
                    │ System               │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Arduino UNO       │
                    │ Robot Controller     │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
       ┌────────────┐   ┌────────────┐   ┌────────────┐
       │ IR Sensors │   │ Ultrasonic │   │ Push       │
       │ Path Track │   │ HC-SR04    │   │ Button     │
       └─────┬──────┘   └─────┬──────┘   └─────┬──────┘
             │                │                │
             └────────────────┼────────────────┘
                              ▼
                    ┌──────────────────────┐
                    │   Control Logic      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   L298N Motor Driver │
                    └──────────┬───────────┘
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
             ┌────────────┐        ┌────────────┐
             │ Left Motor │        │ Right Motor│
             └────────────┘        └────────────┘
                               │
                               ▼
                    🚑 Medical Supply
                       Transportation
```

---

# 🔧 Hardware Components

| No. | Component                        | Quantity | Function               |
| --: | -------------------------------- | -------: | ---------------------- |
|   1 | Arduino UNO (ATmega328P)         |        1 | Main controller        |
|   2 | IR Sensor Module                 |        2 | Line/path detection    |
|   3 | HC-SR04 Ultrasonic Sensor        |        1 | Obstacle detection     |
|   4 | L298N Dual H-Bridge Motor Driver |        1 | Motor control          |
|   5 | 12 V DC Gear Motor with Wheels   |        2 | Robot movement         |
|   6 | 7.4 V Li-ion Battery Pack        |        1 | Power supply           |
|   7 | 7805 Voltage Regulator           |        1 | 5 V regulation         |
|   8 | 16×2 LCD Display                 |        1 | Status indication      |
|   9 | Push Button                      |        1 | Start/stop control     |
|  10 | Cardboard/Acrylic Chassis        |    1 set | Robot structure        |
|  11 | Jumper Wires & Connectors        |    1 set | Electrical connections |

The component list and quantities are based on the project report.

---

# ⚙️ Working Principle

The robot operates using a closed-loop sensing and control process.

### Step 1 — System Initialization

The Arduino UNO initializes:

* IR sensors
* Ultrasonic sensor
* LCD
* Push button
* Motor driver
* Motor control outputs

The LCD displays the system status.

### Step 2 — Path Detection

Two IR sensors are mounted near the front underside of the robot.

The sensors detect the marked path on the test track.

The Arduino compares the left and right sensor readings to determine whether the robot is centered on the path.

### Step 3 — Line Following

If the robot moves away from the center of the path, the motor speeds are corrected independently.

The project report expresses the line-position error as:

```text
e = SL - SR
```

where:

* `SL` = left IR sensor status
* `SR` = right IR sensor status

The corrected motor commands are represented as:

```text
VL = Vbase - Kp × e

VR = Vbase + Kp × e
```

where:

* `VL` = left motor command
* `VR` = right motor command
* `Vbase` = nominal forward speed
* `Kp` = experimentally determined proportional gain

### Step 4 — Obstacle Detection

Before normal steering correction is applied, the ultrasonic sensor checks the path ahead.

The prototype uses a preset safety distance of approximately:

```text
15 cm
```

If an obstacle is detected within this distance:

```text
Both motors → STOP
LCD → "Obstacle! Wait"
```

When the obstacle is removed, normal navigation resumes.

### Step 5 — Delivery

The robot continues along the predefined route while carrying the medical supply payload inside the storage compartment.

### Step 6 — Completion

At the designated delivery point, the robot stops and the delivery status can be updated through the proposed MediRoute workflow.

---

# 🧠 Control Logic

```text
START
   │
   ▼
Initialize Arduino and Sensors
   │
   ▼
Initialize LCD and Motors
   │
   ▼
Wait for Start Command
   │
   ▼
Read Ultrasonic Sensor
   │
   ├── Obstacle Detected?
   │          │
   │          ├── YES → Stop Motors
   │          │          Display "Obstacle! Wait"
   │          │          Wait
   │          │
   │          └── NO
   │
   ▼
Read Left and Right IR Sensors
   │
   ▼
Calculate Line Position Error
   │
   ▼
Correct Left / Right Motor Speed
   │
   ▼
Follow Predefined Path
   │
   ▼
Destination Reached?
   │
   ├── NO → Continue Navigation
   │
   └── YES
          │
          ▼
       Stop Robot
          │
          ▼
     Delivery Complete
```

---

# 🛞 Mechanical Design

The robot uses a lightweight **two-tier chassis structure**.

### Lower Tier

The lower section contains:

* DC gear motors
* Wheels
* Battery pack

The lower placement helps maintain a comparatively low centre of gravity.

### Upper Tier

The upper section contains:

* Arduino UNO
* Motor driver
* Sensor/control electronics
* LCD display
* Medical storage compartment

### Differential Drive

Two DC gear motors independently drive the left and right wheels.

Different motor speeds are used for steering corrections during line following.

---

# 📦 Medical Storage Compartment

A dedicated compartment is provided on the upper portion of the chassis.

It is intended for lightweight medical supplies such as:

* Medicine trays
* Dressing kits
* Small sample containers
* Other lightweight hospital materials

The current prototype uses a simple open-top compartment for experimental validation.

For future hospital deployment, the report proposes upgrading this compartment to a:

* Lockable enclosure
* Sanitizable enclosure
* More secure medical-storage system

---

# 🔌 Arduino UNO Pin Configuration

| Arduino Pin | Function                        |
| ----------- | ------------------------------- |
| D2          | Left IR sensor                  |
| D3          | Right IR sensor                 |
| D4          | Ultrasonic TRIG                 |
| D5          | Ultrasonic ECHO                 |
| D6          | Motor driver ENA / PWM          |
| D7          | Motor driver ENB / PWM          |
| D8–D11      | Motor direction control         |
| D12         | Push button                     |
| A0–A5       | LCD/control lines as documented |

---

# 🔋 Power Supply

The prototype uses a:

**7.4 V rechargeable Li-ion battery pack**

Power is divided into two main paths:

```text
7.4 V Li-ion Battery
        │
        ├──────────────► L298N Motor Driver
        │                    │
        │                    ├──► Left Motor
        │                    └──► Right Motor
        │
        └──► 7805 Regulator
                     │
                     ▼
                    5 V
                     │
             ┌───────┼────────┐
             ▼       ▼        ▼
          Arduino   IR      LCD
                     │
                 Ultrasonic
```

---

# 🌐 MediRoute Hospital Dispatch Website

The project also includes a proposed hospital dispatch website concept.

The website provides an interface for hospital staff to manage medical supply delivery requests.

## Main Workflow

```text
User Login
     ↓
Select Medical Supply
     ↓
Select Destination
     ↓
Confirm Request
     ↓
Robot Dispatch
     ↓
Delivery
     ↓
Status Update
```

## Website Modules

### 1. User Login

Authorized hospital staff can log in to the system before creating delivery requests.

### 2. Medication Room / Dispatch

Staff can select the required medical supply and create a delivery request.

### 3. ICU and Ward Selection

The system provides destination options such as:

* ICU
* General wards
* Nursing stations

### 4. OP / Emergency / OT

The system can provide separate destination modules for:

* Out-Patient Department
* Emergency
* Operation Theatre

### 5. Dispatch Status

Typical delivery states include:

```text
Requested
    ↓
Dispatched
    ↓
In Transit
    ↓
Delivered
```

---

# 🔗 Website–Robot Integration

The proposed system connects the software dispatch interface with the physical robot.

```text
Hospital Staff
      ↓
MediRoute Website
      ↓
Dispatch / Control System
      ↓
Robot Controller
      ↓
Sensors + Motors
      ↓
Medical Supply Delivery
```

The website represents the user-facing dispatch layer, while the robot performs physical transportation and autonomous navigation.

---

# 🧪 Prototype Development

## Chassis Fabrication

The prototype chassis was fabricated using lightweight cardboard reinforced with acrylic sheet.

The structure was assembled as a two-tier platform.

The lower tier supports the motors, wheels and battery.

The upper tier supports the electronics and medical storage compartment.

## Hardware Assembly

The following components were mounted:

* Arduino UNO
* L298N motor driver
* Voltage regulator
* Battery
* LCD
* Sensors
* Motors

Wiring was routed along the chassis to avoid interference with the wheels and moving parts.

## Sensor Installation

The IR sensors were installed symmetrically near the front underside of the robot.

The ultrasonic sensor was installed at the front of the upper chassis and directed forward.

---

# 💻 Software / Control

The robot control system is based on the Arduino UNO.

The control logic handles:

* Sensor initialization
* IR line detection
* Ultrasonic obstacle detection
* Motor control
* Differential steering
* LCD status display
* Start/stop operation

### Main Logic

```text
Sensor Input
     ↓
Arduino UNO
     ↓
Decision Making
     ↓
Motor Driver
     ↓
Left / Right Motor Control
```

---

# 🧪 Experimental Testing

The completed prototype was tested on a simulated hospital corridor track.

The test track used marked paths to represent a hospital corridor.

Testing covered:

1. Obstacle detection
2. Navigation accuracy
3. Turning and stopping
4. Payload carrying
5. Battery performance

---

# 🚧 Obstacle Detection Test

The ultrasonic obstacle detection system was tested using obstacles placed at different distances.

| Trial | Obstacle Position (cm) | Robot Stop Position (cm) | Result |
| ----: | ---------------------: | -----------------------: | ------ |
|     1 |                     30 |                     16.2 | Pass   |
|     2 |                     25 |                     15.8 | Pass   |
|     3 |                     20 |                     14.9 | Pass   |
|     4 |                     35 |                     16.5 | Pass   |
|     5 |                     15 |                     14.5 | Pass   |

The robot stopped before contacting the obstacle in all reported trials.

---

# 🛣️ Navigation Test

Eight trials were conducted over a fixed **3 metre** section of the test path.

| Trial | Distance (m) | Time (s) | Average Deviation (cm) |
| ----: | -----------: | -------: | ---------------------: |
|     1 |          3.0 |     14.2 |                    1.8 |
|     2 |          3.0 |     13.9 |                    1.6 |
|     3 |          3.0 |     14.5 |                    2.1 |
|     4 |          3.0 |     14.1 |                    1.7 |
|     5 |          3.0 |     13.8 |                    1.5 |
|     6 |          3.0 |     14.3 |                    1.9 |
|     7 |          3.0 |     14.6 |                    2.2 |
|     8 |          3.0 |     14.0 |                    1.6 |

The reported trials show approximately **14 seconds average travel time** over 3 metres, with lateral deviation remaining at or below 2.2 cm.

---

# ↪️ Turning and Stopping Test

| Trial | Junction Negotiated Correctly | Stopping Overshoot (cm) |
| ----: | ----------------------------- | ----------------------: |
|     1 | Yes                           |                     2.1 |
|     2 | Yes                           |                     1.8 |
|     3 | Yes                           |                     2.4 |
|     4 | Yes                           |                     1.6 |

The prototype successfully negotiated the tested junction and stopped close to the marked endpoint in the reported trials.

---

# 📦 Payload Test

Payload tests were performed by progressively increasing the load inside the medical storage compartment.

| Payload | Navigation Stability | Observation                                               |
| ------: | -------------------- | --------------------------------------------------------- |
|   100 g | Stable               | No noticeable change in speed or path tracking            |
|   200 g | Stable               | No noticeable change in speed or path tracking            |
|   300 g | Stable               | Slight reduction in acceleration                          |
|   400 g | Stable               | Noticeable but acceptable reduction in speed              |
|   500 g | Unstable             | Wheel slip observed on turns and increased path deviation |

The prototype maintained stable navigation up to approximately **400 g** in the reported tests.

---

# 🔋 Battery Performance

Battery voltage was monitored during a continuous operating test.

|   Time | Battery Voltage |
| -----: | --------------: |
|  0 min |          7.45 V |
| 10 min |          7.36 V |
| 20 min |          7.28 V |
| 30 min |          7.19 V |

The report states that the voltage regulator maintained a stable 5 V supply for the control electronics during the test.

---

# 💰 Cost Estimation

## Components

| Component                       |   Cost (₹) |
| ------------------------------- | ---------: |
| Arduino UNO                     |        550 |
| IR Sensor Module                |        180 |
| HC-SR04 Ultrasonic Sensor       |        120 |
| L298N Motor Driver              |        150 |
| 12 V DC Gear Motors with Wheels |        400 |
| 7.4 V Li-ion Battery            |        450 |
| 7805 Voltage Regulator          |         40 |
| 16×2 LCD                        |        180 |
| Push Button                     |         20 |
| Jumper Wires & Connectors       |         80 |
| **Component Subtotal**          | **₹2,170** |

## Fabrication

| Fabrication Item              | Cost (₹) |
| ----------------------------- | -------: |
| Cardboard & Acrylic Sheet     |      300 |
| Adhesive & Glue Materials     |      150 |
| Fasteners & Mounting Hardware |      120 |
| Test Track Materials          |       80 |
| **Fabrication Subtotal**      | **₹650** |

### Total Prototype Cost

```text
Component Cost       = ₹2,170
Fabrication Cost     = ₹650
--------------------------------
Total Project Cost   = ₹2,820
```

**Total reported prototype cost: ₹2,820**

---

# 🛡️ Safety Features

The prototype includes basic safety measures:

* Ultrasonic obstacle detection
* Automatic motor stopping
* Push-button start/stop
* LCD operating-status indication
* Protected electronics supply
* Secured wiring
* Controlled differential-drive movement

If an obstacle enters the preset safety distance, the robot stops both drive motors.

---

# 🔧 Maintenance

Recommended maintenance procedures include:

* Inspect wheels and motor mounts.
* Check chassis fasteners.
* Clean IR sensor surfaces.
* Clean ultrasonic sensor surface.
* Recalibrate IR thresholds when track conditions change.
* Monitor battery voltage.
* Check motor-driver wiring.
* Inspect battery condition.
* Update firmware when control parameters require adjustment.

---

# ✅ Advantages

* Reduces repetitive manual transportation work.
* Provides autonomous indoor movement.
* Supports medical supply transportation.
* Reduces unnecessary movement by hospital staff.
* Detects obstacles during navigation.
* Uses commonly available electronic components.
* Low-cost prototype implementation.
* Can be upgraded with advanced navigation technologies.
* Provides a foundation for hospital logistics automation.

---

# 🏥 Applications

Potential applications include:

* Medicine delivery from pharmacy to wards
* Laboratory sample transportation
* Medical supply transportation
* Hospital logistics automation
* Isolation-area material transportation
* Transportation between departments
* Document transportation
* Laboratory and diagnostic department support
* Autonomous mobile robot research and demonstration

---

# 🚀 Future Scope

The project report identifies several possible improvements:

### 📡 IoT Monitoring

Remote monitoring could be added for:

* Robot status
* Delivery status
* Battery condition
* Location information

### 🏷️ RFID-Based Ward Identification

RFID technology could be integrated to identify hospital zones and improve destination recognition.

### 📷 Camera-Based Navigation

A camera could replace or supplement fixed-path sensors for more flexible navigation.

### 🗺️ SLAM

SLAM-based navigation could allow the robot to construct and use an indoor map rather than depending entirely on a predefined line.

### 🏥 Hospital System Integration

The robot could eventually be connected with hospital information and dispatch systems.

### 🔐 Secure Medical Storage

The open prototype compartment could be replaced with a lockable and sanitizable enclosure.

---

# 📐 CAD Design

The project includes CAD representations of the robot:

* Isometric view
* Left-side view
* Top view
* Front view

Recommended GitHub location:

```text
CAD/
├── isometric-view.png
├── left-side-view.png
├── top-view.png
└── front-view.png
```

---

# 📷 Prototype

Recommended prototype image locations:

```text
images/
├── prototype-front.jpg
├── prototype-top.jpg
├── prototype-isometric.jpg
├── circuit.jpg
├── testing.jpg
├── obstacle-test.jpg
└── payload-test.jpg
```

---

# 📂 Recommended Repository Structure

```text
Autonomous-Medical-Supply-Delivery-Robot-for-Hospitals/
│
├── README.md
│
├── Arduino/
│   ├── MediRoute.ino
│   └── README.md
│
├── CAD/
│   ├── isometric-view.png
│   ├── left-side-view.png
│   ├── top-view.png
│   └── front-view.png
│
├── Hardware/
│   ├── Components.md
│   ├── Pin-Configuration.md
│   ├── Circuit-Diagram.png
│   └── Bill-of-Materials.md
│
├── Website/
│   ├── README.md
│   ├── login.png
│   ├── dashboard.png
│   ├── dispatch.png
│   ├── ward-selection.png
│   └── status.png
│
├── Documentation/
│   ├── Project-Overview.md
│   ├── Working-Principle.md
│   ├── Mechanical-Design.md
│   ├── Navigation.md
│   ├── Obstacle-Avoidance.md
│   ├── Fabrication.md
│   └── Testing.md
│
├── Results/
│   ├── Obstacle-Detection.md
│   ├── Navigation-Test.md
│   ├── Payload-Test.md
│   └── Battery-Test.md
│
├── Images/
│   ├── prototype/
│   ├── cad/
│   ├── testing/
│   └── circuit/
│
└── Report/
    └── MediRoute-Project-Report.pdf
```

---

# 📊 Project Performance Summary

| Parameter                          | Reported Result         |
| ---------------------------------- | ----------------------- |
| Navigation distance tested         | 3 m                     |
| Average navigation time            | Approximately 14 s      |
| Maximum reported lateral deviation | 2.2 cm                  |
| Obstacle safety threshold          | 15 cm                   |
| Stable payload                     | Approximately 400 g     |
| Tested unstable payload            | 500 g                   |
| Battery test duration              | 40 min operating period |
| Initial battery voltage            | 7.45 V                  |
| Voltage after 30 min               | 7.19 V                  |
| Prototype cost                     | ₹2,820                  |
| Main controller                    | Arduino UNO             |
| Navigation                         | IR line following       |
| Obstacle detection                 | HC-SR04                 |
| Drive system                       | Differential drive      |

---

# 👨‍🔧 Project Team

### Knowledge Institute of Technology, Salem

**Department of Mechanical Engineering**

| Team Member      | Register Number |
| ---------------- | --------------- |
| Ambika B         | 611223114003    |
| Aravinth R       | 611223114006    |
| Bhuvanan M       | 611223114013    |
| Dharaneshwaran B | 611223114020    |

### Project Supervisor

**Mr. A. Kamalakkannan, M.E., (Ph.D.)**
Assistant Professor
Department of Mechanical Engineering
Knowledge Institute of Technology, Salem

### Head of Department

**Dr. K. S. Prabhakaran, M.E., Ph.D.**
Associate Professor
Head of Department – Mechanical Engineering

---

# 🎓 Academic Project

**Degree:** Bachelor of Engineering
**Department:** Mechanical Engineering
**Institution:** Knowledge Institute of Technology, Salem
**University:** Anna University, Chennai
**Project Year:** 2026

---

# 📚 References

1. Najim, H. A., Kareem, I. S., & Abdul-Lateef, W. E. (2023). *Design and implementation of an omnidirectional mobile robot for medicine delivery in hospitals during the COVID-19 epidemic*. AIP Conference Proceedings, 2830, 070004.

2. Su, C. Y., & Young, K. Y. (2023). *Autonomous fever detection, medicine delivery, and environmental disinfection for pandemic prevention*. Applied Sciences, 13(24), 13316.

3. Abdulsaheb, J. A., & Kadhim, D. J. (2023). *Classical and heuristic approaches for mobile robot path planning: A survey*. Robotics, 12(4), 93.

4. *Development of a Mobile Robot for Distribution of Medicine in Hospitals*. (2024). IFAC-PapersOnLine.

5. Rondoni, C., Scotto Di Luzio, F., Tamantini, C., Tagliamonte, N. L., Chiurazzi, M., Ciuti, G., & Zollo, L. (2024). *Navigation benchmarking for autonomous mobile robots in hospital environment*. Scientific Reports, 14, 18334.

6. Riek, L. D. (2017). *Healthcare robotics*. Communications of the ACM, 60(11), 68–78.

7. Cadena, C., Carlone, L., Carrillo, H., et al. (2016). *Past, Present, and Future of Simultaneous Localization and Mapping: Toward the Robust-Perception Age*. IEEE Transactions on Robotics, 32(6), 1309–1332.

8. Macenski, S., et al. (2020). *The Marathon 2: A Navigation System*.

9. Quigley, M., Conley, K., Gerkey, B., et al. (2009). *ROS: An Open-Source Robot Operating System*.

10. Khatib, O. (1986). *Real-Time Obstacle Avoidance for Manipulators and Mobile Robots*. The International Journal of Robotics Research, 5(1), 90–98.

11. LaValle, S. M. (1998). *Rapidly-Exploring Random Trees: A New Tool for Path Planning*.

12. Hart, P. E., Nilsson, N. J., & Raphael, B. (1968). *A Formal Basis for the Heuristic Determination of Minimum Cost Paths*. IEEE Transactions on Systems Science and Cybernetics, 4(2), 100–107.

13. Fox, D., Burgard, W., & Thrun, S. (1997). *The Dynamic Window Approach to Collision Avoidance*. IEEE Robotics & Automation Magazine.

14. Durrant-Whyte, H., & Bailey, T. (2006). *Simultaneous Localization and Mapping: Part I*. IEEE Robotics & Automation Magazine, 13(2), 99–110.

15. Bailey, T., & Durrant-Whyte, H. (2006). *Simultaneous Localization and Mapping (SLAM): Part II*. IEEE Robotics & Automation Magazine, 13(3), 108–117.

16. Grisetti, G., Kümmerle, R., Stachniss, C., & Burgard, W. (2010). *A Tutorial on Graph-Based SLAM*. IEEE Intelligent Transportation Systems Magazine, 2(4), 31–43.

17. Borenstein, J., & Koren, Y. (1991). *The Vector Field Histogram—Fast Obstacle Avoidance for Mobile Robots*. IEEE Transactions on Robotics and Automation, 7(3), 278–288.

18. Siegwart, R., Nourbakhsh, I. R., & Scaramuzza, D. (2011). *Introduction to Autonomous Mobile Robots*. MIT Press.

19. Thrun, S. (2002). *Robotic Mapping: A Survey*.

---

# 📌 Project Status

**Prototype:** Fabricated
**Navigation:** Tested
**Obstacle Detection:** Tested
**Payload Carrying:** Tested
**Battery Performance:** Tested
**CAD Model:** Developed
**Hospital Dispatch Concept:** Developed
**Project Report:** Completed

---

## ⚠️ Prototype Scope

This repository documents an academic scaled prototype.

The reported system was tested on a simulated hospital corridor environment. It is not presented as a clinically certified medical device or as a deployed hospital system.

---

## 👨‍💻 Author

**Aravinth R**
B.E. Mechanical Engineering
Knowledge Institute of Technology, Salem

GitHub: [@Aravinth056](https://github.com/Aravinth056)

---

⭐ If you find this project useful, feel free to explore the design, hardware, testing and documentation.

