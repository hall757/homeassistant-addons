# Home Assistant Add-on: Aerohive Device Tracker

## How to use

- setup a hive of aerohive AP in a mesh netowork using identical credentials for each.
- ensure all aerohive APs have static ip address
- Enter all ip addresses in config as a comma separated list
- Fill in credentials for aerohive devices
- optionally change the mqtt topic from device_tracker/aerohive
- optionally add a list of mac addresses to seed the tracker so that homeassistant will show not_home instead of unknown when the tracker restart and the device is not present.
- Setup an MQTT broker
- fill in mqtt broker connection info
- Sure the mqtt intergration is enabled in HA

## TODO:

- Filter macs or names
- Allow or filter devices with no reverse DNS
- Configurable interval
- Publish unavailable status when shutting down
- mqtt over SSL
- get system mqtt detail automaticly

