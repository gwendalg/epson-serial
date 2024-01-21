# Anthem Serial for Home Assistant

Custom Epson Serial component written in Python3 for Home Assistant. Controls older, serial based, [Epson] projector. Newer, IP based, projectors are controlled with [Epson](https://www.home-assistant.io/integrations/epson/) plugin.

## Supported features

- turn on/off
- set input

## Supported models

- [8350](https://epson.com/For-Home/Projectors/Home-Cinema/PowerLite-Home-Cinema-8350-1080p-3LCD-Projector/p/V11H373120)

[Anthem]: https://www.anthemav.com/

## Installation

1. Copy the custom_components folder to your own hassio /config folder.

2. A serial port is needed. When using a USB to serial dongle, it is recommeneded to use a udev rule, following this [tutorial](https://hackaday.io/project/183711-mks-tft28-with-klipper/log/202591-udev-rules). The USB port path as unique identifier is unique. In `/etc/udev/rules.d/98-local.rules`, add for instance:
```
ENV{ID_BUS}=="usb", ENV{ID_PATH_TAG}=="platform-3f980000_usb-usb-0_1_2_6_1_0", SYMLINK+="projector"
```

   A `/dev/projector` link is created by udev. Then the home assistant device section, add:

```yaml
- name: projector
  platform: epson_serial
  port: /dev/projector
```

   A `media_player.projector` object will be available for configuration.
