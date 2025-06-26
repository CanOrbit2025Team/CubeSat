# Thermal Test Plan\n## Overview\nThis document details the test plan for the Thermal subsystem.\n## Next Steps\n- To be developed during testing phase.
# Thermal Test Plan
## Overview
This document details the test plan for the Thermal subsystem of the CanOrbit2025-1 3U CubeSat, ensuring a temperature range of -20°C to +50°C with MLI blankets.

## Test Objectives
- Verify temperature range of -20°C to +50°C.
- Confirm thermal gradient <10°C.
- Validate integration with Payload and EPS.

## Test Methods
- **Thermal Vacuum Test**: Use vacuum chamber to simulate space conditions.
- **Simulation**: Run MATLAB model to predict thermal performance.
- **Integration Test**: Test within CubeSat stack.

## Test Procedures
1. **Setup**:
   - Enclose CubeSat in vacuum chamber with MLI.
   - Install thermocouples on all faces.
2. **Execution**:
   - Cycle temperature from -20°C to +50°C.
   - Measure gradient across stack.
   - Monitor Payload and EPS temperatures.
3. **Validation**:
   - Compare against THM-001 (temperature range) requirement.

## Test Equipment
- Vacuum chamber
- Thermocouples
- MATLAB software
- OBC emulator

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Temperature range -20°C to +50°C maintained.
- Thermal gradient <10°C.
- No overheating of Payload or EPS.

## Risks and Mitigation
- **Risk**: Vacuum leak.
  - **Mitigation**: Check seals before testing.
- **Risk**: MLI degradation.
  - **Mitigation**: Test multiple samples.

## Next Steps
- Procure test equipment by August 15, 2025.
- Conduct preliminary simulations by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:24 | Initial placeholder |