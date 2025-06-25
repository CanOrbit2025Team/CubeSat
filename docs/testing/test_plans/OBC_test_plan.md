# OBC Test Plan\n## Overview\nThis document details the test plan for the OBC subsystem.\n## Next Steps\n- To be developed during testing phase.
# OBC Test Plan
## Overview
This document details the test plan for the On-Board Computer (OBC) of the CanOrbit2025-1 3U CubeSat, ensuring data processing, storage, and interface management with FreeRTOS.

## Test Objectives
- Verify 1 MB storage capacity.
- Confirm task scheduling with FreeRTOS.
- Validate I2C, SPI, UART interfaces.

## Test Methods
- **Functional Test**: Run FreeRTOS tasks on CubeCore.
- **Interface Test**: Simulate subsystem data flows.
- **Integration Test**: Test within CubeSat stack.

## Test Procedures
1. **Setup**:
   - Program CubeCore with FreeRTOS.
   - Connect to emulated subsystems (I2C, SPI, UART).
2. **Execution**:
   - Execute Payload, ADCS, Comm tasks.
   - Store 1 MB of test data.
   - Monitor task execution.
3. **Validation**:
   - Compare against OBC-001 (processing) and OBC-002 (storage) requirements.

## Test Equipment
- CubeCore development board
- STM32CubeIDE
- Oscilloscope

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Storage ≥ 1 MB.
- All tasks execute without deadlock.
- No interface errors.

## Risks and Mitigation
- **Risk**: Software crash.
  - **Mitigation**: Implement watchdog timer.
- **Risk**: Memory overflow.
  - **Mitigation**: Limit buffer sizes.

## Next Steps
- Procure development board by August 15, 2025.
- Develop test software by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:09 | Initial placeholder |