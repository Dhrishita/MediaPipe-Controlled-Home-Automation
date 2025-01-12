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

1. **Gesture Detection**: The external webcam captures hand movements and detects gestures using the Mediapipe library.
2. **Command Interpretation**: Based on the number of fingers detected, the system sends commands to specific relays.
   - Index Finger: Toggles the bulb.
   - Middle Finger: Toggles the fan.
   - Pinky Finger: Toggles the buzzer.
3. **Appliance Control**: The relays act as switches to control the appliances.

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


