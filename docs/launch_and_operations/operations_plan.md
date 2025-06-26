# Operations Plan Document\n## Overview\nThis document outlines the operational procedures for CanOrbitCubeSat-1.\n## Next Steps\n- To be developed prior to launch.
# CanOrbitCubeSat-1 Operations Plan Document

## Overview
This document outlines the operations plan for the CanOrbitCubeSat-1 3U CubeSat, detailing the launch process and on-orbit activities for temperature and radiation data collection in a 500 km sun-synchronous LEO, with an 8 MB/day downlink.

## Launch Strategy
- **Launch Provider**: [To be selected, e.g., SpaceX Falcon 9]
- **Launch Site**: [To be determined, e.g., Vandenberg SLC-4E]
- **Launch Window**: December 15, 2025 - January 15, 2026
- **Deployment**: Via deployer (e.g., P-POD) into 500 km orbit.

## Operations Schedule
- **Pre-Launch**:
  - Final integration review: November 15, 2025
  - Payload activation test: November 20, 2025
- **Launch and Early Orbit Phase (LEOP)**:
  - Launch: December 20, 2025 (T0)
  - Initial contact: T0 + 1 hour
  - System checkout: T0 + 48 hours
- **Nominal Operations**:
  - Data collection: January 5, 2026 - June 30, 2026 (6 months)
  - Downlink schedule: Daily 9:00-10:00 AM EDT
- **Deorbit**:
  - Planned end: June 30, 2026
  - Passive reentry within 25 years

## Responsibilities
- **Mission Control**: Monitors telemetry, commands CubeSat.
- **Ground Station Team**: Operates university UHF station (435 MHz).
- **Payload Team**: Analyzes temperature/radiation data.
- **System Engineer**: Oversees anomaly resolution.

## Operations Procedures
1. **Pre-Launch**:
   - Conduct final environmental tests.
   - Upload flight software to OBC.
2. **LEOP**:
   - Establish contact via ground station.
   - Verify ADCS stabilization and payload activation.
3. **Nominal Operations**:
   - Collect data every orbit (98 minutes).
   - Downlink 8 MB/day to ground station.
   - Perform weekly health checks (battery, thermal).
4. **End of Mission**:
   - Deactivate payload and transmitters.
   - Monitor reentry trajectory.

## Ground Station Configuration
- **Equipment**: RTL-SDR receiver, dipole antenna, Raspberry Pi
- **Frequency**: 435 MHz UHF
- **Pass Prediction**: Use SatNOGS or GPredict

## Risks and Mitigation
- **Risk**: Launch delay.
  - **Mitigation**: Maintain readiness for 1-month window.
- **Risk**: Communication loss.
  - **Mitigation**: Use redundant ground stations.
- **Risk**: Battery depletion.
  - **Mitigation**: Monitor EPS and reduce payload duty cycle if needed.

## Next Steps
- Select launch provider by September 30, 2025.
- Schedule ground station passes by November 1, 2025.
- Update this plan post-launch contract.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:14 | Initial placeholder |