# Smart Classroom Energy Saver (SCES)

A simple simulation-based project demonstrating how technology can reduce unnecessary energy consumption in classrooms.

---

## 📌 Project Objective

This project applies course concepts in a real-world context by:

- Identifying a meaningful problem  
- Designing a technical solution  
- Implementing a working simulation  
- Demonstrating understanding through documentation and evaluation  

---

## 📝 Problem Overview

Classrooms often waste electricity because lights or fans remain running even when no one is present. This results in:

- Higher energy bills  
- Unnecessary energy consumption  
- Negative environmental impact  

---

## 💡 Proposed Solution

The **Smart Classroom Energy Saver (SCES)** simulates an automated system that turns classroom lights **ON/OFF** based on occupancy detection.

### Key Features

- Motion sensor simulation  
- Automated decision-making system (controller)  
- Light system simulation  
- Console-based interface  
- No database or CRUD files required  

---

## 🛠️ System Design

### Components

1. **MotionSensor**  
   Simulates detection of presence using random values.

2. **LightSystem**  
   Controls the ON/OFF state of the classroom light.

3. **Controller**  
   Connects the sensor and light system, continuously monitoring activity.

---

## 📂 Code Implementation (Python)

```python
import time
import random

class MotionSensor:
    def detect_motion(self):
        # Randomly simulate someone entering or leaving
        return random.choice([True, False])

class LightSystem:
    def __init__(self):
        self.light_on = False

    def turn_on(self):
        if not self.light_on:
            self.light_on = True
            print("Light turned ON")

    def turn_off(self):
        if self.light_on:
            self.light_on = False
            print("Light turned OFF")

class Controller:
    def __init__(self, sensor, light):
        self.sensor = sensor
        self.light = light

    def run(self):
        print("Starting Smart Classroom Energy Saver Simulation...\n")

        for _ in range(10):
            motion = self.sensor.detect_motion()

            if motion:
                print("Motion detected → Classroom occupied")
                self.light.turn_on()
            else:
                print("No motion → Classroom empty")
                self.light.turn_off()

            time.sleep(1)

sensor = MotionSensor()
light = LightSystem()
controller = Controller(sensor, light)

controller.run()
