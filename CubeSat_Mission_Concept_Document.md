# CubeSat Mission Concept Document

## 1. Mission Overview
**Mission Name**: CanOrbitCubeSat-1  
**Objective**: Demonstrate a low-cost CubeSat platform for educational outreach and Earth observation using a visible-spectrum camera.
**CubeSat Size**: 3U  
**Orbit**: Low Earth Orbit (LEO), 500 km altitude, sun-synchronous.  
**Mission Duration**: 1 year (minimum success: 6 months).  
**Stakeholders**: University research team, local high schools, commercial launch provider.

## 2. Mission Objectives
- **Primary**: Capture and downlink images of Earth's surface for educational use.  
- **Secondary**: Demonstrate student-built CubeSat subsystems (ADCS, EPS, OBC).  
- **Success Criteria**:  
  - Minimum: Capture and downlink 10 images with 1-meter resolution.  
  - Full: Capture and downlink 100 images, operate all subsystems for 1 year.

## 3. Concept of Operations (ConOps)
- **Launch Phase**: Deploy via a CubeSat deployer on a commercial launch vehicle.  
- **Initialization**: Deploy solar panels, establish communication with ground station.  
- **Operational Modes**:  
  - Imaging Mode: Payload captures images during daylight passes.  
  - Data Downlink Mode: Transmit images to ground station.  
  - Safe Mode: Low-power state for anomaly resolution.  
- **Ground Segment**: University ground station with UHF/VHF communication.

## 4. System Architecture
- **Form Factor**: 3U CubeSat (10 cm x 10 cm x 30 cm, max 4 kg).  
- **Subsystems**:  
  - **Payload**: Visible-spectrum camera (1-meter resolution, 100 MB/image).  
  - **ADCS**: 3-axis stabilization, ±0.5° pointing accuracy, reaction wheels.  
  - **Communication**: UHF/VHF transceiver, 9.6 kbps data rate.  
  - **Thermal**: Passive control (MLI blankets), operating range -20°C to +50°C.  
  - **EPS**: Solar panels (10 W), Li-ion battery (20 Wh).  
  - **OBC**: 32-bit microcontroller, 1 MB storage for image data.  
- **Interfaces**: I2C for inter-subsystem communication, 3.3V power distribution.

## 5. Preliminary Requirements
- **Payload**: Capture 1 image per orbit, store 5 images onboard.  
- **ADCS**: Slew rate of 1°/s, stabilize within 30 seconds.  
- **Communication**: Downlink 1 image per ground pass (5 minutes).  
- **Thermal**: Maintain components within operational temperature range.  
- **EPS**: Provide 5 W continuous power during imaging mode.  
- **OBC**: Process and store image data, manage subsystem commands.

## 6. Feasibility Assessment
- **Orbit**: Sun-synchronous orbit ensures consistent lighting for imaging.  
- **Mass Budget**: Estimated 3.5 kg (within 4 kg limit).  
- **Power Budget**: 10 W generation, 8 W peak consumption.  
- **Cost**: Estimated $50,000 (components, testing, launch).  
- **Launch**: Compatible with standard CubeSat deployers (e.g., P-POD).  
- **Risks**:  
  - Risk: Camera failure. Mitigation: Use COTS camera with flight heritage.  
  - Risk: Power shortfall. Mitigation: Include redundant battery pack.

## 7. Next Steps
- Develop detailed System Requirements Specification.  
- Conduct subsystem trade studies (e.g., COTS vs. custom ADCS).  
- Establish ground station infrastructure.  
- Secure funding and launch provider agreement.


## Author
- Soniya Purushothama
