# Home Assistant Add-on: Aerohive Device Tracker

Author: Randy Hall [randy.hall@open-source.guru](mailto:randy.hall@open-source.guru)

## Features

- Easy deployment as a homeassistant add-on.
- All configuration is done within the config page of the add-on.
- Threaded operation that allows multiple access point to be queried concurrently.  This should scale well.  I see no difference in performance between one access point or 10 access points.
- Posts status and homeassistant discovery records to mqtt broker.
- Tracks clients by wireless connecton, not MAC address.  Wired devices will never be reported.
- Set regular expression exclusions based on IP, MAC, or hostname of wireless devices.
- Allow clients to be ignored if no reverse DNS is found.
- Configurable update interval and mqtt topic.
- Prefill mac client list with mac address before they are acutally seen allowing for a client's presense to be setup in advance and prevent a state of Unknown being reported for it.
- Retries when connections to the broker or the access points are dropped.
- Published attributes includes the AP were the client was associated.
- Discovery records are published published once on startup as a retained record and refreshed only if client details change while client is in a home state.
- State details are published every scan interval (default of 30s) for all clients the add-on as seen since it was started.  These records are not retained so a restart of homeassistant will only have to wait as long as the scan interval to see updated state.

## Options

| KEY                  | DEFAULT                 | DESCRIPTION                                                  |
| -------------------- | ----------------------- | ------------------------------------------------------------ |
| aerohive_host        |                         | Comma separated list of all aerohive devices in the hive to monitor.  This is a required field. |
| aerohive_username    | admin                   | Username of admin user on aerohive devices.                  |
| aerohive_password    |                         | Password of aerohive devices.  Assumes all devices in the same hive and therfore have the same password.  This is a required field. |
| mqtt_host            | localhost               | MQTT Broker                                                  |
| mqtt_port            | 1883                    | MQTT Port                                                    |
| mqtt_username        |                         | MQTT Username.  Defaults to assuming no auth required        |
| mqtt_password        |                         | MQTT Password. Defaults to assuming no auth required         |
| mqtt_topic           | device_tracker/aerohive | Where the records will be published on the broker.           |
| preinit_macs         |                         | Comma separated lists of lowercase macs in the format xx:xx:xx:xx:xx:xx. Prevents not_home devices from showing as Unavailable when addon is restarted.  Optional |
| ignore_regex_mac     | ^$                      | Regular expression to ignore MAC addresses. Optional         |
| ignore_regex_ip      | ^$                      | Regular expression to ignore IP addresses. Optionsl          |
| ignore_regex_name    | ^$                      | Regular expression to ignore device names. Optional          |
| ignore_unnamed_hosts | True                    | If a reverse DNS lookup of a client IP address does not return a name and this value is True, the client will be excluded from reporting. |
| sleep_interval       | 30                      | he number of seconds to wait between each scan and report cycle. |


## How to use

- setup a hive of aerohive AP in a mesh netowork using identical credentials for each.
- ensure all aerohive APs have static ip address
- Enter all ip addresses in config as a comma separated list
- Fill in credentials for aerohive devices
- optionally change the mqtt topic from device_tracker/aerohive
- optionally add a list of mac addresses to seed the tracker so that homeassistant will show not_home instead of unknown when the tracker restart and the device is not present.
- Setup an MQTT broker
- fill in mqtt broker connection info (unless localhost with no authentication will work)
- ensure the mqtt intergration is enabled in HA

## TODO

- determine neigbor aerohive APs automaticaly when the join or leave the hive
- Publish unavailable status when shutting down
- mqtt over SSL
- get system mqtt detail automaticly

