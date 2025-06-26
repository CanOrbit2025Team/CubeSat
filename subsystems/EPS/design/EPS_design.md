# EPS Design Document\n## Overview\nThis document details the design of the Electrical Power System (EPS) for CanOrbitCubeSat-1.\n## Components\n- GomSpace NanoPower\n## Next Steps\n- To be expanded during detailed design phase.
# EPS Design Document
## Overview
This document details the preliminary design of the Electrical Power System (EPS) for the CanOrbitCubeSat-1 3U CubeSat, providing 10 W RMS power generation and 20 Wh battery capacity in a 500 km sun-synchronous LEO.

## Components
- **Primary Component**: GomSpace NanoPower
  - Solar panels (3U deployable) with GaAs cells.
  - Li-ion battery (20 Wh capacity).
- **Backup**: Redundant battery protection circuit (to be evaluated).

## Design Specifications
- **Performance**:
  - Power Generation: 10 W RMS
  - Battery Capacity: 20 Wh
  - Output Voltages: 3.3 V, 5 V rails
- **Mass**: 0.5 kg
- **Power Consumption**: 0.2 W (standby)
- **Interface**: I2C (400 kbps) to OBC for monitoring and control.
- **Physical Layout**:
  - Solar panels on X± and Y± faces.
  - Battery and EPS unit on Z+ face.

## Design Approach
- **Power Management**: Maximum Power Point Tracking (MPPT) for solar panels.
- **Energy Storage**: Li-ion battery with overcharge protection.
- **Distribution**: Regulated rails for Payload, ADCS, and Communication.

## Assumptions and Constraints
- Solar flux varies with orbit (average 1000 W/m² at 500 km).
- Constrained by 3U form factor (10x10x30 cm) and 4 kg mass limit.
- Power budget allocated as 10 W RMS total.

## Next Steps
- Finalize solar panel sizing by July 15, 2025.
- Conduct power simulations by August 1, 2025.
- Procure NanoPower unit for bench testing by August 15, 2025.
- Update this document post-PDR.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:26 | Initial placeholder |
