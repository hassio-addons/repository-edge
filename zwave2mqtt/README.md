# Home Assistant Community Add-on: Z-Wave to MQTT

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

[![Discord][discord-shield]][discord] [![Community Forum][forum-shield]][forum]

[![Sponsor Frenck via GitHub Sponsors][github-sponsors-shield]][github-sponsors]

[![Support Frenck on Patreon][patreon-shield]][patreon]

Fully configurable Z-Wave to MQTT gateway and control panel.

![Z-Wave to MQTT][logo]

## About

The Z-Wave to MQTT add-on allows you to decouple your Z-Wave network from
your Home Assistant instance by leveraging your MQTT broker. It ships with
a web-based control panel, allowing you to configure every aspect of your
Z-Wave network and how they are published in MQTT.

Some advantages and use-cases for this are:

- Your Z-Wave network will keep running between Home Assistant restarts.
- You can directly use things like Node-RED with your Z-Wave network, while
  it is available for Home Assistant at the same time.
- Allow [ESPHome.io][esphome] based ESP devices to directly respond or work
  with your Z-Wave network.

## WARNING! THIS IS AN EDGE VERSION!

This Home Assistant Add-ons repository contains edge builds of add-ons.
Edge builds add-ons are based upon the latest development version.

- They may not work at all.
- They might stop working at any time.
- They could have a negative impact on your system.

This repository was created for:

- Anybody willing to test.
- Anybody interested in trying out upcoming add-ons or add-on features.
- Developers.

If you are more interested in stable releases of our add-ons:

<https://github.com/hassio-addons/repository>

[discord-shield]: https://img.shields.io/discord/478094546522079232.svg
[discord]: https://discord.me/hassioaddons
[esphome]: https://esphome.io/components/mqtt.html#on-message-trigger
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg
[forum]: https://community.home-assistant.io/t/home-assistant-community-add-on-z-wave-to-mqtt/115899?u=frenck
[github-sponsors-shield]: https://frenck.dev/wp-content/uploads/2019/12/github_sponsor.png
[github-sponsors]: https://github.com/sponsors/frenck
[logo]: https://github.com/hassio-addons/addon-zwave2mqtt/raw/main/zwave2mqtt/logo.png
[maintenance-shield]: https://img.shields.io/maintenance/yes/2021.svg
[patreon-shield]: https://frenck.dev/wp-content/uploads/2019/12/patreon.png
[patreon]: https://www.patreon.com/frenck
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[release-shield]: https://img.shields.io/badge/version-33f02a4-blue.svg
[release]: https://github.com/hassio-addons/addon-zwave2mqtt/tree/33f02a4