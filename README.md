# Easy Vertical Farming

An M5Stack indoor-farming prototype with two complementary parts: environment/soil monitoring and button-controlled watering with a light indicator. The project demonstrates sensor inputs, on-device feedback, servo control, and timed interaction in UIFlow/Blockly.

**Stack:** M5Stack · UIFlow/Blockly · Earth and environment units · servo · light sensor · RGB unit

## Two project files

| Project | Purpose | Port mapping |
| --- | --- | --- |
| [Project_Earth and Env.m5f](src/Project_Earth%20and%20Env.m5f) | Display environment and soil readings, with moisture alerts | Environment unit: A; Earth unit: B |
| [Project_Servo and Light.m5f](src/Project_Servo%20and%20Light.m5f) | Control watering and indicate low ambient light | Servo: A; light sensor: B; RGB unit: C |

These are separate UIFlow projects with different port assignments. The combined demonstration uses two M5Stack units. Do not connect both arrangements to one board using conflicting ports without adapting the design.

## Monitoring behaviour

The environment unit displays temperature, humidity, and pressure; the Earth unit supplies the soil-moisture reading. Moisture feedback is green for acceptable moisture, orange with a beep for low moisture, and red with a beep for extremely low moisture. Review the Blockly comparisons and calibrate them for your sensor and soil before reuse.

## Watering controls

The watering controls are:

| Action | Intended behaviour |
| --- | --- |
| Hold button A | Set the servo to 100 degrees to open the water flow |
| Release button A | Return the servo to 0 degrees |
| Press button B | Increase the selected watering time by 2 seconds |
| Press B and C together | Decrease the selected time by 2 seconds |
| Double-press C | Run the servo for the selected time |

The light sensor controls an RGB indication: purple when no light is detected and off otherwise. This is an indicator/prototype function, not evidence of a validated plant-growth lighting system.

## Reproduce the UIFlow projects

**Required hardware:** M5Stack controllers compatible with these projects, environment and Earth units, a compatible servo/watering mechanism, light sensor, RGB unit, cables, and an appropriate power supply. The two port maps above are different; use two controllers for the combined arrangement or load/test one arrangement at a time.

```sh
git clone https://github.com/ChuaJiaSheng/easy-vertical-farming.git
cd easy-vertical-farming
```

1. Open a UIFlow editor that supports importing the original `.m5f` format. Import `src/Project_Earth and Env.m5f` for monitoring, or `src/Project_Servo and Light.m5f` for watering.
2. Match the editor's unit selections and physical connections to the corresponding port table. Select/connect the intended controller and transfer the project using that UIFlow setup.
3. For monitoring, check that temperature, humidity, pressure, and soil readings appear. Compare dry and moist soil readings; the moisture indicators should change according to the Blockly thresholds.
4. For watering, first leave the water supply disconnected. Hold/release A to check the two servo positions. Press B to increase the displayed time, B+C to decrease it, and double-press C to check timed motion.
5. Cover/uncover the light sensor to check the purple/off RGB behaviour. Connect and test the water mechanism only after verifying servo travel and timing.

**Expected result:** the monitoring project displays sensor readings; the watering project changes the timer and servo position in response to the controls above. These checks require matching hardware and firmware.

**Reproduction limits:** the exact original controller revision, UIFlow editor/firmware release, sensor calibration, power arrangement, and water-valve construction are not fully specified in the repository. Match these to your hardware before attempting the full physical build. A failed import can indicate an incompatible editor format rather than corrupt source. The files are UIFlow projects, not Arduino sketches.

## Demo references

- [Hackster project](https://www.hackster.io/500497/easy-vertical-farming-2922cc)
- [YouTube demonstration](https://youtu.be/xN0PY6DzXPc)
- [Project links](docs/project-links.txt)

## Team

Chua Yu Cheng, Chua Jia Sheng, and Pyie Sone Khaing Min — Group 3.
