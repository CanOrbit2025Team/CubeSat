# CanOrbitCubeSat-1 Software Design Document

## 1. Introduction
**Purpose**: This document details the software architecture for the CanOrbitCubeSat-1 On-Board Computer (OBC), specifying tasks, data flows, and error handling to meet mission requirements.  
**Scope**: Covers OBC software running FreeRTOS on CubeCore (ARM Cortex-M4), managing Payload, ADCS, and Communication subsystems.  
**Reference Documents**: CanOrbitCubeSat-1 Mission Concept Document (MCD), System Requirements Specification (SRS), Preliminary Design Document (PDD), Interface Control Document (ICD).  
**Mission Overview**: 3U CubeSat in 500 km LEO, collecting and downlinking 8 MB/day of environmental data.

## 2. Software Overview
- **Platform**: CubeCore (ARM Cortex-M4, 168 MHz, 1 MB flash, 192 KB RAM).  
- **Operating System**: FreeRTOS v10.5.1 (real-time task scheduling).  
- **Functions**:  
  - Collect payload data (temperature, radiation) every 10 minutes.  
  - Control ADCS for ±0.5° pointing accuracy.  
  - Manage communication (downlink 8 MB/day, uplink commands).  
  - Monitor subsystem health (power, temperature).  
  - Handle errors (e.g., data corruption, subsystem failure).  
- **Development Environment**:  
  - IDE: STM32CubeIDE.  
  - Compiler: GCC ARM Embedded.  
  - Debugging: JTAG/SWD via ST-Link.

## 3. Software Architecture
- **Tasks**: FreeRTOS tasks with priorities and stack sizes.  
  | Task | Priority | Stack (bytes) | Description |
  |------|----------|---------------|-------------|
  | Payload_Task | 3 | 1024 | Collects sensor data every 10 minutes. |
  | ADCS_Task | 4 | 2048 | Polls sensors, controls magnetorquers (10 Hz). |
  | Comm_Task | 3 | 2048 | Manages downlink/uplink during ground passes. |
  | Health_Task | 2 | 512 | Monitors power, temperature, logs errors. |
  | Idle_Task | 1 | 256 | FreeRTOS default idle task. |
- **Inter-Task Communication**:  
  - Queues: Payload data (10 KB packets) sent to Comm_Task.  
  - Semaphores: Synchronize I2C/SPI access.  
  - Event Groups: Signal ground pass start/end.  
- **Block Diagram**:  
  ```
  [Payload_Task] → Queue → [Comm_Task]
  [ADCS_Task] ↔ Semaphore ↔ [I2C Driver]
  [Comm_Task] ↔ Semaphore ↔ [SPI Driver]
  [Health_Task] → Log → [Flash Storage]
  ```

## 4. Data Flow
- **Payload Data**:  
  - Payload_Task reads sensors via UART (115.2 kbps).  
  - Data (10 KB: temperature 4 bytes, radiation 4 bytes, timestamp 2 bytes) stored in RAM.  
  - Sent to Comm_Task via queue every 10 minutes.  
- **ADCS Control**:  
  - ADCS_Task polls sensors via I2C (400 kbps, 10 Hz).  
  - Computes control commands for magnetorquers.  
  - Logs status to Health_Task.  
- **Communication**:  
  - Comm_Task formats 256-byte frames (CRC-16) for downlink via SPI (1 Mbps).  
  - Receives uplink commands, validates CRC, dispatches to tasks.  
- **Health Monitoring**:  
  - Health_Task checks EPS voltage (3.3V/5V), OBC temperature every 60 seconds.  
  - Logs errors to 1 MB flash (circular buffer).

## 5. Task Details
- **Payload_Task**:  
  - Period: 600 seconds (10 minutes).  
  - Reads UART, validates data, queues to Comm_Task.  
  - Error handling: Retry UART read on timeout.  
- **ADCS_Task**:  
  - Period: 100 ms (10 Hz).  
  - Reads I2C sensors, runs control algorithm (PID).  
  - Error handling: Switch to safe mode on I2C failure.  
- **Comm_Task**:  
  - Triggered by ground pass event (via PyEphem TLE).  
  - Sends queued data via SPI, processes uplink commands.  
  - Error handling: Retransmit on CRC error.  
- **Health_Task**:  
  - Period: 60 seconds.  
  - Reads ADC for voltage, temperature sensor.  
  - Logs errors to flash, triggers safe mode if critical.

## 6. Error Handling
- **Mechanisms**:  
  - CRC-16 for UART/SPI data integrity.  
  - Watchdog timer (10 seconds) resets OBC on task hang.  
  - Safe mode: Disable ADCS/Payload, reduce power, beacon status.  
- **Error Types**:  
  - Payload: Sensor timeout → Retry 3 times, log error.  
  - ADCS: I2C failure → Switch to magnetometer-only mode.  
  - Communication: CRC error → Request retransmission.  
  - EPS: Low voltage (<3.0V) → Enter safe mode.

## 7. Memory Management
- **Flash**:  
  - 1 MB total: 512 KB for code, 256 KB for data logs, 256 KB reserved.  
  - Circular buffer for health logs (100 KB max).  
- **RAM**:  
  - 192 KB total: 64 KB for tasks, 64 KB for buffers, 64 KB reserved.  
  - Payload buffer: 100 KB for 10 data packets.  
- **Allocation**: Static allocation via FreeRTOS to avoid fragmentation.

## 8. Verification
- **Tests**:  
  - Unit Tests: Simulate sensor data, test task scheduling in STM32CubeIDE.  
  - Integration Tests: Run on CubeCore with ADCS/Communication emulators.  
  - End-to-End: Test with Payload and ground station emulator.  
- **Compliance**:  
  - Verify OBC-001 (processing), OBC-002 (storage).  
  - Ensure 8 MB/day downlink via Comm_Task.

## 9. Project Management
- **Milestones**:  
  - Software architecture complete: August 2025.  
  - Task implementation: September 2025.  
  - Integration testing: October 2025.  
- **Resources**:  
  - Budget: $2,000 (development tools, CubeCore test boards).  
  - Team: Software lead, embedded engineer.  
- **Next Steps**:  
  - Implement FreeRTOS tasks in STM32CubeIDE.  
  - Develop drivers for I2C, SPI, UART.  
  - Simulate data flows with test harness.