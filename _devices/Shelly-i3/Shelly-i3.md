---
title: Shelly i3
date-published: 2020-09-24
type: switch
standard: uk, us, eu
---

1. TOC
   {:toc}

## GPIO Pinout

| Pin    | Function |
| ------ | -------- |
| GPIO12 | Relay    |
| GPIO13 | Relay    |
| GPIO14 | Relay    |

## Basic Configuration

Since the Shelly i3 has floating inputs there needs to be a delayed_on_off present. 50ms should be sufficient.

```yaml
# Basic Config
substitutions:
  devicename: shelly_i3

esphome:
  name: ${devicename}
  platform: ESP8266
  board: esp01_1m

wifi:
  ssid: !secret ssid1
  password: !secret ssid1_pass

# Enable logging
logger:

# Enable Home Assistant API
api:

ota:

# Device Specific Config
binary_sensor:
  - platform: gpio
    pin:
      number: GPIO12
      mode: INPUT
    name: ${devicename} Switch 1
    filters:
      - delayed_on_off: 50ms
  - platform: gpio
    pin:
      number: GPIO13
      mode: INPUT
    name: ${devicename} Switch 2
    filters:
      - delayed_on_off: 50ms
  - platform: gpio
    pin:
      number: GPIO14
      mode: INPUT
    name: ${devicename} Switch 3
    filters:
      - delayed_on_off: 50ms
```
