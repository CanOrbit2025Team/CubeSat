# DemoSat-1 Interface Control Document (ICD)

## 1. Introduction
**Purpose**: This document specifies the mechanical, electrical, and software interfaces between DemoSat-1 subsystems to ensure compatibility and successful integration.  
**Scope**: Covers interfaces for ADCS, Payload, Communication, Thermal, EPS, and OBC in the 3U CubeSat.  
**Reference Documents**: DemoSat-1 Mission Concept Document (MCD), System Requirements Specification (SRS), Preliminary Design Document (PDD).  
**Mission Overview**: 3U CubeSat in 500 km LEO, collecting and downlinking environmental data (temperature, radiation).

## 2. System Overview
- **Subsystems**:  
  - Payload: Bosch BME280 (temperature), Teledyne radiation detector.  
  - ADCS: CubeSpace CubeSense (magnetorquers, sensors).  
  - Communication: ISIS UHF transceiver (9.6 kbps).  
  - Thermal: MLI blankets (passive).  
  - EPS: GomSpace NanoPower (10 W solar, 20 Wh battery).  
  - OBC: CubeCore (ARM Cortex-M4, FreeRTOS).  
- **Physical Layout**: 3U stack with PC/104 boards, solar panels on external faces, sensors/antennas on 1U face.

## 3. Mechanical Interfaces
- **Standard**: CubeSat Design Specification (3U, 10x10x30 cm, 4 kg max).  
- **Structure**: Aluminum 6061 frame with 6.5 mm rails.  
- **Subsystem Mounting**:  
  - All subsystems use PC/104 form factor (96x90 mm PCBs).  
  - Payload sensors mounted on external Z+ face (4x M2.5 bolts, 20x20 mm pattern).  
  - Antennas (UHF dipole) deploy from Z+ face, 50 cm length.  
  - Solar panels bonded to X±, Y±, Z- faces.  
  - MLI blankets wrap external surfaces, except sensors/antennas/solar panels.  
- **Stack Configuration**:  
  - Bottom (Z-): EPS (battery, power board).  
  - Middle: OBC, ADCS, Communication.  
  - Top (Z+): Payload, antennas.  
- **Clearances**: 5 mm minimum between PCBs, 10 mm for antenna deployment.

## 4. Electrical Interfaces
- **Power Distribution**:  
  - EPS provides 3.3V and 5V rails via Molex Mini-Fit Jr. connectors (4-pin, 4.2 mm pitch).  
  - Current limits: 3.3V (2 A max), 5V (1 A max).  
  - Subsystem power consumption:  
    - Payload: 1 W (3.3V).  
    - ADCS: 1 W (3.3V).  
    - Communication: 2 W (5V, transmit mode).  
    - OBC: 0.5 W (3.3V).  
    - EPS: 1 W (internal).  
    - Thermal: 0 W.  
- **Grounding**: Single-point ground at EPS to prevent loops.  
- **Connector Mapping**:  
  | Subsystem | Connector | Pins | Voltage |
  |-----------|-----------|------|---------|
  | OBC       | J1        | 1-2: 3.3V, 3-4: GND | 3.3V |
  | ADCS      | J2        | 1-2: 3.3V, 3-4: GND | 3.3V |
  | Communication | J3    | 1-2: 5V, 3-4: GND   | 5V   |
  | Payload   | J4        | 1-2: 3.3V, 3-4: GND | 3.3V |

## 5. Data Interfaces
- **Protocols**:  
  - **I2C**: ADCS-OBC (400 kbps, 7-bit addressing).  
  - **SPI**: Communication-OBC (1 Mbps, 8-bit frames).  
  - **UART**: Payload-OBC (115.2 kbps, 8N1).  
- **Interface Details**:  
  | Interface | Subsystems | Details |
  |-----------|------------|---------|
  | I2C       | OBC-ADCS   | OBC as master, ADCS address: 0x10. Data: sensor readings, actuator commands. |
  | SPI       | OBC-Communication | OBC as master, CS pin: GPIO5. Data: downlink/uplink packets. |
  | UART      | OBC-Payload | 115.2 kbps, Payload sends 10 KB every 10 minutes. |
- **Data Formats**:  
  - ADCS: 32-byte packets (sensor data: 16 bytes, status: 16 bytes).  
  - Communication: 256-byte frames with CRC-16.  
  - Payload: 10 KB data packets (temperature: 4 bytes, radiation: 4 bytes, timestamp: 2 bytes).  
- **Error Handling**: CRC-16 for SPI/UART, I2C retransmission on NACK.

## 6. Software Interfaces
- **OBC Software**: FreeRTOS on CubeCore.  
- **Command Structure**:  
  - Format: [Header: 2 bytes][Command ID: 1 byte][Payload: 0-32 bytes][CRC: 2 bytes].  
  - Example: ADCS slew command: [0xAA55][0x01][Angles: 12 bytes][CRC].  
- **Data Flow**:  
  - Payload → OBC (UART): Sensor data every 10 minutes.  
  - OBC → ADCS (I2C): Control commands every 1 second.  
  - OBC → Communication (SPI): Downlink data every ground pass.  
- **Timing**:  
  - ADCS polling: 10 Hz.  
  - Payload data: 0.00167 Hz (every 10 minutes).  
  - Communication: 1 Hz during ground passes.

## 7. Verification
- **Interface Tests**:  
  - Mechanical: Fit check with 3D-printed mockups.  
  - Electrical: Continuity and power draw tests on breadboard.  
  - Data: End-to-end test with OBC emulator (e.g., Arduino).  
- **Compliance**:  
  - Verify against SRS requirements (e.g., SYS-002, PLD-004, COM-003).  
  - Ensure CubeSat Design Specification compliance for mechanical interfaces.

## 8. Change Control
- **Process**: Interface changes require approval from system engineer and affected subsystem leads.  
- **Documentation**: Updates logged in ICD revision history.  
- **Revision History**:  
  | Version | Date       | Changes |
  |---------|------------|---------|
  | 1.0     | 2025-06-19 | Initial draft |