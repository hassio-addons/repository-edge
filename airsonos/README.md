# Home Assistant Community Add-on: AirSonos

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

[![Discord][discord-shield]][discord] [![Community Forum][forum-shield]][forum]

[![Sponsor Frenck via GitHub Sponsors][github-sponsors-shield]][github-sponsors]

[![Support Frenck on Patreon][patreon-shield]][patreon]

AirPlay capabilities for your Sonos (and UPnP) players.

## About

Apple devices use AirPlay to send audio to other devices, but this is not
compatible with Sonos players. This add-on tries to solve this
compatibility gap.

It detects Sonos players in your network and creates virtual AirPlay
devices for each of them. It acts as a bridge between the AirPlay client
and the real Sonos device.

Since Sonos uses UPnP, the add-on might also work for other UPnP players
(e.g., newer Samsung televisions).

The AirCast add-on is based on the excellent [AirConnect][airconnect] project.

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

[airconnect]: https://github.com/philippe44/AirConnect
[discord-shield]: https://img.shields.io/discord/478094546522079232.svg
[discord]: https://discord.me/hassioaddons
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg
[forum]: https://community.home-assistant.io/t/home-assistant-community-add-on-airsonos/36796?u=frenck
[github-sponsors-shield]: https://frenck.dev/wp-content/uploads/2019/12/github_sponsor.png
[github-sponsors]: https://github.com/sponsors/frenck
[maintenance-shield]: https://img.shields.io/maintenance/yes/2025.svg
[patreon-shield]: https://frenck.dev/wp-content/uploads/2019/12/patreon.png
[patreon]: https://www.patreon.com/frenck
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[release-shield]: https://img.shields.io/badge/version-db88e52-blue.svg
[release]: https://github.com/hassio-addons/addon-airsonos/tree/db88e52