# KosselXL-DIY

DIY Delta 3D printer build based on a Kossel XL frame, upgraded with a BigTreeTech Manta M8P controller and Klipper firmware.

This repository documents the machine configuration, parts, and setup process.

## Project Goals

- Rebuild and modernize a classic Kossel XL style Delta printer.
- Use a modern 32-bit control board (BigTreeTech Manta M8P).
- Run Klipper for better kinematics handling and easier tuning.
- Keep the project open and easy to reproduce.

## Hardware Overview

- Frame type: Delta (Kossel XL style)
- Mainboard: BigTreeTech Manta M8P
- Firmware stack: Klipper + Moonraker + Mainsail
- Configuration files: located in `Klipper/`

Current Klipper configs in this repository:

- `Klipper/printer.cfg`
- `Klipper/mainsail.cfg`
- `Klipper/moonraker.conf`
- `Klipper/user_macros.cfg`
- `Klipper/sonar.conf`
- `Klipper/timelapse.cfg`

## Repository Structure

- `Klipper/`: machine and service configuration for Klipper stack
- `Blender/`: 3D model related files and notes
- `Parts/`: printable or mechanical part references

## Recommended Build and Setup Flow

1. Assemble frame, towers, linear motion system, and effector.
2. Install the Manta M8P and wire all components:
   - stepper motors
   - endstops
   - hotend heater and thermistor
   - bed heater and thermistor (if heated bed is used)
   - part cooling and hotend fans
   - probe/sensor (if installed)
3. Install Klipper host software (typically on a Raspberry Pi or similar Linux SBC).
4. Flash Klipper firmware to the Manta M8P.
5. Copy and adapt config files from `Klipper/` to your active Klipper config folder.
6. Verify motion direction and endstop logic before any homing test.
7. Run Delta calibration and then print tuning.

## Safety Checklist (Before First Heat or Motion)

- Confirm correct PSU voltage and grounding.
- Check all heater and thermistor ports carefully.
- Validate max temperature limits in config.
- Test endstops with `QUERY_ENDSTOPS` before homing.
- Keep one hand near power-off during first movement tests.
- Never leave first thermal tests unattended.

## Delta Calibration Checklist

After basic axis movement is verified:

1. Home the printer safely.
2. Set rough geometry values (arm length, radius, endstop positions).
3. Run Klipper Delta calibration routine.
4. Re-check first layer consistency across the full bed area.
5. Tune extrusion and temperature for your filament.

## Software and Service Notes

This project uses:

- Klipper for motion control
- Moonraker for API/service layer
- Mainsail as web UI

Service-specific configuration lives in the `Klipper/` folder and can be adapted to your environment.

## Status

Work in progress.

Planned additions:

- Wiring diagram for Manta M8P pin mapping
- BOM with exact part numbers
- Step-by-step commissioning logs
- Known-good slicer profiles

## License

See `LICENSE` for license details.

## Credits

40mm Fan Guard by Prot0typ1cal https://www.thingiverse.com/thing:1662879
