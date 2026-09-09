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
## 5. Hardware Components

- **STM32F103C6Tx** – Main microcontroller
- **RV2 Potentiometer** – Desired knee-angle input
- **RV1 Potentiometer** – Position-sensor interface/provision
- **L293D** – DC motor driver
- **DC Motor** – Knee-joint actuator
- **Virtual Terminal** – UART monitoring
- **Oscilloscope** – PWM waveform observation
5. Software and Tools
STM32CubeIDE
STM32CubeMX
Embedded C
STM32 HAL Library
Proteus 8
Virtual Terminal
Oscilloscope
6. Circuit / Interface Diagram

The STM32 generates the control signals required by the L293D motor driver.

The L293D receives:

PWM enable signal from PA6
Direction control signals from PB0 and PB1

The driver then controls the DC motor according to the controller output.

Circuit Diagram

Replace the placeholder below with your actual Proteus circuit/interface diagram:
![Circuit Interface Diagram](Documentation/Circuit_Interface_Diagram.png)
8. Control Algorithm

The controller continuously performs the following sequence:

Read Desired Angle
        |
        v
Calculate Position Error
        |
        v
Determine Motor Direction
        |
        v
Calculate PWM Duty Cycle
        |
        v
Update Motor / Joint Response
        |
        v
Repeat
The position error is calculated using:

Error = Desired Angle - Actual Angle

The PWM duty cycle is approximately proportional to the magnitude of the error:

PWM Duty = |Error| × PWM Gain

The PWM duty cycle is limited to a maximum of 100%.
