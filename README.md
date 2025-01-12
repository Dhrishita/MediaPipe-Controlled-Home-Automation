# MediaPipe-Controlled-Home-Automation

This project demonstrates a home automation system controlled by hand gestures using a Raspberry Pi, relays, and an external webcam. The system recognizes specific finger gestures to control devices like a bulb, fan, and buzzer. 

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Components Required](#components-required)
- [Circuit Diagram](#circuit-diagram)
- [Connections with Raspberry Pi and Relay](#connections-with-raspberry-pi-and-relay)
- [Working of the Project](#working-of-the-project)
- [Installation](#installation)
- [Usage](#usage)
- [Contact](#contact)

## Introduction

Hand gesture recognition provides an intuitive way to control home appliances. This project leverages computer vision with OpenCV and Mediapipe libraries for gesture detection, and a Raspberry Pi with relays to switch appliances on or off based on detected gestures.

## Features

- Controls a bulb, fan, and buzzer using hand gestures.
- Intuitive recognition of individual finger gestures.
- Real-time feedback using a webcam.
- Efficient and responsive automation using Raspberry Pi and relays.

## Components Required

1. **Hardware**:
   - Raspberry Pi (any model with GPIO support)
   - Relay module (3 channels)
   - Bulb, Fan, and Buzzer
   - Breadboard and jumper wires
   - External webcam

2. **Software**:
   - Python 3.13
   - OpenCV
   - Mediapipe
   - RPi.GPIO library

## Circuit Diagram



## Connections with Raspberry Pi and Relay

### Table 1: Raspberry Pi to Breadboard

| Raspberry Pi GPIO Pin | Breadboard Pin  |
|-----------------------|-----------------|
| GPIO 6 (GND)          | Common Ground   |
| GPIO 4 (VCC)          | Common VCC      |

### Table 2: Relay Input Side to Breadboard

| Relay Pin | Breadboard Pin |
|-----------|----------------|
| VCC       | Common VCC     |
| GND       | Common GND     |

### Table 3: Relay Input to Raspberry Pi

| Relay Pin | Raspberry Pi GPIO Pin | Appliance |
|-----------|-----------------------|-----------|
| IN1       | GPIO 3                | Bulb      |
| IN2       | GPIO 5                | Fan       |
| IN3       | GPIO 8                | Buzzer    |

### Table 4: Relay Output for Bulb

| Relay Pin     | Bulb Connection                  |
|---------------|----------------------------------|
| NO (Relay 1)  | GND                              |
| C (Relay 1)   | Switch GND                       |

### Table 5: Relay Output for Fan

| Relay Pin     | Fan Connection                  | Breadboard Pin      |
|---------------|---------------------------------|---------------------|
| NO (Relay 2)  | VCC                             |         -           | 
| C (Relay 2)   |                                 | Common VCC          |
|      -        | GND                             | Common GND          |

### Table 6: Relay Output for Buzzer

| Relay Pin     | Buzzer Connection               | Breadboard Pin      |
|---------------|---------------------------------|---------------------|
| NO (Relay 3)  | VCC                             |         -           | 
| C (Relay 3)   |                                 | Common VCC          |
|      -        | GND                             | Common GND          |

## Working of the Project

1. **Gesture Detection**: The external webcam captures hand movements and detects gestures using the Mediapipe library.
2. **Command Interpretation**: Based on the number of fingers detected, the system sends commands to specific relays.
   - Index Finger: Toggles the bulb.
   - Middle Finger: Toggles the fan.
   - Pinky Finger: Toggles the buzzer.
3. **Appliance Control**: The relays act as switches to control the appliances.


## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Dhrishita/MediaPipeControlledHomeAutomation.git
   cd MediaPipeControlledHomeAutomation


