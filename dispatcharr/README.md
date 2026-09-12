# Home Assistant Community App: Dispatcharr

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

[![Sponsor Frenck via GitHub Sponsors][github-sponsors-shield]][github-sponsors]

[![Support Frenck on Patreon][patreon-shield]][patreon]

Manage IPTV streams, EPG data and DVR recordings.

## About

[Dispatcharr][dispatcharr] takes the IPTV subscriptions you already have and
turns them into one tidy channel list. Point it at your providers and it pulls
in their playlists, works out which of the thousands of streams you actually
want, and puts them in the order you choose. Where the same channel comes from
several providers it keeps all of them and moves on to the next when one stops
working, so a dead stream is something it handles rather than something you
notice.

The guide is the other half. It matches your channels against XMLTV sources or
Schedules Direct, so what comes out has proper programme listings attached, and
a DVR that can record from them on a schedule.

What it hands back is a channel list every media player already understands. It
serves a playlist and a guide, and it pretends to be an HDHomeRun tuner, which
is how Plex, Emby and Jellyfin find it without being told anything beyond an
address.

## WARNING! THIS IS AN EDGE VERSION!

This Home Assistant Apps repository contains edge builds of apps.
Edge builds apps are based upon the latest development version.

- They may not work at all.
- They might stop working at any time.
- They could have a negative impact on your system.

This repository was created for:

- Anybody willing to test.
- Anybody interested in trying out upcoming apps or app features.
- Developers.

If you are more interested in stable releases of our apps:

<https://github.com/hassio-addons/repository>

[dispatcharr]: https://github.com/Dispatcharr/Dispatcharr
[github-sponsors-shield]: https://frenck.dev/wp-content/uploads/2019/12/github_sponsor.png
[github-sponsors]: https://github.com/sponsors/frenck
[maintenance-shield]: https://img.shields.io/maintenance/yes/2026.svg
[patreon-shield]: https://frenck.dev/wp-content/uploads/2019/12/patreon.png
[patreon]: https://www.patreon.com/frenck
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[release-shield]: https://img.shields.io/badge/version-2d9df5b-blue.svg
[release]: https://github.com/hassio-addons/app-dispatcharr/tree/2d9df5b