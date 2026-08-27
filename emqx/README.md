# Home Assistant Community App: EMQX

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

[![Sponsor Frenck via GitHub Sponsors][github-sponsors-shield]][github-sponsors]

[![Support Frenck on Patreon][patreon-shield]][patreon]

The most scalable MQTT broker for IoT, IIoT, and connected vehicles.

## About

[EMQX][emqx] is an MQTT broker with a high-performance real-time message
processing engine, powering event streaming for IoT devices at massive scale.
As the most scalable MQTT broker, EMQX can help you connect any device, at any
scale (including your home).

The [EMQX MQTT broker][emqx] is an advanced alternative to the Mosquitto MQTT
broker/app that is generally used in Home Assistant. It has a UI
to configure, manage, and debug your MQTT broker, clients, and traffic.

While EMQX sells their product mainly as a cloud hosted product on their
website, this app runs EMQX in a fully local, self-hosted environment.

As of version 5.9.0, EMQX is no longer open source; it is licensed under the
[Business Source License 1.1][emqx-license]. The build shipped here carries the
EMQX Community License, which is free of charge and allows running a single
node, which is exactly what this app does. Clustering requires a commercial
license.

![EMQX in the Home Assistant Frontend][screenshot]

## WARNING! THIS IS AN EDGE VERSION!

This Home Assistant Apps repository contains edge builds of apps.
Edge builds are based upon the latest development version.

- They may not work at all.
- They might stop working at any time.
- They could have a negative impact on your system.

This repository was created for:

- Anybody willing to test.
- Anybody interested in trying out upcoming apps or app features.
- Developers.

If you are more interested in stable releases of our apps:

<https://github.com/hassio-addons/repository>

[emqx-license]: https://github.com/emqx/emqx/blob/main/LICENSE
[emqx]: https://www.emqx.io/
[github-sponsors-shield]: https://frenck.dev/wp-content/uploads/2019/12/github_sponsor.png
[github-sponsors]: https://github.com/sponsors/frenck
[maintenance-shield]: https://img.shields.io/maintenance/yes/2026.svg
[patreon-shield]: https://frenck.dev/wp-content/uploads/2019/12/patreon.png
[patreon]: https://www.patreon.com/frenck
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[release-shield]: https://img.shields.io/badge/version-675310e-blue.svg
[release]: https://github.com/hassio-addons/addon-emqx/tree/675310e
[screenshot]: https://github.com/hassio-addons/app-emqx/raw/main/images/screenshot.png