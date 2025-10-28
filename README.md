# Ultrasonic SONAR-Based Object Localization & Drawing Pen System

This project implements a **40 kHz ultrasonic SONAR-based localization system** capable of detecting the position of an object in 2-D space with approximately **5 mm – 1 cm accuracy**.  
A custom **drawing pen mechanism** physically draws according to the detected coordinates.

The system continuously senses the object’s position using multiple receivers, performs triangulation, and visualizes the location on a terminal and LCD.

---

## ✅ Features

- 40 kHz ultrasonic transmitter
- Multi-receiver localization using triangulation
- Real-time 2-D coordinate measurement
- ~5 mm localization accuracy
- Drawing pen that traces path based on detected coordinates
- EEPROM-based configuration storage
- Shell command interface
- Coordinate display on serial terminal + LCD (I2C)

---

## 🛠 Hardware Overview

| Component | Purpose |
|----------|---------|
| **LM556 (Dual 555 Timer)** | 40 kHz wave generation with 50% duty cycle |
| **Ultrasonic Transmitter** | Emits ultrasonic pulses |
| **Ultrasonic Receivers (x3)** | Detect reflections |
| **TLC072 Op-Amp** | Signal amplification + rectification |
| **MCP5544** | Signal comparison (4-ch comparator) |
| **Tiva TM4C microcontroller** | Computation + triangulation |
| **LCD (I2C)** | Shows coordinates |
| **Drawing Pen** | Draws according to object coordinates |

---

## 🔍 Software Overview

### Key Responsibilities
- Read sensor times and compute position via triangulation
- EEPROM-based persistent configuration
- User shell command interface
- Noise filtering through averaging + variance filtering
- Coordinate rendering to LCD and serial terminal
- Real-time motion output for drawing pen

### Triangulation

Coordinates are computed from time-of-flight data from multiple receivers.  
Error tolerance is ~**5 mm per axis**, depending on calibrated geometry.

---

## 📟 Shell Commands

| Command | Args | Description |
|--------|------|-------------|
| `beep` | ir/beep2/beep3/fix freq duration | Configure ping/beep parameters |
| `beep` | ir/beep2/beep3/fix ON/OFF | Enable/disable source |
| `correct` | sensor offset slope | Calibration |
| `reset` | — | Reboot μC |
| `average` | count | Sample count |
| `variance` | value | Allowed noise variance |
| `distance` | — | Show raw sensor distances |
| `sensor` | id x y | Set sensor coordinate |

---

## 🖊 Drawing Pen Module

A compact mechanical drawing assembly is integrated to visualize location-tracking results.

✅ Tracks coordinates in real-time  
✅ Converts coordinates into physical drawing motion  
✅ Demonstrates mapping accuracy and trajectory logging  

This feature provides intuitive visualization of the SONAR positioning system.

