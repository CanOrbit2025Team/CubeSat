# OBC Design Document\n## Overview\nThis document details the design of the On-Board Computer (OBC) for CanOrbitCubeSat-1.\n## Components\n- CubeCore (ARM Cortex-M4)\n## Next Steps\n- To be expanded during detailed design phase.
# OBC Design Document
## Overview
This document details the preliminary design of the On-Board Computer (OBC) for the  3U CubeSat, managing data processing and subsystem control in a 500 km sun-synchronous LEO.

## Components
- **Primary Component**: CubeCore
  - ARM Cortex-M4 processor (100 MHz).
  - 1 MB Flash, 256 KB RAM.
- **Backup**: Watchdog timer for fault recovery (to be evaluated).

## Design Specifications
- **Performance**:
  - Processing Speed: 100 MIPS
  - Storage: 1 MB Flash
  - Interfaces: I2C, SPI, UART
- **Mass**: 0.2 kg
- **Power Consumption**: 0.3 W
- **Physical Layout**:
  - Mounted internally (Z+ face) with heat sink.

## Design Approach
- **Software**: Real-time OS (FreeRTOS) for task scheduling.
- **Data Handling**: Buffers 8 MB/day from Payload, manages downlink.
- **Interfaces**: Controls ADCS, EPS, Communication via I2C/SPI/UART.

## Assumptions and Constraints
- Radiation-hardened components for LEO environment.
- Constrained by 3U form factor (10x10x30 cm) and 4 kg mass limit.
- Power budget limited to 10 W RMS, with 0.3 W allocated to OBC.

## Next Steps
- Finalize software architecture by July 15, 2025.
- Conduct processor benchmarking by August 1, 2025.
- Procure CubeCore for bench testing by August 15, 2025.
- Update this document post-PDR.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:27 | Initial placeholder |
