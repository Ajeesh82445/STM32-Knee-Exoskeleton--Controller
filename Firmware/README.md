# STM32 Firmware

Firmware for the STM32F103C6Tx-based knee exoskeleton joint position controller.

The firmware performs:
- Desired knee-angle acquisition using ADC
- Joint position error calculation
- Bidirectional motor control
- PWM-based motor speed control
- UART monitoring of system parameters

The firmware is developed using STM32CubeIDE and HAL libraries.
