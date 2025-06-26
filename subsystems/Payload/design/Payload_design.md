# Payload Design Document\n## Overview\nThis document details the design of the Payload subsystem for Can   CanOrbit2025-1.\n## Components\n- Bosch BME280, Teledyne radiation detector\n## Next Steps\n- To be expanded during detailed design phase.
# Payload Design Document
## Overview
This document details the preliminary design of the Payload subsystem for the CanOrbit2025-1 3U CubeSat, responsible for collecting temperature (-50°C to +100°C) and radiation (0-50 rad/day) data in a 500 km sun-synchronous LEO.

## Components
- **Primary Components**:
  - Bosch BME280: Temperature and humidity sensor with ±0.01°C accuracy.
  - Teledyne radiation detector: Measures radiation dose (0-50 rad/day) with 0.1 rad resolution.
- **Backup**: Potential redundant sensor (to be evaluated).

## Design Specifications
- **Performance**:
  - Temperature Range: -50°C to +100°C
  - Temperature Accuracy: ±0.01°C
  - Radiation Range: 0-50 rad/day
  - Sampling Rate: 1 sample per minute
- **Mass**: 0.2 kg
- **Power Consumption**: 0.5 W
- **Interface**: UART (115.2 kbps) to OBC for data transmission.
- **Physical Layout**:
  - BME280 on internal panel (Z+ face) for thermal exposure.
  - Radiation detector on external panel (X+ face) for direct exposure.

## Design Approach
- **Data Collection**: Continuous sampling with 10 KB data packets every 10 minutes.
- **Data Storage**: Temporary buffering on OBC (1 MB capacity).
- **Thermal Management**: Integrated with MLI blankets to maintain payload above 0°C.

## Assumptions and Constraints
- Stable thermal environment within -20°C to +50°C (per Thermal subsystem).
- Constrained by 3U form factor (10x10x30 cm) and 4 kg mass limit.
- Power budget limited to 10 W RMS, with 0.5 W allocated to Payload.

## Next Steps
- Finalize sensor calibration by July 15, 2025.
- Conduct thermal simulations by August 1, 2025.
- Procure sensors for bench testing by August 15, 2025.
- Update this document post-PDR.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:18 | Initial placeholder |