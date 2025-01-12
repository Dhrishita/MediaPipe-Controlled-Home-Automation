# MediaPipe-Controlled-Home-Automation

This project demonstrates a home automation system controlled by hand gestures using a Raspberry Pi, relays, and an external webcam. The system recognizes specific finger gestures to control devices like a bulb, fan, and buzzer. 

## Table of Contents

- [Introduction](#introduction)
- [Media Pipe](#media-pipe)
- [Framework](#framework)
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

## Media Pipe

![mediapipe](https://github.com/user-attachments/assets/ca254866-5cd2-41c5-b8ab-22d0728cb9a1)


> MediaPipe offers open source cross-platform, customizable ML solutions for live and streaming media.

### What is Media Pipe?

MediaPipe is an open-source framework from Google that allows developers to build machine learning (ML) and artificial intelligence (AI) pipelines for cross-platform applications.

MediaPipe Solutions provides a suite of libraries and tools for us to quickly
apply artificial intelligence (AI) and machine learning (ML) techniques in our
applications. We can plug these solutions into our applications immediately,
customize them to our needs, and use them across multiple development
platforms. MediaPipe Solutions is part of the MediaPipe [open source
project](https://github.com/google/mediapipe), so you can further customize the
solutions code to meet your application needs.

These libraries and resources provide the core functionality for each MediaPipe
Solution:

*   **MediaPipe Tasks**: Cross-platform APIs and libraries for deploying
    solutions. [Learn
    more](https://developers.google.com/mediapipe/solutions/tasks).
*   **MediaPipe models**: Pre-trained, ready-to-run models for use with each
    solution.

These tools let you customize and evaluate solutions:

*   **MediaPipe Model Maker**: Customize models for solutions with your data.
    [Learn more](https://developers.google.com/mediapipe/solutions/model_maker).
*   **MediaPipe Studio**: Visualize, evaluate, and benchmark solutions in your
    browser. [Learn
    more](https://developers.google.com/mediapipe/solutions/studio).

![hand_landmarks_docs](https://github.com/user-attachments/assets/737ffbe4-93e7-4fe0-bc9e-a0dcae51d05d)

## Framework

To start using MediaPipe Framework, [install MediaPipe
Framework](https://developers.google.com/mediapipe/framework/getting_started/install)
and start building example applications in C++, Android, and iOS.

[MediaPipe Framework](https://developers.google.com/mediapipe/framework) is the
low-level component used to build efficient on-device machine learning
pipelines, similar to the premade MediaPipe Solutions.

Before using MediaPipe Framework, familiarize yourself with the following key
[Framework
concepts](https://developers.google.com/mediapipe/framework/framework_concepts/overview.md):

*   [Packets](https://developers.google.com/mediapipe/framework/framework_concepts/packets.md)
*   [Graphs](https://developers.google.com/mediapipe/framework/framework_concepts/graphs.md)
*   [Calculators](https://developers.google.com/mediapipe/framework/framework_concepts/calculators.md)

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

Below is a detailed breakdown of how the system operates:

### 1. **Gesture Detection**:
- An **external webcam** captures the hand movements of the user.
- The captured video frames are processed using the **Mediapipe** library, which performs **hand landmark detection** to identify the position of each finger.
- Based on the positions of the fingers, the number of visible fingers is calculated, and gestures are detected.

### 2. **Gesture Recognition**:
The system recognizes the following gestures to control the appliances:
- **One Finger (Index Finger Raised)**: Turns the **bulb** on or off.
- **Two Fingers (Index and Middle Fingers Raised)**: Turns the **fan** on or off.
- **Three Fingers (Index, Middle, and Ring Fingers Raised)**: Turns the **buzzer** on or off.

When the system detects a specific gesture, it interprets the gesture and sends a corresponding signal to the **Raspberry Pi's GPIO pins**.

### 3. **Command Interpretation**:
The hand gestures are mapped to specific GPIO pins connected to the relay module:
- **Index Finger** → Turns the bulb on/off by activating **Relay 1** (connected to GPIO 3).
- **Middle Finger** → Turns the fan on/off by activating **Relay 2** (connected to GPIO 5).
- **Pinky Finger** → Turns the buzzer on/off by activating **Relay 3** (connected to GPIO 8).

The system processes the detected gesture and interprets it as a command to control the corresponding appliance.

### 4. **Appliance Control**:
The **Raspberry Pi** sends signals to the **relay module** based on the recognized gesture:
- The relay's **input pins** (IN1, IN2, IN3) are connected to the Raspberry Pi GPIO pins (GPIO 3, GPIO 5, GPIO 8).
- When a gesture is recognized, the Raspberry Pi triggers the appropriate relay by providing a HIGH signal to its input pin, causing the relay to switch its corresponding output.

For example:
- **Relay 1** controls the **bulb**:
  - When the system detects the index finger, it sends a signal to Relay 1 to turn the bulb on or off by connecting the **NO (Normally Open)** pin of the relay to the bulb's power input.

### 5. **Real-Time Feedback**:
The system provides **real-time feedback** on the status of the appliances:
- When the appliances are turned on or off, the user can immediately see the result of their gesture.

### 6. **User Interaction**:
- The system waits for hand gestures and provides feedback after each gesture is processed.
- Users can repeat the gestures as needed to control different appliances.

### 7. **Exit the Program**:
- The program continues running until the user presses `q` to exit, which stops the webcam feed and releases the GPIO pins.

## Installation
## Hardware Setup

1. Connect the camera module to the Raspberry Pi.
2. Connect the LED indicator to the GPIO pins on the Raspberry Pi.
   
    ```bash
    sudo apt-get update
    sudo apt-get upgrade
    pip install pip==22.3.1 --break-system-packages
    pip install opencv-python
    pip install mediapipe
    pip install cvzone

## Usage
1. Clone this repository to your Raspberry Pi:
   
   ```bash
   git clone https://github.com/Dhrishita/mediapipe-controlled-home-automation.git
   cd mediapipe-controlled-home-automation
   
2. Run the Python script:
   
   ```bash
   python3 main.py

## Contact
If you have any questions or suggestions, feel free to open an issue or contact:
Dhrishita Parve: dhrishitap18@gmail.com
