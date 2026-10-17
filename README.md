# PLC-Based Four-Floor Elevator Control Simulation

Shailesh Dhakal | Electrical Engineering | University of South Florida

A four-floor elevator simulation developed with ladder logic in Rockwell Automation Connected Components Workbench using the Allen-Bradley Micro850 simulator. The project combines state-based sequencing, stored floor requests, motion interlocks, fault diagnostics, and controlled recovery.

## Project Documentation

- [Complete Ladder Logic Documentation (PDF)](Elevator_Complete_Ladder_Logic_Documentation.pdf) — 77 rungs explained with 22 selected CCW screenshots in program order.
- [Project and Functional Testing Report (Word)](Elevator_Control_System_Project_Report%20%281%29.docx) — system architecture, test procedures, observed results, fault recovery, and troubleshooting.
- [CCW Solution File](Elevator_4Floor.ccwsln) — uploaded solution file; c

The rung document shows the implemented program; the testing report documents its tested behavior.

## Engineering Highlights

- Four-floor request handling with directional destination selection and a locked active target.
- Coordinated travel, door opening, timed dwell, and door closing.
- Door/motion interlocks and position validation.
- Latched fault codes for simulated emergency stop, invalid position, and travel timeout.
- Conditional reset followed by deliberate restart.
- 23 documented functional simulation checks.

## My Work

I developed the ladder logic, implemented the request and state handling, configured fault detection and recovery, and tested normal and abnormal operating conditions. During testing, I diagnosed a premature travel-watchdog timeout, increased the preset from 30 to 60 seconds, and repeated normal-operation and blocked-travel tests.

## Operating Sequence

Idle -> Travel -> Door Opening -> Door Dwell -> Door Closing -> Idle

Requests at the current floor initiate door service without travel. Additional calls during a trip are stored for later service rather than changing the active destination.

Normal Stop pauses the active trip while retaining its request and destination. A fault disables operation, clears requests, and requires an allowed reset followed by a fresh Start command.

## Testing

The project report documents 23 checks covering floor feedback, upward/downward travel, stored and additional requests, door operation, pause/resume, injected faults, blocked reset, and deliberate restart. All listed checks passed after the documented corrections. Several checks were performed within the same run.

## Tools

Connected Components Workbench | Allen-Bradley Micro850 Simulator | Ladder Logic

## Project Scope

This is an educational software simulation with simulated position and door feedback. It does not include physical elevator hardware, commissioned I/O, a completed HMI, or a safety-rated emergency-stop system.
