# STM32 Knee Exoskeleton Controller

A simulation-based knee exoskeleton control system developed using an STM32F103C6Tx microcontroller, PWM motor control, L293D motor driver, and Proteus.

The system compares a desired knee angle with a software-simulated actual knee angle and controls a DC motor to reduce the position error.

---

## Project Overview

The project demonstrates the basic control concept of a knee exoskeleton.

A potentiometer is used to provide the desired knee angle. The STM32 calculates the difference between the desired and actual angle and controls the DC motor through the L293D motor driver.

The complete system is developed and tested in Proteus simulation.

---

## Objectives

- Develop a basic knee-angle control system using STM32.
- Calculate the position error between desired and actual angle.
- Control motor direction according to the position error.
- Control motor speed using PWM.
- Demonstrate forward, reverse, and stop conditions.
- Monitor system parameters through UART.
- Implement and test the system using Proteus simulation.

---

## System Architecture

The overall control flow is:

```text
Desired Angle
     |
     v
Potentiometer
     |
     v
STM32F103C6Tx
     |
     +----------------+
     |                |
     v                v
Position Error      PWM
     |                |
     v                v
Direction          L293D
Control             |
     |               v
     +----------> DC Motor
                     |
                     v
              Simulated Joint
                     |
                     v
                Actual Angle
                     |
                     +------> Feedback
