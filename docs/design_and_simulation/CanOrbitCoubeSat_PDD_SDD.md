# CanOrbitCubeSat-1 Preliminary Design Document(PDD)/System Design Document (SDD).

## 1. Introduction
**Purpose**: This document provides the preliminary system design for the CanOrbitCubeSat-1 3U CubeSat, detailing subsystem architectures, component selections, interfaces, and analyses to meet mission requirements.  
**Scope**: Covers system-level and subsystem designs for ADCS, Payload, Communication, Thermal, EPS, and OBC, with interface definitions and verification plans.  
**Reference Documents**: CanOrbitCubeSat-1 Mission Concept Document (MCD), System Requirements Specification (SRS), Requirements Refinement and Trade-Off Analysis Document.  
**Mission Objectives**:  
- Primary: Collect and downlink environmental data (temperature, radiation) in LEO.  
- Secondary: Demonstrate reliable CubeSat subsystems.

## 2. System Architecture
- **Form Factor**: 3U CubeSat (10x10x30 cm, max 4 kg).  
- **Block Diagram**:  
  ```
  [Payload: Sensors] ↔ UART ↔ [OBC: CubeCore]
                            ↕ I2C ↔ [ADCS: CubeSense]
                            ↕ SPI ↔ [Communication: ISIS UHF]
                            ↕ Power ↔ [EPS: GomSpace NanoPower]
                            ↕ Thermal ↔ [Thermal: MLI Blankets]
  ```
- **Physical Layout**:  
  - 1U: Payload (sensors) and antennas.  
  - 1U: OBC, ADCS, Communication.  
  - 1U: EPS (batteries, solar panels on all faces).  
  - MLI blankets cover external surfaces for thermal control.

## 3. Subsystem Designs

### 3.1 Payload (Sensor Suite)
- **Components**:  
  - Bosch BME280 (temperature sensor, -50°C to +100°C, 0.01°C resolution).  
  - Teledyne Radiation Detector (0-50 rad/day, 0.1 rad resolution).  
- **Design**: Sensors mounted on external face for environmental exposure, connected to OBC via UART.  
- **Performance**: Generates 8 MB/day (10 KB every 10 minutes).  
- **Mass**: 0.2 kg. **Power**: 1 W.  
- **Schematic**:  
  ```
  [BME280] → UART → [OBC]
  [Teledyne Detector] → UART → [OBC]
  ```

### 3.2 Attitude Determination and Control System (ADCS)
- **Components**: CubeSpace CubeSense (magnetorquers, magnetometers, sun sensors).  
- **Design**: 3-axis stabilization using magnetorquers, sensors on external faces.  
- **Performance**: ±0.5° pointing accuracy, 50s stabilization time.  
- **Mass**: 0.3 kg. **Power**: 1 W.  
- **Schematic**:  
  ```
  [Magnetometers, Sun Sensors] → I2C → [OBC] → I2C → [Magnetorquers]
  ```

### 3.3 Communication
- **Components**: ISIS UHF Transceiver (9.6 kbps, 430-440 MHz).  
- **Design**: Deployable dipole antenna, transceiver mounted on internal PCB.  
- **Performance**: Downlinks 8 MB/day over multiple ground passes (~2 hours/day).  
- **Mass**: 0.2 kg. **Power**: 2 W (transmit mode).  
- **Schematic**:  
  ```
  [OBC] → SPI → [ISIS Transceiver] → [Dipole Antenna]
  ```

### 3.4 Thermal
- **Components**: Multi-Layer Insulation (MLI) blankets.  
- **Design**: MLI blankets cover external surfaces, except solar panels and sensor apertures.  
- **Performance**: Maintains -20°C to +50°C, payload >0°C via battery proximity.  
- **Mass**: 0.05 kg. **Power**: 0 W.  
- **Schematic**: Passive design, no active components.

### 3.5 Electrical Power System (EPS)
- **Components**: GomSpace NanoPower (10 W RMS solar panels, 20 Wh Li-ion battery).  
- **Design**: Solar panels on all faces (except sensor face), battery pack in 1U section.  
- **Performance**: Provides 5 W continuous, 3.3V/5V rails.  
- **Mass**: 0.6 kg. **Power**: 1 W (EPS overhead).  
- **Schematic**:  
  ```
  [Solar Panels] → [Power Conditioning] → [Battery] → [3.3V/5V Rails] → [Subsystems]
  ```

### 3.6 On-Board Computer (OBC)
- **Components**: CubeCore (ARM Cortex-M4, 1 MB storage).  
- **Design**: Single PCB with I2C, SPI, UART interfaces, manages data and commands.  
- **Performance**: Stores 100 KB payload data, processes ADCS and communication tasks.  
- **Mass**: 0.1 kg. **Power**: 0.5 W.  
- **Schematic**:  
  ```
  [OBC] ↔ I2C ↔ [ADCS]
        ↔ SPI ↔ [Communication]
        ↔ UART ↔ [Payload]
        ↔ Power ↔ [EPS]
  ```

## 4. Interface Definitions
- **Mechanical**:  
  - Standard 3U CubeSat rails per CubeSat Design Specification.  
  - Subsystems mounted on PC/104 stack (96x90 mm PCBs).  
- **Electrical**:  
  - EPS provides 3.3V (OBC, ADCS, Payload) and 5V (Communication) rails.  
  - Power connectors: Molex Mini-Fit Jr.  
- **Data**:  
  - I2C: ADCS-OBC (400 kbps).  
  - SPI: Communication-OBC (1 Mbps).  
  - UART: Payload-OBC (115.2 kbps).  
- **Software**:  
  - OBC uses FreeRTOS for task scheduling.  
  - Data packets: 256-byte frames with CRC-16 error checking.

## 5. Preliminary Analyses
- **Mass Budget**:  
  | Subsystem | Mass (kg) | Margin (kg) |
  |-----------|-----------|-------------|
  | Payload   | 0.2       |             |
  | ADCS      | 0.3       |             |
  | Communication | 0.2   |             |
  | Thermal   | 0.05      |             |
  | EPS       | 0.6       |             |
  | OBC       | 0.1       |             |
  | Structure | 0.8       |             |
  | **Total** | **2.25**  | **1.75** (4 kg limit) |

- **Power Budget**:  
  | Subsystem | Power (W) | Margin (W) |
  |-----------|-----------|------------|
  | Payload   | 1         |            |
  | ADCS      | 1         |            |
  | Communication | 2 (tx) |            |
  | Thermal   | 0         |            |
  | EPS       | 1         |            |
  | OBC       | 0.5       |            |
  | **Total** | **7.5**   | **2.5** (10 W RMS) |

- **Data Budget**:  
  - Payload: 8 MB/day.  
  - Downlink: 8 MB/day over ~2 hours (9.6 kbps).  
  - Storage: 1 MB (OBC) supports >100 KB requirement.

- **Link Budget**:  
  - Frequency: 435 MHz (UHF).  
  - Transmit power: 1 W (30 dBm).  
  - Antenna gain: 0 dBi (dipole).  
  - Path loss: -140 dB (500 km).  
  - Ground station gain: 10 dBi.  
  - Margin: 6 dB (above 3 dB requirement).

- **Orbital Analysis**:  
  - Sun-synchronous orbit, 500 km.  
  - Solar illumination: ~60% of orbit (10 W RMS generation).  
  - Thermal range: -30°C to +60°C (MLI ensures -20°C to +50°C).

- **Structural Analysis**:  
  - Compliant with CubeSat Design Specification (6.5g axial, 9g lateral loads).  
  - Aluminum 6061 frame, PC/104 stack.

## 6. Verification Plan
- **Requirement Verification**:  
  | Requirement ID | Verification Method | Description |
  |----------------|--------------------|-------------|
  | PLD-001 (Payload) | Test | Measure temperature/radiation on bench. |
  | ADCS-001 (Pointing) | Simulation/Test | Simulate in MATLAB, test magnetorquers. |
  | COM-001 (Downlink) | Analysis/Test | Link budget analysis, ground station test. |
  | THM-001 (Thermal) | Simulation | Thermal model in MATLAB. |
  | EPS-001 (Power) | Analysis/Test | Power budget analysis, solar panel test. |
  | OBC-001 (Processing) | Test | Run FreeRTOS on CubeCore. |

- **Preliminary Test Plans**:  
  - ADCS: Bench test magnetorquers with Helmholtz coil.  
  - Payload: Calibrate sensors in controlled environment.  
  - Communication: End-to-end test with ground station emulator.  
  - Thermal: Simplified thermal model in MATLAB.  
  - EPS: Charge/discharge cycle test for battery.

## 7. Risk Assessment
- **Risks**:  
  | Risk | Likelihood | Impact | Mitigation |
  |------|------------|--------|------------|
  | Payload sensor failure | Low | High | Use redundant sensors (BME280 backup). |
  | ADCS magnetorquer failure | Medium | Medium | Select CubeSpace with flight heritage. |
  | Communication interference | Medium | High | Secure FCC frequency allocation. |
  | Battery degradation | Low | High | Monitor charge cycles, use GomSpace EPS. |

- **Mitigation**: Procure COTS components with flight heritage, conduct early subsystem tests.

## 8. Project Management
- **Milestones**:  
  - Complete detailed subsystem designs: August 2025.  
  - Procure COTS components: September 2025.  
  - Begin subsystem simulations: October 2025.  
- **Resources**:  
  - Budget: $25,500 spent, $24,500 remaining ($50,000 limit).  
  - Team: Subsystem leads for ADCS, Payload, Communication, Thermal, EPS, OBC.  
- **Next Steps**:  
  - Subsystem teams finalize detailed designs.  
  - Conduct simulations (e.g., MATLAB for thermal, STK for orbit).  
  - Procure components (e.g., CubeSpace, GomSpace).  
  - Update SRS with design-driven requirements.

## 9. Traceability Matrix
| Mission Objective | Requirement ID | Subsystem | Design Element | Status |
|-------------------|---------------|-----------|----------------|--------|
| Collect environmental data | PLD-001, PLD-002 | Payload | Bosch BME280, Teledyne Detector | Designed |
| Downlink data | COM-001 | Communication | ISIS UHF Transceiver | Designed |
| Operate 6 months | SYS-001, THM-001, EPS-001 | System, Thermal, EPS | MLI blankets, GomSpace EPS | Designed |
| Demonstrate subsystems | ADCS-001, OBC-001 | ADCS, OBC | CubeSense, CubeCore | Designed |