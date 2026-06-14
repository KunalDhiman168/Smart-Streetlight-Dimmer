# Smart Street Light Dimmer

An intelligent and energy-efficient street lighting system developed under the Texas Instruments BYTE Program at IIT Ropar. The system dynamically adjusts streetlight brightness based on real-time traffic and pedestrian activity using radar sensing and long-range wireless communication.

---


## Problem Statement

Conventional streetlights remain at full brightness throughout the night regardless of traffic density, leading to:

- Excessive power consumption
- High electricity costs
- Light pollution
- Environmental impact

The objective of this project is to develop a smart street lighting solution that automatically dims or brightens lights based on real-time traffic activity while maintaining public safety.

---

## Design Thinking Approach

### 1. Empathize

Research conducted through:

- Municipal worker interviews
- Street maintenance staff discussions
- Resident surveys
- Night-shift worker feedback
- Traffic flow observations

#### Key Findings

- Streetlights remain fully powered even when roads are empty.
- Municipal budgets are heavily affected by electricity costs.
- Maximum brightness is unnecessary in low-traffic areas.

#### Pain Points

- Energy wastage
- Increased operational costs
- Light pollution
- Environmental concerns

---

### 2. Define

#### Problem

Urban streetlights operate at full brightness irrespective of traffic during low-demand hours.

#### Goal

Design a system that:

- Detects approaching pedestrians and vehicles
- Dynamically adjusts brightness
- Reduces energy consumption
- Maintains road safety

#### Scope

- Operation from 10 PM to 5 AM
- Residential and industrial zones
- Individual and clustered streetlight control

---

### 3. Ideate

#### Core Design Principles

##### Safety

- Consistent illumination
- No privacy concerns
- Sensor-driven activation

##### Forecasting

- Detect movement before arrival
- Smooth brightness transitions

##### Responsive Illumination

- Bright when activity is detected
- Dim during inactivity

##### Scalability

- Modular architecture
- Easy future upgrades

---

## Sensor Selection Study

### Infrared / Ultrasonic

#### Pros

- Low cost
- Easy implementation

#### Cons

- Short range
- Alignment sensitive

---

### PIR Motion Sensor

#### Pros

- Human-focused detection

#### Cons

- Limited range
- Misses distant vehicles

---

### Camera

#### Pros

- Rich environmental information

#### Cons

- Expensive
- High power consumption
- Privacy concerns

---

### Radar

#### Pros

- Long-range detection
- Weather independent
- Detects speed and distance

#### Cons

- Higher initial cost

---

## Selected Sensor

### TI AWR6843 mmWave Radar

Features:

- FMCW Radar Technology
- Detection range up to 200 meters
- Real-time range and velocity measurement
- Reliable in fog, rain, and darkness

---

## Wireless Communication Study

### Bluetooth

Pros:

- Ultra-low power

Cons:

- Very short range

---

### WiFi

Pros:

- High-speed communication

Cons:

- High power consumption
- Requires network infrastructure

---

### LoRa

Pros:

- Very long range

Cons:

- Additional hardware
- Not a TI-native solution

---

## Selected Wireless Solution

### TI CC1312R7

Features:

- Integrated MCU + Radio
- Sub-GHz communication
- AES-128 encryption
- OTA firmware support
- PWM control support
- Communication range > 1 km

---

## System Architecture

### Streetlight Cluster

Each cluster consists of:

- 1 × AWR6843 Radar
- 5 × Streetlights
- 1 × CC1312R7 Controller

### Deployment

- Lamp spacing: 35 m
- Total cluster coverage: 175 m

### Working Principle

1. Radar detects approaching object.
2. Detection is processed by CC1312R7.
3. Wireless command is transmitted to nearby lamps.
4. All lamps increase brightness simultaneously.
5. Lamps return to dim mode after inactivity.

---

## Hardware Components

### Main Components

#### TI AWR6843 Radar

- Object detection
- Speed estimation
- Distance estimation

#### TI CC1312R7

- Processing unit
- Wireless communication
- PWM generation

#### Additional Components

- Solar Panel
- Charge Controller
- Lithium-Ion Battery
- Buck Converter
- LDR Sensor
- MOSFET Driver
- LED Lamp

---

## Block Diagram

```text
Solar Panel
      |
Charge Controller
      |
Li-Ion Battery
      |
Buck Converter
      |
    CC1312R7
    /      \
 Radar     LDR
    |
 PWM Output
    |
 MOSFET
    |
   LED

Wireless Communication
       |
Neighboring Streetlights
