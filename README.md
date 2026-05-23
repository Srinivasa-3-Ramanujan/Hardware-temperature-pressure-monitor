# Hardware-Accelerated Atmospheric Monitor

Atmospheric monitoring system that uses **discrete 74-series logic gates** 
for decision-making instead of software — meaning the system responds in 
nanoseconds, independent of the microcontroller.

Built as a Digital Logic Design (DLD) course project.

---

## Why hardware logic instead of software?

Most Arduino projects do all their thinking in code — if humidity is high, 
do this. The problem: that depends on clock cycles, polling loops, and 
software that can hang.

This system offloads the decision to physical logic gates. The hardware 
**always** responds, even if the microcontroller freezes.

---

## How it works
1. **Sensors** capture temperature, humidity, and barometric pressure
2. **Arduino Nano** converts digital sensor data to PWM voltage signals
3. **LM339 Comparator** thresholds those voltages into clean HIGH/LOW logic
4. **7408 (AND) / 7432 (OR) gates** perform Boolean logic — e.g., HIGH humidity AND LOW pressure = storm incoming
5. **74151 MUX** acts as a hardware lookup table, selecting one of three output states: Stable / Turbulent / Critical

---

## Components

| Component | Role |
|---|---|
| Arduino Nano | Sensor data harvester + PWM bridge |
| DHT11 | Temperature and humidity sensing |
| BMP280 | Barometric pressure sensing |
| LM339 | Hardware-level voltage comparator |
| 7408 / 7432 | AND / OR logic gate matrix |
| 74151 MUX | Hardware lookup table for state selection |

---

## What I'd improve next

- Replace breadboard with a custom PCB (KiCad)
- Add an LCD to display current state
- Expand to 5 atmospheric states instead of 3

---
