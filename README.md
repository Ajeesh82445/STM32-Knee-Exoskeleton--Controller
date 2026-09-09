# STM32-Based Knee Exoskeleton Joint Position Control System

A Proteus-simulated embedded control system for knee-joint position control using an STM32F103C6Tx microcontroller, PWM-based DC motor control, and an L293D motor driver.

---

## Project Overview

This project demonstrates the control of a knee exoskeleton joint using a closed-loop position control concept.

The user provides a desired knee angle through a potentiometer. The STM32F103C6Tx reads the desired angle using its ADC, calculates the position error, and generates a PWM signal and motor-direction control signals. The L293D motor driver then controls the direction and speed of a DC motor.

The current Proteus implementation uses a **software-simulated joint-position response** to represent the actual knee angle. This allows the control algorithm to be demonstrated without requiring a mechanically coupled physical position sensor.

---

## Objective

The main objectives of the project are:

- To interface an angle input with an STM32 microcontroller using ADC.
- To calculate the difference between desired and actual joint angle.
- To control motor speed using PWM.
- To control motor direction according to the position error.
- To demonstrate forward, reverse, and stop operation.
- To simulate the complete control system using Proteus.

---

## System Architecture

```text
          Desired Knee Angle
          RV2 Potentiometer
                 |
                 v
        STM32F103C6Tx MCU
                 |
        +--------+--------+
        |                 |
     ADC Input        Error Calculation
        |                 |
        +--------> Desired - Actual
                          |
                 +--------+--------+
                 |                 |
                 v                 v
             PWM Output      Direction Control
              PA6              PB0 / PB1
                 |                 |
                 +--------+--------+
                          |
                          v
                       L293D
                          |
                          v
                      DC Motor
                          |
                          v
                Simulated Knee Joint
                          |
                          v
               Software Position Model
Hardware Components
STM32F103C6Tx
L293D Motor Driver
DC Motor
Potentiometers
Virtual Terminal
Oscilloscope
