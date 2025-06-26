# EPS Test Plan\n## Overview\nThis document details the test plan for the EPS subsystem.\n## Next Steps\n- To be developed during testing phase.
# EPS Test Plan
## Overview
This document details the test plan for the Electrical Power System (EPS) of the CanOrbitCubeSat-1 3U CubeSat, ensuring 10 W RMS power generation and 20 Wh battery capacity.

## Test Objectives
- Verify 10 W RMS power output.
- Confirm 20 Wh battery charge/discharge cycle.
- Validate 3.3V/5V power rails.

## Test Methods
- **Solar Simulation**: Use solar simulator for panel testing.
- **Battery Test**: Cycle charge/discharge under load.
- **Integration Test**: Test within CubeSat stack.

## Test Procedures
1. **Setup**:
   - Connect solar panels to simulator.
   - Attach battery to EPS board.
2. **Execution**:
   - Simulate 60% orbit illumination.
   - Measure power output and rail voltages.
   - Cycle battery (20 Wh).
3. **Validation**:
   - Compare against EPS-001 (power requirement).

## Test Equipment
- Solar simulator
- Multimeter
- Battery analyzer

## Schedule
- **Start Date**: September 1, 2025
- **Completion Date**: September 15, 2025
- **Duration**: 2 weeks

## Success Criteria
- Power output ≥ 10 W RMS.
- Battery capacity ≥ 20 Wh.
- Rail voltages 3.3V ±0.1V, 5V ±0.1V.

## Risks and Mitigation
- **Risk**: Panel degradation.
  - **Mitigation**: Test new panels, monitor output.
- **Risk**: Overcharge.
  - **Mitigation**: Use EPS safety cutoffs.

## Next Steps
- Procure simulator by August 15, 2025.
- Conduct preliminary tests by August 25, 2025.
- Update with integration test results.

## Revision History
| Version | Date             | Changes             |
|---------|------------------|---------------------|
| 1.0     | 2025-06-19 14:09 | Initial placeholder |