# ESPHome Configurations

This repository contains various ESPHome configurations for ESP32-based IoT devices. Each YAML file represents a different device configuration with specific functionalities.

## Projects

### Blink Configuration (`blink.yaml`)
A simple LED blink controller with adjustable intervals.

Features:
- Web server interface
- Adjustable blink interval (5-120 seconds)
- MQTT integration for availability reporting
- GPIO-controlled LED on pin 2
- OTA updates support

### Dallas Temperature Sensor (`dallas.yaml`)
Temperature monitoring system using Dallas temperature sensors.

Features:
- Dual temperature sensor support
- High precision readings (3 decimal accuracy)
- Web interface
- MQTT integration
- OneWire communication on GPIO4

### Moisture and Humidity Monitor (`moisture-humidity.yaml`)
DHT sensor-based temperature and humidity monitoring with power-saving features.

Features:
- DHT sensor integration on GPIO02
- Deep sleep support (15 minute intervals)
- Static IP configuration
- MQTT control for OTA and sleep modes
- Temperature and humidity reporting

## Setup Requirements

- ESPHome installed
- ESP32 development board
- WiFi network
- MQTT broker (configured at 192.168.2.50)

## Configuration

### WiFi Setup
Create a `secrets.yaml` file in your ESPHome configuration directory with the following:

```yaml
WifiSsid: "your_wifi_ssid"
WifiPassword: "your_wifi_password"
apWifiPassword: "your_ap_password"
```

### MQTT Setup
The MQTT broker is configured at 192.168.2.50. Update the broker address in the YAML files if your setup differs.

## Usage

To flash a configuration to a device:

```bash
esphome <config-file>.yaml run
```

Example:
```bash
esphome moisture-humidity.yaml run
```

## Features

### Deep Sleep Support
The moisture-humidity configuration includes deep sleep functionality:
- Run duration: 30 seconds
- Sleep duration: 15 minutes
- Can be controlled via MQTT topics:
  - `esphome/moisture-humidity/ota_mode`
  - `esphome/moisture-humidity/sleep_mode`

### Web Interface
All configurations include a web interface accessible at:
- `http://<device-ip>`
- Default port: 80

### OTA Updates
All devices support Over-The-Air updates through ESPHome.

## Troubleshooting

If WiFi connection fails:
1. Device will create a fallback access point
2. Connect to the AP (check individual config for SSID)
3. Use the captive portal to configure WiFi settings

## Pin Assignments

- Blink Configuration: LED on GPIO2
- Dallas Temperature: OneWire bus on GPIO4
- Moisture-Humidity: DHT sensor on GPIO02

## Contributing

Feel free to submit issues and enhancement requests!
