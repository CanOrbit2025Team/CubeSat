# Communication Test Plan\n## Overview\nThis document details the test plan for the Communication subsystem.\n## Next Steps\n- To be developed during testing phase.
# Communication Test Plan
## Overview
This document details the test plan for the Communication subsystem of the CanOrbit2025-1 3U CubeSat, ensuring a downlink of 8 MB/day at 9.6 kbps via UHF.

## Test Objectives
- Verify downlink data rate of 9.6 kbps.
- Confirm 8 MB/day data transmission.
- Validate SPI interface with OBC.

## Test Methods
- **RF Test**: Use ground station emulator with UHF receiver.
- **Link Budget Test**: Measure signal strength and margin.
- **Integration Test**: Test within CubeSat stack.

## Test Procedures
1. **Setup**:
   - Deploy dipole antenna on test jig.
   - Connect to OBC via SPI (1 Mbps).
2. **Execution**:
   - Transmit 8 MB of test data over 2 hours.
   - Measure signal with receiver (435 MHz).
   - Verify CRC-16 integrity.
3. **Validation**:
   - Compare against COM-001 (downlink requirement).

## Test Equipment
- UHF receiver (RTL-SDR)
- Dipole antenna
- OBC emulator
- Spectrum analyzer

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Downlink rate ≥ 9.6 kbps.
- 8 MB/day transmitted successfully.
- No SPI communication errors.

## Risks and Mitigation
- **Risk**: Antenna deployment failure.
  - **Mitigation**: Test deployment mechanism separately.
- **Risk**: RF interference.
  - **Mitigation**: Secure FCC frequency allocation.

## Next Steps
- Procure test equipment by August 15, 2025.
- Conduct RF tests by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:20 | Initial placeholder |