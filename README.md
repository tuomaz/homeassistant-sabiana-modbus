# Home Assistant Sabiana Fan Coil Integration

A custom Home Assistant integration to control and monitor Sabiana fan coil units over Modbus RTU Serial. 

This integration features dynamic schema auto-detection to support both standard Cassette/Fancoil models (Schema A) and CVP/QCV models (Schema B). It has been tested on a **Sabiana Carisma Fly CVP-ECM-MB 4** unit, but should theoretically work on other compatible Sabiana units.



## Features
- **Climate Entity (`climate.sabiana`)**:
  - Exposes `off`, `cool`, `heat`, `fan_only`, and `auto` modes.
  - Temperature setpoint control (automatically targets the Summer setpoint `102D` or Winter setpoint `102E` based on the active season).
  - Fan speed control (`auto`, `low`, `medium`, `high`).
  - Real-time ambient air temperature (`T1`).
- **Diagnostic Sensors (`sensor.sabiana_*`)**:
  - **Ambient Air Temperature (`T1`)**
  - **Coil Water Temperature (`T2`)** (automatically reports `Unavailable` when T2 probe is not connected)
  - **Minimum Probe Temperature (`T3`)** (automatically reports `Unavailable` when T3 probe is disabled via DIP 3)
  - **Board Power-On Time** (hours)
  - **Machine On Time** (hours)
  - **T-MB Wall Controller Present** (Yes/No)
  - **IR Receiver Present** (Yes/No)
  - **Slave/Master Mode** (Slave/Master)
- **Binary Sensors (`binary_sensor.sabiana_*`)**:
  - **T1 Sensor Fault**
  - **T2 Sensor Fault**
  - **T3 Sensor Fault**
  - **Condensation Alarm**
  - **T2 Probe Connected**
  - **T3 Probe Enabled**

## Installation

### Via HACS (Recommended)
1. Open **HACS** in Home Assistant.
2. Add `https://github.com/tuomaz/homeassistant-sabiana-modbus` as a custom repository (Category: **Integration**).
3. Install **Sabiana Fan Coil** and restart Home Assistant.

### Manual Installation
1. Copy the `custom_components/sabiana` directory into your Home Assistant `config/custom_components/` folder.
2. Restart Home Assistant.
3. Go to **Settings -> Devices & Services -> Add Integration** and search for `Sabiana Fan Coil`.
4. Enter your connection settings:
   - **Serial Port:** (e.g., `/dev/sabiana`)
   - **Baud Rate:** 9600 (default)
   - **Modbus Slave Address (Unit ID):** 1 (default)
   - **Polling Interval (seconds):** 30 (default)


