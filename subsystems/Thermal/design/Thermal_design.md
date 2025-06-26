# Thermal Design Document\n## Overview\nThis document details the design of the Thermal subsystem for CanOrbit2025-1.\n## Components\n- MLI blankets\n## Next Steps\n- To be expanded during detailed design phase.
# Thermal Design Document
## Overview
This document details the preliminary design of the Thermal subsystem for the CanOrbit2025-1 3U CubeSat, ensuring a temperature range of -20°C to +50°C in a 500 km sun-synchronous LEO using MLI blankets.

## Components
- **Primary Component**: Multi-Layer Insulation (MLI) blankets
  - Kapton-based with aluminum coating.
  - Provides thermal insulation and passive control.
- **Heaters**: Resistive heaters (optional backup, to be evaluated).

## Design Specifications
- **Performance**:
  - Temperature Range: -20°C to +50°C
  - Heat Dissipation: 5 W max
  - Thermal Gradient: <10°C across CubeSat
- **Mass**: 0.15 kg
- **Power Consumption**: 0 W (passive), 1 W (with heaters)
- **Physical Layout**:
  - MLI covers all external faces (X±, Y±, Z±).
  - Heaters on internal panels (Z+ face) if needed.

## Design Approach
- **Passive Control**: MLI reduces heat loss/gain, leveraging solar flux.
- **Thermal Modeling**: Use MATLAB for heat transfer simulation.
- **Integration**: Ensures compatibility with Payload (BME280) and EPS.

## Assumptions and Constraints
- Orbital thermal environment varies with sun angle.
- Constrained by 3U form factor (10x10x30 cm) and 4 kg mass limit.
- Power budget limited to 10 W RMS, with 1 W allocated for heaters if active.

## Next Steps
- Finalize thermal model by July 15, 2025.
- Conduct simulation runs by August 1, 2025.
- Procure MLI materials for bench testing by August 15, 2025.
- Update this document post-PDR.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:24 | Initial placeholder |