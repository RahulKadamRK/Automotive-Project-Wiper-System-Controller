# Automotive-Project-Wiper-System-Controller

This project implements a model-based wiper system control software component in Simulink, simulating real-time control of an automotive wiper motor based on driver inputs and rain sensor feedback.

## Project Overview

The wiper system is designed to regulate the motor's duty cycle and determine the activation status of the wiper based on:

- **Wiper Mode**: Off, Automatic, Low Speed, High Speed
- **Rain Sensor Error**: Fault detection
- **Wiper Speed Request**: (Applicable in Automatic mode, levels 0–7)

The system is scheduled to run every 10 milliseconds to meet real-time performance requirements.

## Features

- **Mode-Based Duty Cycle Control**:
  - Off Mode: 0% duty cycle
  - Low Speed Mode: 40% duty cycle
  - High Speed Mode: 70% duty cycle
  - Automatic Mode: Dynamic mapping of speed request levels (0–7) to duty cycles from 0% to 70%
  
- **Rain Sensor Fault Handling**:
  - Disables the wiper system by setting the duty cycle to 0% when a rain sensor error is detected.
  
- **Duty Cycle Smoothing**:
  - Gradually transitions the duty cycle in Automatic mode to prevent abrupt motor speed changes.

- **Subsystem Architecture Exploration**:
  - Developed and tested multiple subsystem designs to model the same functionality using different Simulink blocks and structures.

## Inputs

- **Wiper Mode** (`uint8`):  
  `0` - Off, `1` - Automatic, `2` - Low Speed, `3` - High Speed

- **Rain Sensor Error** (`boolean`):  
  `0` - No Error, `1` - Error Detected

- **Wiper Speed Request** (`uint8`, 0–7):  
  Applicable only in Automatic Mode

## Outputs

- **Wiper Motor Duty Cycle** (`float`):  
  Duty cycle value (%) controlling the wiper motor speed.

- **Wiper Active Flag** (`boolean`):  
  `0` - Wiper Off, `1` - Wiper Active

## Model Execution

- **Task Rate**: 10 ms (100 Hz)

## Getting Started

1. Open the model file (`WiperSystemModel.slx`) in MATLAB/Simulink.
2. Simulate the model and observe duty cycle behavior based on input signals.
3. Modify input parameters to test different operating modes and fault conditions.

## Tools Used

- MATLAB / Simulink (R202x)
- Model-Based Design principles
