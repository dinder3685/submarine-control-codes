Here's a basic README file for the code:

---

# Submarine Robot Control System with MPU6050, ESCs, and Color Sensor

This project involves controlling a submarine robot with multiple motors using an Arduino. The system utilizes an MPU6050 sensor for orientation control, ESCs (Electronic Speed Controllers) for motor control, and a color sensor for environmental sensing.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Hardware Setup](#hardware-setup)
- [Libraries Used](#libraries-used)
- [Pin Configuration](#pin-configuration)
- [Code Explanation](#code-explanation)
- [Usage](#usage)
- [License](#license)

## Overview

This project uses an Arduino to control a submarine robot equipped with:

- **MPU6050**: Used for reading the robot's orientation (yaw, pitch, roll).
- **ESCs**: Control the robot's movement (forward, backward, left, right, up, down).
- **Color Sensor**: Used for detecting certain colors in the environment.

The robot can be controlled using serial commands to perform various tasks like moving in different directions, turning, and more.

## Features

- **MPU6050 Integration**: Real-time yaw, pitch, and roll tracking for orientation control.
- **Motor Control**: Control up to six motors using ESCs.
- **Button-Controlled System**: Toggle system state (ON/OFF) using a button.
- **Leak Detection**: The robot ascends if a leak is detected.
- **Serial Command Control**: Send commands via serial interface to control the robot's actions.

## Hardware Setup

### Components Required

- Arduino (e.g., Arduino Uno)
- MPU6050 sensor
- Six ESCs (for motor control)
- Servo motors (6)
- Color sensor (with UART communication)
- Button (for system ON/OFF toggle)
- Leak sensor (to trigger emergency actions)
- LED (for status indication)

### Pin Configuration

- **MPU6050**: 
  - SDA (A4) 
  - SCL (A5)
  - INT (D2)

- **ESCs**: Connected to pins 2, 3, 4, 5, 6, 7 on the Arduino.

- **Button**: Pin 12

- **LED**: Pin 11

- **Leak Sensor**: Pin 31 (adjust as needed)

- **Color Sensor**:
  - RX Pin: 15
  - TX Pin: 14

## Libraries Used

This project uses the following Arduino libraries:

- **Wire.h**: For I2C communication.
- **MPU6050_6Axis_MotionApps20.h**: For interacting with the MPU6050 sensor.
- **SoftwareSerial.h**: For communication with the color sensor.
- **Servo.h**: For controlling the ESCs using PWM signals.

Make sure to install the required libraries through the Arduino IDE Library Manager or manually.

## Code Explanation

### Setup

1. **Wire.begin()**: Initializes the I2C communication.
2. **MPU6050 Setup**: Initializes the MPU6050 sensor, calibrates it, and sets up the Digital Motion Processing (DMP) functionality.
3. **Motor Calibration**: The ESCs are calibrated during the setup using specific PWM values.
4. **Button & LED Setup**: The button toggles the system ON/OFF, and the LED indicates the system's status.
5. **Leak Sensor**: If a leak is detected (low signal), the robot ascends and stops all motors.

### Loop

- **Button Control**: The button state is monitored. If pressed, it toggles the system's ON/OFF state.
- **Leak Detection**: If a leak is detected, the robot ascends.
- **MPU6050 Data**: The robot continuously reads the yaw, pitch, and roll from the MPU6050.
- **Serial Command Parsing**: Commands sent via serial control the robot’s actions, such as moving forward, turning, rotating, etc.

### Movement Functions

- **moveForward()**: Moves the robot forward by adjusting motor speeds.
- **moveBackward()**: Moves the robot backward.
- **turnLeft()**: Turns the robot left based on yaw values.
- **turnRight()**: Turns the robot right.
- **moveUp()**: Moves the robot up.
- **moveDown()**: Moves the robot down.
- **rotate360()**: Rotates the robot 360 degrees until the target yaw is reached.

## Usage

1. **Upload the Code**: Load the code to the Arduino using the Arduino IDE.
2. **Connect the Robot**: Make sure all hardware components are connected according to the pin configuration.
3. **Open Serial Monitor**: Open the Arduino Serial Monitor at 115200 baud.
4. **Send Commands**: You can control the robot by typing commands into the Serial Monitor:
   - `1`: Move forward
   - `2`: Move backward
   - `3`: Turn left
   - `4`: Turn right
   - `5`: Move up
   - `6`: Move down
   - `7`: Strafe left
   - `8`: Strafe right
   - `0`: Stop all motors
   - `10`: Rotate 360 degrees
   - `44`: Trigger a custom action (e.g., shoot)
   - `72`: Custom action for stable position

## License

This project is open-source. Feel free to modify and share the code as needed.

---

You can adjust and customize this README further depending on the specifics of your project.
