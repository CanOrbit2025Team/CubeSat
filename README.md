# CanOrbitCubeSat Project
# CubeSat Project Repository

This repository contains documentation for the CanOrbit2025-1 CubeSat project.

## Folder Structure
- `docs/concept_and_mission_definition/`: Mission Concept, SRS, RRTA
- `docs/design_and_simulation/`: PDD, ICD, GSDD, SDD
- `docs/testing/`: Test plans and results
- `docs/launch_and_operations/`: Operations plans and logs
- `docs/presentations/`: PDR and future presentations
- `subsystems/`: Subsystem-specific design, test plans, and results

## Getting Started
- Clone the repository: `git clone <repository-url>`
- Install dependencies: [list any, e.g., Markdown viewer]
- Contribute: Follow the structure for new files.





### How to Customize and Use These Documents
1. **MCD**:
   - Update the mission name, objectives, and stakeholders to reflect your project (e.g., change payload to imaging if applicable).
   - Adjust orbit, CubeSat size (1U, 6U, etc.), and budget based on your constraints.
   - Refine the ConOps with specific operational modes or ground station details.
    - The MCD defines the mission’s goals and high-level architecture.
2. **SRS**:
   - Modify subsystem requirements to match your payload and mission goals (e.g., change sensor types, data rates, or pointing accuracy).
   - Update constraints (mass, power, budget) to reflect your project’s limits.
   - Ensure traceability links to your mission objectives.
   - The SRS and Refinement Document establish and validate detailed requirements.
3. **Refinement Document**:
   - Use as a template for subsystem team discussions to validate requirements.
   - Replace COTS examples with components you’re considering (e.g., specific vendors like Clyde Space or CubeSatShop).
   - Adjust trade-offs based on your team’s priorities (e.g., cost vs. reliability vs. performance).
   - Update mass, power budgets, and requirements for your subsystems.
   - The SRS and Refinement Document establish and validate detailed requirements. 

### Next Steps
- **Subsystem Team Kickoff**: Share the MCD and SRS with ADCS, Payload, Communication, Thermal, EPS, and OBC teams to align their work.
- **Workshops**: Use the Refinement Document to guide trade-off discussions and resolve inter-subsystem dependencies.
- **Simulation**: Begin basic simulations (e.g., orbit analysis with STK, or power modeling with MATLAB) to validate requirements.
- **Regulatory**: Contact regulatory bodies (e.g., FCC for UHF frequency allocation in the US) for compliance.
- **Funding**: Use the MCD to draft a proposal for sponsors or grants.


