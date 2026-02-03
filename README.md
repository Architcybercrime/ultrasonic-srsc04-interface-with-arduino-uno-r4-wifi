# Ultrasonic Distance Sensor (Arduino Uno R4 WiFi)

This project measures distance using an HC-SR04 ultrasonic sensor connected to an `Arduino Uno R4 WiFi`. The main sketch is in `src/main.cpp`. Project configuration is stored in `platform.ini`.

## Hardware
- Arduino Uno R4 WiFi
- HC-SR04 ultrasonic sensor
- Jumper wires
- (Optional) Breadboard

Wiring (matches `src/main.cpp`):
- HC-SR04 VCC -> 5V
- HC-SR04 GND -> GND
- HC-SR04 TRIG -> digital pin `9`
- HC-SR04 ECHO -> digital pin `10`

Note: Verify voltage compatibility for the `ECHO` signal with your board. Use a level shifter or voltage divider if required.

## Behavior
- The sketch triggers the sensor, reads the echo pulse duration, converts it to distance (cm), and prints values to Serial at 9600 baud once per second.

## Files
- `src/main.cpp` — Arduino sketch that triggers the sensor and prints distance readings.
- `platform.ini` — Project configuration (board, framework, monitor speed). Edit this file to match your development environment.

Example `platform.ini` template (replace placeholders with your board/platform):

## Build & Upload

Using PlatformIO (recommended if `platform.ini` is present):
1. Set the correct `board`/`platform` in `platform.ini`.
2. Build: `pio run`
3. Upload: `pio run --target upload`
4. Monitor serial: `pio device monitor -b 9600`

Using Arduino IDE / CLI:
1. Open `src/main.cpp`.
2. Select `Arduino Uno R4 WiFi` and correct port.
3. Upload from the IDE, or with Arduino CLI:
   - Compile: `arduino-cli compile --fqbn <fqbn> .`
   - Upload: `arduino-cli upload -p <port> --fqbn <fqbn> .`
4. Open Serial Monitor at `9600` baud.

## Usage
1. Connect hardware as described above.
2. Upload the sketch.
3. Open Serial Monitor at 9600 baud to view distance measurements printed every second.

## Troubleshooting
- No readings: check wiring and sensor power.
- Incorrect distances: ensure correct pin assignments in `src/main.cpp` and that `ECHO` signal is read safely.
- Serial output missing: confirm `monitor_speed` / Serial Monitor is set to `9600`.

## License
MIT License
