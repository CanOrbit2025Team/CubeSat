#  Integration Plan Document

## Overview
This document outlines the integration plan for the 3U CubeSat, detailing the process for assembling and testing subsystems (ADCS, Payload, Communication, Thermal, EPS, OBC) into a functional system. The plan ensures compliance with the Preliminary Design Document (PDD) and Interface Control Document (ICD).

## Integration Strategy
- **Approach**: Sequential integration of subsystems onto the PC/104 stack, followed by system-level testing.
- **Order**: 
  1. EPS (power backbone)
  2. OBC (central controller)
  3. ADCS, Payload, Communication (peripheral subsystems)
  4. Thermal (final assembly with MLI blankets)
- **Location**: University lab with cleanroom facilities.

## Schedule
- **Start Date**: July 15, 2025
- **Milestones**:
  - Subsystem pre-integration checks: July 20, 2025
  - Initial stack assembly: August 1, 2025
  - System-level integration complete: September 15, 2025
  - Integration review: September 20, 2025
- **Duration**: 9 weeks

## Responsibilities
- **System Engineer**: Oversees integration, resolves interface issues.
- **Subsystem Leads**: 
  - ADCS: Ensures sensor/actuator alignment.
  - Payload: Verifies sensor mounting.
  - Communication: Tests antenna deployment.
  - Thermal: Applies MLI blankets.
  - EPS: Configures power rails.
  - OBC: Validates software integration.
- **Test Team**: Conducts post-integration tests.

## Integration Procedures
1. **Pre-Integration**:
   - Verify subsystem compliance with ICD (e.g., I2C, SPI, UART interfaces).
   - Perform bench tests on each subsystem.
2. **Assembly**:
   - Mount subsystems on PC/104 stack using M2.5 bolts.
   - Connect power (Molex Mini-Fit Jr.) and data interfaces.
   - Install MLI blankets, ensuring sensor/antennna access.
3. **System Testing**:
   - Power-on test with EPS.
   - Data flow test (OBC to subsystems).
   - End-to-end communication test with ground station emulator.
4. **Validation**:
   - Confirm requirements (e.g., SYS-001, COM-001) via test results.
   - Document anomalies and resolutions.

## Tools and Equipment
- PC/104 stack jig
- Multimeter for electrical checks
- Oscilloscope for signal verification
- Ground station emulator (Raspberry Pi with UHF)

## Risks and Mitigation
- **Risk**: Interface mismatch (e.g., I2C address conflict).
  - **Mitigation**: Pre-integration ICD review, use unique addresses.
- **Risk**: Mechanical misalignment.
  - **Mitigation**: 3D-printed mockups for fit checks.
- **Risk**: Power overload.
  - **Mitigation**: Gradual power-up with EPS monitoring.

## Next Steps
- Finalize subsystem designs by July 1, 2025.
- Procure integration tools by July 10, 2025.
- Conduct pre-integration tests starting July 15, 2025.
- Update this plan post-PDR feedback.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:06 | Initial placeholder |# Integration Plan Document\n## Overview\nThis document outlines the integration plan for DemoSat-1 subsystems.\n## Next Steps\n- To be developed during integration phase.
