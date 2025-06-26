# CanOrbitCubeSat-1 Ground Segment Design Document

## 1. Introduction
**Purpose**: This document details the design of the CanOrbitCubeSat-1 ground segment, including hardware and software for communication with the 3U CubeSat.  
**Scope**: Covers ground station hardware (antennas, receivers), software (data processing, control), and operational procedures.  
**Reference Documents**: CanOrbit2025-1 Mission Concept Document (MCD), System Requirements Specification (SRS), Preliminary Design Document (PDD).  
**Mission Overview**: 3U CubeSat in 500 km LEO, downlinking 8 MB/day of environmental data via UHF (9.6 kbps).

## 2. Ground Segment Overview
- **Function**: Receive 8 MB/day of payload data, send commands to CubeSat, and process/store data for scientific analysis.  
- **Location**: University campus, rooftop installation.  
- **Components**:  
  - Hardware: UHF Yagi antenna, software-defined radio (SDR), rotor for antenna tracking, control PC.  
  - Software: GNU Radio for signal processing, custom Python scripts for data decoding and control.  
- **Operational Modes**:  
  - Receive Mode: Downlink data during ground passes (~5 minutes/pass, 4-6 passes/day).  
  - Command Mode: Uplink commands (e.g., mode switch, data request).  
  - Idle Mode: Antenna parked, system on standby.

## 3. Hardware Design
- **Antenna**:  
  - Type: 10-element UHF Yagi (435 MHz).  
  - Gain: 10 dBi.  
  - Beamwidth: 40°.  
  - Mounting: Azimuth-elevation rotor (Yaesu G-5500).  
- **Receiver/Transmitter**:  
  - Type: RTL-SDR (software-defined radio, 430-440 MHz).  
  - Sensitivity: -120 dBm.  
  - Transmit power: 1 W (with external amplifier).  
- **Control System**:  
  - PC: Linux workstation (Ubuntu 24.04, 16 GB RAM, 1 TB SSD).  
  - Rotor controller: Yaesu GS-232B, USB interface.  
- **Power**:  
  - 12V DC, 100 W (solar backup for outages).  
  - UPS for PC and rotor (30-minute runtime).  
- **Block Diagram**:  
  ```
  [Yagi Antenna] ↔ [LNA] ↔ [RTL-SDR] ↔ USB ↔ [Linux PC]
  [Antenna] ↔ [Rotor] ↔ RS-232 ↔ [PC]
  ```

## 4. Software Design
- **Software Stack**:  
  - **GNU Radio**: Signal demodulation (GFSK, 9.6 kbps).  
  - **Python Scripts**:  
    - Data decoding: Extract 256-byte frames, verify CRC-16.  
    - Command generation: Format uplink commands (e.g., [0xAA55][0x01][Data][CRC]).  
    - Orbit tracking: Use PyEphem to predict CubeSat passes.  
  - **Database**: SQLite for storing payload data (temperature, radiation, timestamps).  
  - **GUI**: Tkinter-based interface for operator control (mode selection, data visualization).  
- **Data Flow**:  
  - Downlink: Antenna → SDR → GNU Radio → Python (decode) → SQLite.  
  - Uplink: Operator → GUI → Python (encode) → GNU Radio → SDR → Antenna.  
- **Error Handling**:  
  - CRC-16 verification for downlink data.  
  - Retransmission request if errors detected.  
- **Sample Data Packet**:  
  ```
  [Header: 0xAA55][Payload: 250 bytes (temperature: 4 bytes, radiation: 4 bytes, etc.)][CRC: 2 bytes]
  ```

## 5. Operational Procedures
- **Setup**:  
  - Power on PC, SDR, rotor.  
  - Launch GNU Radio and Python scripts.  
  - Calibrate antenna using known satellite pass.  
- **Pass Operations**:  
  - Predict pass using PyEphem (TLE from NORAD).  
  - Track CubeSat with rotor (update every 1 second).  
  - Receive data (8 MB over ~2 hours/day, 4-6 passes).  
  - Send commands (e.g., switch to safe mode).  
- **Data Processing**:  
  - Decode and store data in SQLite.  
  - Generate CSV reports for scientific team.  
- **Shutdown**: Park antenna, backup data, power down non-essential components.

## 6. Performance Analysis
- **Link Budget**:  
  - CubeSat transmit power: 1 W (30 dBm).  
  - Path loss: -140 dB (500 km, 435 MHz).  
  - Ground antenna gain: 10 dBi.  
  - LNA gain: 20 dB.  
  - Receiver sensitivity: -120 dBm.  
  - Margin: 6 dB (above 3 dB requirement).  
- **Data Throughput**:  
  - 9.6 kbps × 5 min/pass × 5 passes/day = ~2.88 MB/pass, sufficient for 8 MB/day.  
- **Pass Availability**: 4-6 passes/day, ~5-7 minutes each (based on 500 km orbit).

## 7. Verification
- **Tests**:  
  - Hardware: Bench test SDR with signal generator.  
  - Antenna: Field test with local UHF source.  
  - Software: Simulate CubeSat data with Python script.  
  - End-to-End: Test with CubeSat emulator (e.g., Raspberry Pi with UHF transmitter).  
- **Compliance**:  
  - Verify COM-001 (8 MB/day downlink).  
  - Ensure FCC compliance for UHF frequency (435 MHz).

## 8. Project Management
- **Milestones**:  
  - Ground station hardware assembly: August 2025.  
  - Software development complete: September 2025.  
  - End-to-end test: October 2025.  
- **Resources**:  
  - Budget: $5,000 (Yagi: $500, SDR: $100, Rotor: $1,000, PC: $1,500, Misc: $1,900).  
  - Team: Ground station lead, software developer, RF engineer.  
- **Next Steps**:  
  - Procure hardware (Yagi, SDR, rotor).  
  - Develop Python scripts and GNU Radio flowgraphs.  
  - Secure FCC frequency allocation.