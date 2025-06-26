# Thermal Test Plan
## Overview
This document details the test plan for the Thermal subsystem of the CanOrbitCubeSat-1 3U CubeSat, ensuring a temperature range of -20°C to +50°C with MLI blankets.

## Test Objectives
- Verify temperature range of -20°C to +50°C.
- Confirm payload temperature above 0°C.
- Validate passive thermal design.

## Test Methods
- **Thermal Vacuum Test**: Use chamber to simulate LEO conditions.
- **Simulation**: Run MATLAB thermal model.
- **Integration Test**: Test within CubeSat stack.

## Test Procedures
1. **Setup**:
   - Place CubeSat in thermal vacuum chamber.
   - Monitor with internal thermocouples.
2. **Execution**:
   - Cycle temperature from -30°C to +60°C.
   - Record payload and battery temperatures.
3. **Validation**:
   - Compare against THM-001 (thermal range) requirement.

## Test Equipment
- Thermal vacuum chamber
- Thermocouples
- MATLAB software

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Temperature range -20°C to +50°C.
- Payload > 0°C.
- No thermal runaway.

## Risks and Mitigation
- **Risk**: MLI damage.
  - **Mitigation**: Handle with care, inspect pre-test.
- **Risk**: Uneven heating.
  - **Mitigation**: Adjust MLI coverage.

## Next Steps
- Procure chamber time by August 15, 2025.
- Conduct simulation by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:09 | Initial placeholder |# Thermal Test Plan\n## Overview\nThis document details the test plan for the Thermal subsystem.\n## Next Steps\n- To be developed during testing phase.
