# ADCS Test Plan
## Overview
This document details the test plan for the Attitude Determination and Control System (ADCS) of the CanOrbitCubeSat-1 3U CubeSat, ensuring ±0.5° pointing accuracy and 50s stabilization time in a 500 km LEO environment.

## Test Objectives
- Verify pointing accuracy of ±0.5°.
- Confirm stabilization time within 50 seconds.
- Validate I2C interface with OBC.

## Test Methods
- **Bench Test**: Use a Helmholtz coil to simulate magnetic field, test magnetorquers.
- **Simulation**: Run MATLAB model to predict attitude control performance.
- **Integration Test**: Verify ADCS operation within the CubeSat stack.

## Test Procedures
1. **Setup**:
   - Mount ADCS on test jig with Helmholtz coil.
   - Connect to OBC via I2C (400 kbps).
2. **Execution**:
   - Apply magnetic field perturbations.
   - Record sensor data (magnetometers, sun sensors) and actuator response.
   - Measure stabilization time and accuracy.
3. **Validation**:
   - Compare results against ADCS-001 (pointing accuracy) and ADCS-002 (stabilization time) requirements.

## Test Equipment
- Helmholtz coil
- Multimeter
- OBC emulator (CubeCore)
- MATLAB software

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Pointing accuracy ≤ ±0.5°.
- Stabilization time ≤ 50s.
- No I2C communication errors.

## Risks and Mitigation
- **Risk**: Coil calibration error.
  - **Mitigation**: Calibrate coil with known magnetic field source.
- **Risk**: Sensor noise.
  - **Mitigation**: Average multiple readings.

## Next Steps
- Procure test equipment by August 15, 2025.
- Conduct preliminary bench tests by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:09 | Initial placeholder |# ADCS Test Plan\n## Overview\nThis document details the test plan for the ADCS subsystem.\n## Next Steps\n- To be developed during testing phase.
