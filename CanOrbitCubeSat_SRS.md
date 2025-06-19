# CanOrbitCubeSat-1 System Requirements Specification

## 1. Introduction
**Purpose**: This document specifies the functional, performance, and interface requirements for the CanOrbitCubeSat-1 3U CubeSat to ensure alignment with mission objectives.  
**Scope**: Covers system-level and subsystem requirements for ADCS, Payload, Communication, Thermal, EPS, and OBC.  
**Reference**: CanOrbitCubeSat-1 Mission Concept Document (MCD).

## 2. System-Level Requirements
- **SYS-001**: The CubeSat shall operate in a 500 km sun-synchronous LEO for at least 6 months.  
- **SYS-002**: The CubeSat shall not exceed 4 kg mass and 10x10x30 cm dimensions.  
- **SYS-003**: The CubeSat shall collect and downlink 100 data sets (10 KB each) in 6 months (minimum success).  
- **SYS-004**: The CubeSat shall comply with CubeSat Design Specification for deployer compatibility.  
- **SYS-005**: The CubeSat shall operate within a $50,000 budget for development and launch.

## 3. Subsystem Requirements

### 3.1 Payload (Sensor Suite)
- **PLD-001**: The payload shall measure temperature (-50°C to +100°C) and radiation levels (0-100 rad/day).  
- **PLD-002**: The payload shall generate 10 KB of data every 12 hours.  
- **PLD-003**: The payload shall have a mass <0.5 kg and power consumption <2 W.  
- **PLD-004**: The payload shall interface with OBC via UART.

### 3.2 Attitude Determination and Control System (ADCS)
- **ADCS-001**: The ADCS shall provide pointing accuracy of ±1°.  
- **ADCS-002**: The ADCS shall stabilize the CubeSat within 60 seconds.  
- **ADCS-003**: The ADCS shall have a mass <0.5 kg and power consumption <2 W.  
- **ADCS-004**: The ADCS shall interface with OBC via I2C.

### 3.3 Communication
- **COM-001**: The communication subsystem shall downlink 100 KB/day at 9.6 kbps (UHF).  
- **COM-002**: The communication subsystem shall have a mass <0.3 kg and power consumption <3 W.  
- **COM-003**: The communication subsystem shall interface with OBC via SPI.  
- **COM-004**: The communication subsystem shall comply with FCC regulations for frequency allocation.

### 3.4 Thermal
- **THM-001**: The thermal subsystem shall maintain components within -20°C to +50°C.  
- **THM-002**: The thermal subsystem shall use passive control (e.g., MLI blankets).  
- **THM-003**: The thermal subsystem shall have a mass <0.1 kg and zero power consumption.

### 3.5 Electrical Power System (EPS)
- **EPS-001**: The EPS shall generate 10 W via solar panels.  
- **EPS-002**: The EPS shall store 20 Wh in a Li-ion battery.  
- **EPS-003**: The EPS shall provide 5 W continuous power during data collection.  
- **EPS-004**: The EPS shall have a mass <0.8 kg.  
- **EPS-005**: The EPS shall provide 3.3V and 5V power rails to subsystems.

### 3.6 On-Board Computer (OBC)
- **OBC-001**: The OBC shall use a 32-bit microcontroller with 512 KB storage.  
- **OBC-002**: The OBC shall store 100 KB of payload data.  
- **OBC-003**: The OBC shall have a mass <0.2 kg and power consumption <1 W.  
- **OBC-004**: The OBC shall support I2C, SPI, and UART interfaces.

## 4. Constraints
- **CON-001**: Total mass shall not exceed 4 kg.  
- **CON-002**: Total power consumption shall not exceed 10 W peak.  
- **CON-003**: Development and launch costs shall not exceed $50,000.  
- **CON-004**: The CubeSat shall withstand launch vibrations per deployer standards.

## 5. Traceability Matrix
| Mission Objective | Requirement ID | Subsystem | Description |
|-------------------|---------------|-----------|-------------|
| Collect environmental data | PLD-001, PLD-002 | Payload | Measure temperature and radiation, 10 KB/12 hours |
| Downlink data | COM-001 | Communication | Downlink 100 KB/day |
| Operate 6 months | SYS-001, THM-001, EPS-001 | System, Thermal, EPS | LEO operation, thermal control, power generation |
| Demonstrate subsystems | ADCS-001, OBC-001 | ADCS, OBC | Pointing accuracy, data processing |

## 6. Next Steps
- Validate requirements with subsystem teams.  
- Conduct trade-off analysis for COTS vs. custom components.  
- Update SRS based on refinement outcomes.