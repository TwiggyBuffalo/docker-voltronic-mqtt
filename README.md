# MQTT interface for Voltronic (aka Phocos, MPPSolar, Axpert, Powland, EASun, etc) solar inverters.

This project is based on the original work by lavron and is configured specifically for the Phocos PSW-H inverter.

### Motivation
I wanted to get my inverter values into Home Assistant for monitoring and automation.
To do that, I used an RS232-to-Serial adapter and then a Serial-to-USB adapter so the inverter data could be read and published to MQTT for Home Assistant.


Supports protocols PI30 and PI41 devices.

### Exposed sensors:
- Inverter status
- grid_voltage (V)
- grid_frequency (Hz)
- AC output voltage (V)
- AC output frequency (Hz)
- AC output apparent power (VA)
- output_load_watt (W)
- output_load_percent (%)
- bus_voltage (V)
- battery_voltage (V)
- battery_charge_current (A)
- battery_capacity (%)
- heatsink_temperature (°C)
- PV input current (A)
- pv_input_voltage (V)
- PV input watt (W)
- Warnings
### How to run
Change credentials to your MQTT server and USB port in the command below and run it.
```bash
docker run -t -i --privileged -v /dev:/dev --restart=always --name voltronic-mqtt --pull=always -e \
MQTT_PASSWORD='your_password' -e \
MQTT_SERVER='your_server' -e \
MQTT_USER='your_username' -e \
SERIAL_PORT='/dev/ttyUSB0' \
twiggybuffalo/voltronic-mqtt:latest
```

### Home Assistant users
Copy the content of 'ha-sensors.yaml' to your 'configuration.yaml' file. Edit as needed.

### Aditional protocols and sensors
Please check [this discussion](https://github.com/lavron/docker-voltronic-mqtt/discussions/5).

### Upstream source
Original project by lavron:
https://github.com/lavron/docker-voltronic-mqtt

