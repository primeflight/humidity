# 💧 Humidity Sensor — DHT11 + Arduino Uno

Digital humidity and temperature display with a **gauge-style** visualization, reading data from the DHT11 sensor via serial and rendering in real-time in the browser.

![Humidity Gauge](screenshot.png)

## Hardware

| Component | Wiring |
|---|---|
| **DHT11** | VCC→5V, GND→GND, DATA→D2 |
| **Arduino Uno R3** | Connected via USB |

## Software

- **Arduino sketch** (`humidity.ino`): reads the DHT11 and sends JSON over serial every 2 seconds
- **Web page** (`humidity.html`): circular gauge with humidity percentage and temperature — uses **Web Serial API** (Chrome/Edge)

## Usage

1. **Upload the sketch** to the Arduino:
   ```bash
   arduino-cli compile --fqbn arduino:avr:uno humidity
   arduino-cli upload -p /dev/ttyACM0 --fqbn arduino:avr:uno humidity
   ```

2. **Open** `humidity.html` in Chrome or Edge

3. **Click "Connect"** and select the Arduino serial port

4. **Watch** the gauge update with humidity and temperature readings

## Data format

```json
{"h":45.0,"t":23.5}
```

| Field | Description |
|---|---|
| `h` | Humidity in % (0-100) |
| `t` | Temperature in °C |

## Structure

```
humidity/
├── humidity.ino    # Arduino sketch (DHT11 → Serial JSON)
├── humidity.html   # Gauge web page (Web Serial API → Canvas)
├── screenshot.png  # Gauge screenshot
└── README.md       # This file
```
