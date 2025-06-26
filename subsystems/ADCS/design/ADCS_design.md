# ADCS Design Document\n## Overview\nThis document details the design of the Attitude Determination and Control System (ADCS) for CanOrbitCubeSat-1.\n## Components\n- CubeSpace CubeSense (magnetorquers, sensors)\n## Next Steps\n- To be expanded during detailed design phase.
# ADCS Design Document
## Overview
This document details the preliminary design of the Attitude Determination and Control System (ADCS) for the CanOrbitCubeSat-1 3U CubeSat, ensuring ±0.5° pointing accuracy and 50s stabilization time in a 500 km sun-synchronous LEO.

## Components
- **Primary Component**: CubeSpace CubeSense
  - Magnetorquers, 3-axis magnetometers, and sun sensors.
  - Provides 3-axis stabilization with ±0.5° accuracy.
- **Backup**: Potential redundant magnetorquers (to be evaluated).

## Design Specifications
- **Performance**:
  - Pointing Accuracy: ±0.5°
  - Stabilization Time: 50 seconds
  - Slew Rate: 0.5°/s (preliminary)
- **Mass**: 0.3 kg
- **Power Consumption**: 1 W
- **Interface**: I2C (400 kbps) to OBC for sensor data and actuator commands.
- **Physical Layout**:
  - Magnetometers and sun sensors on external faces (X±, Y±, Z-).
  - Magnetorquers integrated into the CubeSat frame.

## Design Approach
- **Control Algorithm**: Preliminary PID (Proportional-Integral-Derivative) control, implemented in OBC software.
- **Sensor Fusion**: Combines magnetometer and sun sensor data for attitude determination.
- **Actuation**: Magnetorquers adjust orientation using Earth’s magnetic field.

## Assumptions and Constraints
- Stable LEO environment with minimal disturbance torques.
- Constrained by 3U form factor (10x10x30 cm) and 4 kg mass limit.
- Power budget limited to 10 W RMS, with 1 W allocated to ADCS.

## Next Steps
- Finalize PID tuning parameters by July 15, 2025.
- Conduct MATLAB simulations by August 1, 2025.
- Procure CubeSense components for bench testing by August 15, 2025.
- Update this document post-PDR.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:16 | Initial placeholder |