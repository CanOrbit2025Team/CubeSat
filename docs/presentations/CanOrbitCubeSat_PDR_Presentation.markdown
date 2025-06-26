# CanOrbitCubeSat-1 Preliminary Design Review (PDR) Presentation

## Slide 1: Title Slide
**Content**:  
- **Title**: CanOrbitCubeSat-1 Preliminary Design Review  
- **Subtitle**: 3U CubeSat for Environmental Data Collection  
- **Details**:  
  - Presented by: [Your Team Name]  
  - Date: [Insert Date, e.g., July 15, 2025]  
  - University/Sponsor Logo(s)  
- **Visual**: CubeSat rendering or mission graphic  

**Speaker Notes**:  
- Welcome stakeholders to the PDR for CanOrbitCubeSat-1.  
- Briefly introduce the team and the purpose: to review the preliminary design and seek approval to proceed to detailed design.  

---

## Slide 2: Agenda
**Content**:  
- Mission Overview  
- System Requirements Recap  
- System Architecture  
- Subsystem Designs  
- Interface Definitions  
- Preliminary Analyses  
- Verification Plan  
- Risk Assessment  
- Project Management  
- Next Steps  

**Speaker Notes**:  
- Outline the presentation structure.  
- Highlight that we’ll cover technical design, analyses, and project status to demonstrate readiness.  

---

## Slide 3: Mission Overview
**Content**:  
- **Objective**: Collect temperature and radiation data in 500 km sun-synchronous LEO, downlink 8 MB/day.  
- **Secondary Goal**: Demonstrate reliable CubeSat subsystems.  
- **Key Parameters**:  
  - CubeSat: 3U, 4 kg max, $50,000 budget  
  - Mission Duration: 1 year (6 months minimum)  
  - Orbit: 500 km, sun-synchronous  
- **Stakeholders**: University, scientific community, launch provider  

**Visual**: Orbit diagram or mission timeline  

**Speaker Notes**:  
- Recap CanOrbitCubeSat-1’s goals: primary science mission and educational demonstration.  
- Emphasize alignment with stakeholder interests (e.g., science data, student training).  

---

## Slide 4: System Requirements Recap
**Content**:  
- **Key Requirements**:  
  - SYS-001: Operate in 500 km LEO for 6 months.  
  - SYS-003: Downlink 100 data sets (8 MB/day).  
  - PLD-001: Measure temperature (-50°C to +100°C), radiation (0-50 rad/day).  
  - COM-001: Downlink at 9.6 kbps (UHF).  
  - EPS-001: Generate 10 W via solar panels.  
- **Constraints**:  
  - Mass: ≤4 kg  
  - Power: ≤10 W peak  
  - Budget: $50,000  

**Visual**: Table or traceability matrix excerpt  

**Speaker Notes**:  
- Summarize critical requirements from the SRS.  
- Note that refined requirements (e.g., 8 MB/day) guide the design.  
- Confirm traceability to mission objectives.  

---

## Slide 5: System Architecture
**Content**:  
- **Form Factor**: 3U CubeSat (10x10x30 cm)  
- **Subsystems**:  
  - Payload: Bosch BME280, Teledyne radiation detector  
  - ADCS: CubeSpace CubeSense  
  - Communication: ISIS UHF transceiver  
  - Thermal: MLI blankets  
  - EPS: GomSpace NanoPower  
  - OBC: CubeCore (FreeRTOS)  
- **Block Diagram**:  
  ```
  [Payload] ↔ UART ↔ [OBC] ↔ I2C ↔ [ADCS]
                       ↕ SPI ↔ [Comm]
                       ↕ Power ↔ [EPS]
                       ↕ Thermal ↔ [Thermal]
  ```
- **Physical Layout**: 1U (Payload, antennas), 1U (OBC, ADCS, Comm), 1U (EPS)  

**Visual**: Block diagram, 3D CubeSat model  

**Speaker Notes**:  
- Present the high-level system architecture.  
- Highlight modularity (PC/104 stack) and COTS components for reliability.  
- Explain layout optimizes sensor exposure and power generation.  

---

## Slide 6: Subsystem Designs - Payload & ADCS
**Content**:  
- **Payload**:  
  - Components: Bosch BME280 (temperature), Teledyne detector (radiation)  
  - Performance: 8 MB/day, 0.2 kg, 1 W  
  - Design: Sensors on Z+ face, UART to OBC  
- **ADCS**:  
  - Components: CubeSpace CubeSense (magnetorquers, sensors)  
  - Performance: ±0.5° accuracy, 50s stabilization, 0.3 kg, 1 W  
  - Design: Sensors on external faces, I2C to OBC  

**Visual**: Payload sensor photo, ADCS schematic  

**Speaker Notes**:  
- Describe Payload’s role in meeting science objectives.  
- Highlight ADCS’s precision for orientation (minimal pointing needs).  
- Note COTS selection reduces risk.  

---

## Slide 7: Subsystem Designs - Communication & Thermal
**Content**:  
- **Communication**:  
  - Components: ISIS UHF transceiver (9.6 kbps, 435 MHz)  
  - Performance: 8 MB/day over ~2 hours, 0.2 kg, 2 W  
  - Design: Dipole antenna on Z+, SPI to OBC  
- **Thermal**:  
  - Components: MLI blankets  
  - Performance: -20°C to +50°C, 0.05 kg, 0 W  
  - Design: Passive control, covers external surfaces  

**Visual**: Antenna deployment diagram, MLI blanket photo  

**Speaker Notes**:  
- Explain Communication’s ability to meet downlink requirements.  
- Note Thermal’s simplicity (passive) suits LEO environment.  
- Highlight FCC coordination for UHF frequency.  

---

## Slide 8: Subsystem Designs - EPS & OBC
**Content**:  
- **EPS**:  
  - Components: GomSpace NanoPower (10 W solar, 20 Wh battery)  
  - Performance: 5 W continuous, 0.6 kg  
  - Design: Solar panels on X±, Y±, Z-, 3.3V/5V rails  
- **OBC**:  
  - Components: CubeCore (ARM Cortex-M4, FreeRTOS)  
  - Performance: 1 MB storage, 0.1 kg, 0.5 W  
  - Design: Manages data via I2C, SPI, UART  

**Visual**: Solar panel layout, OBC PCB photo  

**Speaker Notes**:  
- Emphasize EPS’s power margin (2.5 W) for reliability.  
- Highlight OBC’s role as system brain, with FreeRTOS for multitasking.  
- Note lightweight, low-power designs.  

---

## Slide 9: Interface Definitions
**Content**:  
- **Mechanical**:  
  - PC/104 stack, 3U rails, M2.5 bolts for Payload  
- **Electrical**:  
  - 3.3V (OBC, ADCS, Payload), 5V (Communication)  
  - Molex Mini-Fit Jr. connectors  
- **Data**:  
  - I2C (ADCS-OBC, 400 kbps)  
  - SPI (Communication-OBC, 1 Mbps)  
  - UART (Payload-OBC, 115.2 kbps)  
- **Software**:  
  - 256-byte frames, CRC-16 error checking  
  - FreeRTOS task scheduling  

**Visual**: Interface table or schematic  

**Speaker Notes**:  
- Summarize interfaces from ICD.  
- Highlight standardized connectors and protocols for integration ease.  
- Note verification via fit checks and data tests.  

---

## Slide 10: Preliminary Analyses
**Content**:  
- **Mass Budget**: 2.25 kg (1.75 kg margin, 4 kg limit)  
- **Power Budget**: 7.5 W peak (2.5 W margin, 10 W RMS)  
- **Data Budget**: 8 MB/day, 1 MB storage (>100 KB needed)  
- **Link Budget**: 6 dB margin (UHF, 435 MHz)  
- **Orbital Analysis**: 60% solar illumination, -20°C to +50°C with MLI  
- **Structural**: Compliant with 6.5g axial, 9g lateral loads  

**Visual**: Budget tables, link budget chart  

**Speaker Notes**:  
- Present key analyses from PDD.  
- Emphasize margins (mass, power, link) ensure robustness.  
- Note simulations (MATLAB, STK) validate design.  

---

## Slide 11: Verification Plan
**Content**:  
- **Methods**: Analysis, simulation, test  
- **Key Verifications**:  
  - PLD-001: Bench test sensors  
  - ADCS-001: MATLAB simulation, Helmholtz coil test  
  - COM-001: Link budget, ground station test  
  - THM-001: MATLAB thermal model  
  - EPS-001: Solar panel/battery cycle test  
- **Test Plans**:  
  - ADCS: Bench test magnetorquers  
  - Communication: End-to-end with emulator  
  - Payload: Calibrate in lab  

**Visual**: Verification matrix  

**Speaker Notes**:  
- Explain how requirements will be verified.  
- Highlight early tests (bench, simulation) to reduce risk.  
- Note compliance with SRS requirements.  

---

## Slide 12: Risk Assessment
**Content**:  
- **Key Risks**:  
  | Risk | Likelihood | Impact | Mitigation |
  |------|------------|--------|------------|
  | Payload sensor failure | Low | High | Redundant sensors |
  | ADCS failure | Medium | Medium | COTS with flight heritage |
  | Comm interference | Medium | High | FCC frequency allocation |
  | Battery degradation | Low | High | Monitor charge cycles |
- **Mitigation**: COTS components, early testing, redundancy  

**Visual**: Risk matrix (likelihood vs. impact)  

**Speaker Notes**:  
- Acknowledge potential risks and mitigations.  
- Emphasize COTS and testing reduce technical risks.  
- Note regulatory coordination for communication.  

---

## Slide 13: Project Management
**Content**:  
- **Status**:  
  - Budget: $25,500 spent, $24,500 remaining ($50,000 limit)  
  - Team: Subsystem leads, ground station team, software team  
- **Milestones**:  
  - Detailed designs: August 2025  
  - Component procurement: September 2025  
  - Simulations: October 2025  
- **Resources**:  
  - Tools: MATLAB, STK, STM32CubeIDE  
  - Facilities: University lab, ground station  

**Visual**: Gantt chart or milestone timeline  

**Speaker Notes**:  
- Provide project status and resource overview.  
- Highlight budget and schedule margins.  
- Assure stakeholders of team readiness.  

---

## Slide 14: Next Steps
**Content**:  
- Finalize detailed subsystem designs (August 2025).  
- Procure COTS components (e.g., GomSpace, CubeSpace).  
- Conduct simulations (MATLAB for thermal, STK for orbit).  
- Develop ground station hardware/software.  
- Implement OBC software (FreeRTOS tasks).  
- Schedule Critical Design Review (CDR, November 2025).  

**Visual**: Roadmap graphic  

**Speaker Notes**:  
- Outline clear path forward post-PDR.  
- Emphasize parallel efforts (design, procurement, simulation).  
- Invite feedback to refine plans.  

---

## Slide 15: Q&A
**Content**:  
- **Title**: Questions & Discussion  
- **Text**: Thank you for attending the CanOrbitCubeSat-1 PDR!  
- **Visual**: CubeSat graphic or team photo  

**Speaker Notes**:  
- Open the floor for questions.  
- Be prepared to discuss technical details (e.g., component choices, analyses) or project concerns (e.g., budget, schedule).  
- Thank stakeholders for their support and feedback.