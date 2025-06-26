# OBC Test Plan\n## Overview\nThis document details the test plan for the OBC subsystem.\n## Next Steps\n- To be developed during testing phase.
# OBC Test Plan
## Overview
This document details the test plan for the On-Board Computer (OBC) of the CanOrbitCubeSat-1 3U CubeSat, ensuring reliable data processing and subsystem control.

## Test Objectives
- Verify processing speed ≥ 100 MIPS.
- Confirm 1 MB Flash storage functionality.
- Validate I2C, SPI, UART interfaces.

## Test Methods
- **Benchmark Test**: Run CPU performance tests.
- **Storage Test**: Write/read 1 MB data.
- **Integration Test**: Test with ADCS, EPS, Communication.

## Test Procedures
1. **Setup**:
   - Connect CubeCore to test bench.
   - Link to OBC emulator via I2C, SPI, UART.
2. **Execution**:
   - Run Dhrystone benchmark for 100 MIPS.
   - Store and retrieve 1 MB test data.
   - Simulate subsystem commands.
3. **Validation**:
   - Compare against OBC-001 (processing) requirement.

## Test Equipment
- OBC emulator
- Multimeter
- Logic analyzer
- Test software (Dhrystone)

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Processing speed ≥ 100 MIPS.
- 1 MB Flash read/write successful.
- No interface communication errors.

## Risks and Mitigation
- **Risk**: Processor overheating.
  - **Mitigation**: Monitor with heat sink.
- **Risk**: Interface failure.
  - **Mitigation**: Test each interface separately.

## Next Steps
- Procure test equipment by August 15, 2025.
- Conduct preliminary benchmarks by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:27 | Initial placeholder |