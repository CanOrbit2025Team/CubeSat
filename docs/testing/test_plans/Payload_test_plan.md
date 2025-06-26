# Payload Test Plan\n## Overview\nThis document details the test plan for the Payload subsystem.\n## Next Steps\n- To be developed during testing phase.
# Payload Test Plan
## Overview
This document details the test plan for the Payload subsystem of the CanOrbitCubeSat-1 3U CubeSat, ensuring accurate measurement of temperature (-50°C to +100°C) and radiation (0-50 rad/day).

## Test Objectives
- Verify temperature accuracy within 0.01°C.
- Confirm radiation detection range and resolution.
- Validate UART interface with OBC.

## Test Methods
- **Environmental Test**: Use climate chamber for temperature range.
- **Radiation Test**: Expose to calibrated radiation source.
- **Integration Test**: Test data transmission within CubeSat stack.

## Test Procedures
1. **Setup**:
   - Mount sensors in climate chamber.
   - Connect to OBC via UART (115.2 kbps).
2. **Execution**:
   - Vary temperature from -50°C to +100°C.
   - Expose to radiation source (0-50 rad/day).
   - Record data packets (10 KB every 10 minutes).
3. **Validation**:
   - Compare against PLD-001 (temperature) and PLD-002 (radiation) requirements.

## Test Equipment
- Climate chamber
- Radiation source (calibrated)
- OBC emulator
- Oscilloscope

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Temperature accuracy ±0.01°C.
- Radiation range 0-50 rad/day with 0.1 rad resolution.
- No UART data loss.

## Risks and Mitigation
- **Risk**: Sensor drift.
  - **Mitigation**: Calibrate before testing.
- **Risk**: Radiation source inaccuracy.
  - **Mitigation**: Use certified source.

## Next Steps
- Procure test equipment by August 15, 2025.
- Conduct calibration by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:09 | Initial placeholder |