# EPS Test Plan\n## Overview\nThis document details the test plan for the EPS subsystem.\n## Next Steps\n- To be developed during testing phase.
# EPS Test Plan
## Overview
This document details the test plan for the Electrical Power System (EPS) of the CanOrbit2025-1 3U CubeSat, ensuring 10 W RMS power generation and 20 Wh battery capacity.

## Test Objectives
- Verify power generation ≥ 10 W RMS.
- Confirm battery capacity ≥ 20 Wh.
- Validate I2C interface with OBC.

## Test Methods
- **Solar Simulation**: Use solar simulator to test power generation.
- **Battery Test**: Perform charge/discharge cycles.
- **Integration Test**: Test within CubeSat stack.

## Test Procedures
1. **Setup**:
   - Mount solar panels under simulator.
   - Connect to OBC via I2C (400 kbps).
2. **Execution**:
   - Simulate 1000 W/m² flux for 2 hours.
   - Charge battery to 20 Wh, then discharge.
   - Monitor rail voltages (3.3 V, 5 V).
3. **Validation**:
   - Compare against EPS-001 (power output) requirement.

## Test Equipment
- Solar simulator
- Multimeter
- Battery analyzer
- OBC emulator

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Power output ≥ 10 W RMS.
- Battery capacity ≥ 20 Wh.
- No I2C communication errors.

## Risks and Mitigation
- **Risk**: Simulator inaccuracy.
  - **Mitigation**: Calibrate with known light source.
- **Risk**: Battery failure.
  - **Mitigation**: Test with redundant circuit.

## Next Steps
- Procure test equipment by August 15, 2025.
- Conduct preliminary simulations by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:26 | Initial placeholder |
