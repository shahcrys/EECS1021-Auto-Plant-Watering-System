# EECS 1012 - Automated Plant Watering System 🌱💧

**Author**: Crystal Mumtaz-Shah  
**Course**: EECS 1021  
**Date**: April 12, 2024  

---

## Table of Contents
- [Introduction](#introduction)
- [Project Context](#project-context)
- [Features](#features)
- [Components](#components)
- [Setup & Installation](#setup--installation)
- [Implementation](#implementation)
- [Testing](#testing)
- [Learning Outcomes](#learning-outcomes)
- [Conclusion](#conclusion)

---

## Introduction
This project is an **automated plant watering system** that monitors soil moisture levels via voltage readings from a sensor. It activates a water pump when the soil is dry (voltage > 3.4V) and stops when the soil is adequately moist (voltage ≤ 2.8V). The system includes real-time data plotting and an OLED display for status updates.

---

## Project Context
Maintaining optimal soil moisture is critical for plant health. Manual monitoring is error-prone and time-consuming. This system automates the process by:
- Continuously measuring soil moisture.
- Watering plants when needed.
- Displaying real-time metrics (voltage, moisture level) on an OLED.
- Plotting data on a live graph.

---

## Features
### 🌟 Core Functionality
- **State Machine**: Uses `if/else` statements to control the pump based on voltage thresholds.
- **Real-Time Data Plotting**: Graphs moisture vs. time using Princeton's `StdDraw` library.
- **OLED Display**: Shows moisture levels, voltage, and pump status.
- **Emergency Stop**: A button to manually turn off the pump.

### 📊 Data Management
- **`ArrayList<Double> moistureList`**: Tracks moisture values over time.
- **`HashMap<Integer, Double> voltageMap`**: Maps timestamps to voltage readings.

### 🔌 Hardware Integration
- **Arduino Communication**: Uses `Firmata4J` to send/receive commands.
- **Components**: Moisture sensor, MOSFET, 12V battery, water pump.

---

## Components
| Component              | Purpose                                  |
|------------------------|------------------------------------------|
| Arduino Grove Board    | Controls all components.                 |
| Moisture Sensor (A0)   | Measures soil moisture.                  |
| Water Pump (D2)        | Delivers water to the plant.             |
| MOSFET                 | Regulates pump conductivity.             |
| 12V Battery            | Powers the pump.                         |
| OLED Display           | Shows real-time data.                    |
| Laptop (IntelliJ)      | Hosts the Java program.                  |

---

## Setup & Installation
### Hardware Setup
1. Connect the moisture sensor to **A0**.
2. Connect the MOSFET to **D2**.
3. Power the pump with the 12V battery.
4. Link the Arduino to the laptop via USB.

### Software Dependencies
- **Java** (with `Firmata4J` library for Arduino communication).
- **Princeton Standard Library** (`StdDraw` for graphing).
- Arduino IDE (to upload Firmata firmware).

---

## Implementation
### Code Structure
- **Main Class**: Manages the state machine, data collection, and Arduino communication.
- **Graph Class**: Handles real-time plotting using `StdDraw`.
- **Test Class**: Validates sensor readings, pump control, and button functionality.

### Key Logic Snippets
```java
// State Machine Example
if (voltage > 3.4) {
    pump.on();
    oled.display("Watering...");
} else if (voltage <= 2.8) {
    pump.off();
    oled.display("Soil Moist");
}

// Data Collection
moistureList.add(moistureValue);
voltageMap.put(counter_Array, voltage);
```

---

## Testing
A dedicated test class ensures:
1. **Board Connection**: Confirms Arduino is detected.
2. **Sensor Accuracy**: Validates moisture-to-voltage conversion.
3. **Pump Control**: Tests activation/deactivation via voltage thresholds.
4. **Emergency Button**: Verifies manual override functionality.

---

## Learning Outcomes
- **CLO1**: Built a test suite to validate hardware/software integration.
- **CLO2**: Integrated `StdDraw` for graphing and `Firmata4J` for Arduino communication.
- **CLO3**: Utilized `ArrayList` and `HashMap` for efficient data tracking.
- **CLO4**: Designed a state machine with `if/else` logic for pump control.
- **CLO5**: Applied encapsulation (e.g., private variables) for modular code.

---

## Conclusion
This project demonstrates the effective use of **object-oriented programming** and **hardware integration** to solve real-world problems. By combining Arduino, Java, and real-time data visualization, the system ensures optimal plant health with minimal manual intervention. Future enhancements could include IoT integration for remote monitoring!
