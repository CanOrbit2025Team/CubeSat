# CanOrbitCubeSat-1 Requirements Refinement and Trade-Off Analysis Document

## 1. Introduction
**Purpose**: This document refines preliminary subsystem requirements for the CanOrbitCubeSat-1 3U CubeSat mission and documents trade-off analyses to ensure alignment with mission objectives.  
**Scope**: Covers requirements validation and trade-offs for ADCS, Payload, Communication, Thermal, EPS, and OBC subsystems.  
**Mission Objectives**:  
- Primary: Capture and downlink Earth images for educational use.  
- Secondary: Demonstrate student-built CubeSat subsystems.  
**Reference Documents**: Mission Concept Document (MCD), System Requirements Specification (SRS).

## 2. Requirements Refinement Process
- **Step 1**: Subsystem teams review preliminary requirements from the SRS.  
- **Step 2**: Validate requirements using feasibility analysis (e.g., COTS specs, simulations).  
- **Step 3**: Conduct trade-off analysis for key design decisions (e.g., COTS vs. custom components).  
- **Step 4**: Update requirements based on validation and trade-offs.  
- **Step 5**: Document inter-subsystem dependencies and refined requirements.

## 3. Subsystem Requirements Refinement

### 3.1 Attitude Determination and Control System (ADCS)
**Preliminary Requirements** (from SRS):  
- Pointing accuracy: ±0.5°.  
- Slew rate: 1°/s.  
- Stabilization time: <30 seconds.  
- Mass: <0.5 kg. Power: <2 W.

**Validation**:
- **Feasibility**: Reviewed COTS ADCS units (e.g., CubeSpace CubeADCS). CubeSpace offers ±0.3° accuracy, 0.8°/s slew rate, mass 0.4 kg, power 1.5 W.  
- **Constraints**: Mass and power within budget. Accuracy exceeds requirement.  
- **Issues**: Slew rate slightly below target; team assessed impact on imaging (minimal due to slow orbital dynamics).

**Trade-Off Analysis**:
| Option | Description | Pros | Cons | Decision |
|--------|-------------|------|------|----------|
| COTS (CubeSpace) | Pre-built 3-axis ADCS | High reliability, flight heritage, low development time | Higher cost ($10,000), fixed performance | Selected |
| Custom ADCS | In-house magnetorquers + sensors | Lower cost ($2,000), customizable | High development risk, longer schedule | Rejected |

**Refined Requirements**:
- Pointing accuracy: ±0.3° (updated to match COTS capability).  
- Slew rate: 0.8°/s (accepted trade-off).  
- Stabilization time: <30 seconds.  
- Mass: 0.4 kg. Power: 1.5 W.  
- Interface: I2C for OBC communication.

### 3.2 Payload (Visible-Spectrum Camera)
**Preliminary Requirements**:
- Resolution: 1-meter at 500 km altitude.  
- Data size: 100 MB/image.  
- Capture frequency: 1 image/orbit.  
- Mass: <0.5 kg. Power: <3 W.

**Validation**:
- **Feasibility**: Evaluated COTS camera (e.g., NanoAvionics EO Camera). Offers 1-meter resolution, 80 MB/image, mass 0.3 kg, power 2 W.  
- **Constraints**: Data size slightly lower (80 MB), reducing storage needs.  
- **Issues**: Camera requires 10-second stabilization before capture (ADCS dependency).

**Trade-Off Analysis**:
| Option | Description | Pros | Cons | Decision |
|--------|-------------|------|------|----------|
| COTS Camera | NanoAvionics EO Camera | Flight heritage, compact | Fixed resolution, cost ($8,000) | Selected |
| Custom Camera | Build with off-shelf optics | Lower cost ($3,000), tunable | High risk, no flight heritage | Rejected |

**Refined Requirements**:
- Resolution: 1-meter.  
- Data size: 80 MB/image (updated).  
- Capture frequency: 1 image/orbit.  
- Stabilization time: 10 seconds (ADCS dependency).  
- Mass: 0.3 kg. Power: 2 W.  
- Interface: UART for OBC data transfer.

### 3.3 Communication
**Preliminary Requirements**:
- Data rate: 9.6 kbps (UHF/VHF).  
- Downlink: 1 image/pass (5 minutes).  
- Mass: <0.3 kg. Power: <3 W.

**Validation**:
- **Feasibility**: COTS transceiver (e.g., ISIS UHF/VHF) supports 9.6 kbps, mass 0.2 kg, power 2.5 W. Downlink time for 80 MB image: ~70 minutes (multiple passes needed).  
- **Constraints**: Data rate limits single-pass downlink.  
- **Issues**: Regulatory approval for frequency allocation pending.

**Trade-Off Analysis**:
| Option | Description | Pros | Cons | Decision |
|--------|-------------|------|------|----------|
| UHF/VHF | ISIS Transceiver | Low power, simple antenna | Low data rate | Selected |
| S-Band | Higher data rate (1 Mbps) | Faster downlink | Higher power (5 W), complex antenna | Rejected |

**Refined Requirements**:
- Data rate: 9.6 kbps (UHF/VHF).  
- Downlink: 80 MB image over 2 passes (~35 min/pass).  
- Mass: 0.2 kg. Power: 2.5 W.  
- Interface: SPI for OBC.  
- Dependency: Ground station frequency coordination.

### 3.4 Thermal
**Preliminary Requirements**:
- Operating range: -20°C to +50°C.  
- Control: Passive (MLI blankets).  
- Mass: <0.1 kg.

**Validation**:
- **Feasibility**: Thermal analysis (using simplified orbital model) confirms passive control sufficient for LEO. MLI blankets add 0.05 kg.  
- **Constraints**: No active heaters needed for 500 km orbit.  
- **Issues**: Payload camera requires +10°C minimum (EPS battery dependency).

**Trade-Off Analysis**:
| Option | Description | Pros | Cons | Decision |
|--------|-------------|------|------|----------|
| Passive | MLI blankets | Low mass, no power | Limited control | Selected |
| Active | Heaters + thermostats | Precise control | Power (1 W), mass (0.2 kg) | Rejected |

**Refined Requirements**:
- Operating range: -20°C to +50°C.  
- Control: Passive (MLI blankets).  
- Mass: 0.05 kg.  
- Dependency: EPS battery maintains +10°C for camera.

### 3.5 Electrical Power System (EPS)
**Preliminary Requirements**:
- Power generation: 10 W (solar panels).  
- Storage: 20 Wh (Li-ion battery).  
- Distribution: 5 W continuous during imaging.  
- Mass: <0.8 kg.

**Validation**:
- **Feasibility**: COTS EPS (e.g., GomSpace NanoPower) provides 12 W (solar), 25 Wh (battery), mass 0.6 kg. Supports 5 W imaging mode.  
- **Constraints**: Power margin sufficient (20% excess).  
- **Issues**: Battery temperature must be >0°C (Thermal dependency).

**Trade-Off Analysis**:
| Option | Description | Pros | Cons | Decision |
|--------|-------------|------|------|----------|
| COTS EPS | GomSpace NanoPower | Reliable, integrated | Cost ($6,000) | Selected |
| Custom EPS | Build solar + battery | Lower cost ($2,000) | Development risk | Rejected |

**Refined Requirements**:
- Power generation: 12 W (solar panels).  
- Storage: 25 Wh (Li-ion battery).  
- Distribution: 5 W continuous, 3.3V/5V rails.  
- Mass: 0.6 kg.  
- Dependency: Thermal maintains battery >0°C.

### 3.6 On-Board Computer (OBC)
**Preliminary Requirements**:
- Processing: 32-bit microcontroller.  
- Storage: 1 MB for image data.  
- Power: <1 W. Mass: <0.2 kg.

**Validation**:
- **Feasibility**: COTS OBC (e.g., CubeComputer) offers ARM Cortex-M4, 2 MB storage, mass 0.1 kg, power 0.8 W. Supports I2C, SPI, UART interfaces.  
- **Constraints**: Storage exceeds needs; power within budget.  
- **Issues**: Software development for image processing pending.

**Trade-Off Analysis**:
| Option | Description | Pros | Cons | Decision |
|--------|-------------|------|------|----------|
| COTS OBC | CubeComputer | Flight heritage, interfaces | Cost ($4,000) | Selected |
| Custom OBC | Build with Arduino | Low cost ($500) | No flight heritage | Rejected |

**Refined Requirements**:
- Processing: ARM Cortex-M4.  
- Storage: 2 MB (updated).  
- Power: 0.8 W. Mass: 0.1 kg.  
- Interfaces: I2C (ADCS), SPI (Communication), UART (Payload).

## 4. Inter-Subsystem Dependencies
- **ADCS-Payload**: 10-second stabilization for camera capture.  
- **Payload-Communication**: 80 MB image requires 2 ground passes.  
- **Thermal-EPS**: Battery temperature >0°C.  
- **EPS-All**: 3.3V/5V power distribution to all subsystems.  
- **OBC-All**: Manages data/command interfaces (I2C, SPI, UART).

## 5. System-Level Budget Updates
- **Mass**: Total 2.15 kg (ADCS: 0.4 kg, Payload: 0.3 kg, Communication: 0.2 kg, Thermal: 0.05 kg, EPS: 0.6 kg, OBC: 0.1 kg, Structure: 0.5 kg). Margin: 1.85 kg (4 kg limit).  
- **Power**: Peak 8.8 W (ADCS: 1.5 W, Payload: 2 W, Communication: 2.5 W, Thermal: 0 W, EPS: 1 W, OBC: 0.8 W). Generation: 12 W. Margin: 3.2 W.  
- **Cost**: $28,000 (ADCS: $10,000, Payload: $8,000, Communication: $3,000, EPS: $6,000, OBC: $4,000). Budget: $50,000. Margin: $22,000.

## 6. Next Steps
- **Subsystem Teams**: Begin detailed design based on refined requirements.  
- **System Engineering**: Update SRS with refined requirements.  
- **Simulation**: Use MATLAB/STK for power/thermal/orbit validation.  
- **Regulatory**: Initiate FCC frequency allocation for Communication.  
- **Funding**: Incorporate cost estimates into sponsor proposal.

## 7. Traceability Matrix
| Mission Objective | Requirement | Subsystem | Status |
|-------------------|-------------|-----------|--------|
| Capture Earth images | 1-meter resolution, 80 MB/image | Payload | Validated |
| Downlink images | 9.6 kbps, 2 passes | Communication | Validated |
| Demonstrate subsystems | 3-axis stabilization, ±0.3° | ADCS | Validated |
| Operate 1 year | Passive thermal, 12 W power | Thermal, EPS | Validated |