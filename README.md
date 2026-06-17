# Aerodynamic Wing Flutter Control Using IMU Sensor

## Overview

This project implements a simple real-time wing flutter control system using an MPU6050 inertial measurement unit (IMU) and a servo-actuated control surface. The system continuously measures the wing's lateral acceleration and adjusts the flap position to counter unwanted oscillations, demonstrating a basic active flutter suppression mechanism.

The project was developed as part of an aerospace control systems study using a NACA 2412 wing profile and an Arduino-based embedded control platform.

---

## Features

* Real-time acceleration monitoring using MPU6050
* Active flap control using SG90 servo motor
* Proportional flutter suppression based on wing motion
* Simple and lightweight Arduino implementation
* Serial monitoring for debugging and analysis

---

## Hardware Requirements

| Component            | Description                        |
| -------------------- | ---------------------------------- |
| Arduino UNO          | Main controller                    |
| MPU6050              | 3-axis accelerometer and gyroscope |
| SG90 Servo Motor     | Flap actuation                     |
| NACA 2412 Wing Model | Test platform                      |
| Jumper Wires         | Connections                        |
| 5V Power Supply      | System power                       |

---

## System Architecture

```text
Wing Motion
     ↓
 MPU6050 Sensor
     ↓
 Arduino UNO
     ↓
 Proportional Mapping Logic
     ↓
 SG90 Servo Motor
     ↓
 Control Flap Deflection
```

---

## Working Principle

1. The MPU6050 measures acceleration along the Y-axis.
2. The Arduino reads the sensor data continuously.
3. The acceleration value is mapped from a range of -10 m/s² to +10 m/s².
4. The mapped value is converted into a servo angle between 180° and 0°.
5. The servo adjusts the control flap position to oppose wing oscillations.

This creates a simple feedback-based flutter control system.

---

## Circuit Connections

### MPU6050 to Arduino UNO

| MPU6050 | Arduino UNO |
| ------- | ----------- |
| VCC     | 5V          |
| GND     | GND         |
| SDA     | A4          |
| SCL     | A5          |

### Servo to Arduino UNO

| Servo  | Arduino UNO |
| ------ | ----------- |
| Signal | D3          |
| VCC    | 5V          |
| GND    | GND         |

---

## Software Libraries

Install the following libraries through the Arduino IDE Library Manager:

* Adafruit MPU6050
* Adafruit Unified Sensor
* Servo
* Wire

---

## Arduino Code

The controller continuously reads Y-axis acceleration from the MPU6050 and maps it to a servo position.

```cpp
int value = a.acceleration.y;
value = map(value, -10, 10, 180, 0);
servo.write(value);
```

---

## Control Strategy

The implemented controller follows a simple proportional control concept:

```text
Flap Deflection ∝ Measured Wing Acceleration
```

Positive acceleration causes flap movement in one direction, while negative acceleration causes movement in the opposite direction.

---

## Results

* Successful acquisition of real-time wing acceleration data.
* Servo response directly correlated with wing motion.
* Demonstrated active flutter mitigation using feedback control.
* Stable operation achieved using a low-cost embedded platform.


## Project Title

**Aerodynamic Wing Flutter Control Using IMU Sensor**
