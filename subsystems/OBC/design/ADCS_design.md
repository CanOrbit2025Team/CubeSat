# ADCS Design Document
## Overview
This document details the preliminary design of the Attitude Determination and Control System (ADCS) for the DemoSat-1 3U CubeSat. The ADCS ensures precise orientation control to support payload data collection in a 500 km sun-synchronous Low Earth Orbit (LEO).

## Components
- **Primary Component**: CubeSpace CubeSense
  - Includes magnetorquers, magnetometers, and sun sensors.
  - Provides 3-axis stabilization with ±0.5° pointing accuracy.
- **Backup Consideration**: Potential redundancy with additional magnetorquers (to be evaluated).

## Design Specifications
- **Performance**:
  - Pointing Accuracy: ±0.5°
  - Stabilization Time: 50 seconds
  - Slew Rate: 0.5°/s (preliminary, to be refined)
- **Mass**: 0.3 kg
- **Power Consumption**: 1 W
- **Interface**: I2C (400 kbps) to On-Board Computer (OBC) for sensor data and actuator commands.
- **Physical Layout**:
  - Magnetometers and sun sensors mounted on external faces (X±, Y±, Z-).
  - Magnetorquers integrated into the CubeSat frame for torque application.

## Design Approach
- **Control Algorithm**: Preliminary PID (Proportional-Integral-Derivative) control, to be implemented in OBC software.
- **Sensor Fusion**: Combines magnetometer and sun sensor data for attitude determination.
- **Actuation**: Magnetorquers adjust orientation using Earth’s magnetic field.

## Assumptions and Constraints
- Assumes stable LEO environment with minimal disturbance torques.
- Constrained by 3U CubeSat form factor (10x10x30 cm) and 4 kg mass limit.
- Power budget limited to 10 W RMS, with 1 W allocated to ADCS.

## Next Steps
- Conduct detailed design to finalize control algorithm parameters.
- Perform MATLAB simulations to validate pointing accuracy and stabilization time.
- Procure CubeSpace CubeSense components for bench testing.
- Update this document with test results and interface details post-PDR.

## Traceability
- **Requirement**: ADCS-001 (Pointing accuracy ±1°, refined to ±0.5°)
- **Mission Objective**: Demonstrate reliable CubeSat subsystems.

## Revision History
| Version | Date       | Changes             |
|---------|------------|---------------------|
| 1.0     | 2025-06-19 | Initial placeholder |