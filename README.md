Stage 1: Temperature Simulation + Setpoint Control

The first stage of the HVAC building automation control system, simulates a zone temperature that drifts over time and implements setpoint/deadband control logic to determine heating and cooling demand. The simulated passive drift model is a control loop that self-oscillates around the setpoint without manual input, this demonstrates a realistic closed-loop thermostat behavior in a simulation without physical hardware.

Skills demonstrated: Analog (REAL) variable simulation, setpoint/deadband control logic, timer-based simulation loops (TON), foundational logic for the multi-stage HVAC system that follows (damper/fan control, alarms, OPC-UA exposure)

Stage 2: Damper and Fan Control

Extends Stage 1's setpoint control loop with proportional actuator control. Added two function blocks, FB_Damper and FB_Fan, translate binary heat/cool demand signals into simulated analog actuator positions (0-100%), ramping gradually rather than snapping instantly, to represent realistic physical actuator movement. The damper opens for outside air cooling demand, and the fan runs at operating speed whenever heating or cooling is active, both ramping down to idle when demand clears.

Skills demonstrated: Function block design for analog/proportional actuator control, simulated ramp-rate behavior, modular integration of multiple function blocks into a single coordinated control loop

Stage 3: Alarms and Fault Detection

Adds process alarm monitoring to the HVAC control loop via a dedicated FB_AlarmMonitor function block, detecting high and low temperature excursions and simulated sensor faults. Alarms latch on when a condition occurs and remain active until an operator acknowledges the fault, even if the underlying condition has since cleared, standard alarm management practice that ensures transient issues aren't silently missed. It reuses the latched fault/reset pattern first developed for the e-stop logic in the earlier safety=interlock project, applied here to process-level alarming rather than safe-critical shutdown.

Skills demonstrated: Alarm latching and operator-acknowledge logic, rising-edge detection (R_TRIG) for acknowledge/reset actions, reapplying a proven safety-interlock pattern to a new domain (process alarms), function block composition within a growing cumulative control system.
