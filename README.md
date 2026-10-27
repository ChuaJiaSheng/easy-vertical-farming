# Easy Vertical Farming

An M5Stack indoor-farming prototype with two complementary parts: environment/soil monitoring and button-controlled watering with a light indicator. The project demonstrates sensor inputs, on-device feedback, servo control, and timed interaction in UIFlow/Blockly.

**Stack:** M5Stack · UIFlow/Blockly · Earth and environment units · servo · light sensor · RGB unit

## Two project files

| Project | Purpose | Original port mapping |
| --- | --- | --- |
| [Project_Earth and Env.m5f](src/Project_Earth%20and%20Env.m5f) | Display environment and soil readings, with moisture alerts | Environment unit: A; Earth unit: B |
| [Project_Servo and Light.m5f](src/Project_Servo%20and%20Light.m5f) | Control watering and indicate low ambient light | Servo: A; light sensor: B; RGB unit: C |

These are separate UIFlow projects with different port assignments. The original presentation describes two M5Stack units for the combined demonstration. Do not connect both arrangements to one board using conflicting ports without adapting the design.

## Monitoring behaviour

The environment unit displays temperature, humidity, and pressure; the Earth unit supplies the soil-moisture reading. The presentation describes green feedback for acceptable moisture, orange with a beep for low moisture, and red with a beep for extremely low moisture. Review the Blockly comparisons and calibrate them for your sensor and soil before reuse.

## Watering controls

The original presentation documents the following controls:

| Action | Intended behaviour |
| --- | --- |
| Hold button A | Set the servo to 100 degrees to open the water flow |
| Release button A | Return the servo to 0 degrees |
| Press button B | Increase the selected watering time by 2 seconds |
| Press B and C together | Decrease the selected time by 2 seconds |
| Double-press C | Run the servo for the selected time |

The light sensor controls an RGB indication: purple when no light is detected and off otherwise. This is an indicator/prototype function, not evidence of a validated plant-growth lighting system.

## Open and test locally

1. Use a UIFlow environment compatible with the original `.m5f` project format and your M5Stack firmware.
2. Open one project from `src/` and review its unit types and port selections.
3. Connect matching hardware, inspect the Blockly events and thresholds, then transfer the project to the board.
4. First test readings, buttons, servo endpoints, and timer behaviour without water connected. Check the final mechanism separately.

The files are UIFlow/Blockly projects, not standalone Arduino sketches. The exact compatible firmware/editor combination has not been tested here.

## Demo references

The supplied [project-links.txt](docs/project-links.txt) records the original [Hackster project](https://www.hackster.io/500497/easy-vertical-farming-2922cc) and [YouTube demonstration](https://youtu.be/xN0PY6DzXPc). They are historical project references; their current availability has not been checked.

## Team and verification

The original Group 3 presentation names **Chua Yu Cheng, Chua Jia Sheng, and Pyie Sone Khaing Min**. The controls and hardware mapping above are drawn from that presentation and the supplied project files. Individual ownership of each subsystem is not asserted.

Both `.m5f` files parse as JSON. No firmware transfer, sensor calibration, watering, or hardware performance test has been performed here.
