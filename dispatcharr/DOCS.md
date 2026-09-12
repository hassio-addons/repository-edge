# Home Assistant Community App: Dispatcharr

[Dispatcharr][dispatcharr] takes the IPTV subscriptions you already have and
turns them into one tidy channel list, with a proper programme guide attached
and a DVR that can record from it.

What it hands back is a channel list every media player already understands. It
serves a playlist and a guide, and it pretends to be an HDHomeRun tuner, which
is how Plex, Emby and Jellyfin find it without being told anything beyond an
address.

## Installation

The installation of this app is pretty straightforward and not different in
comparison to installing any other Home Assistant app.

1. Click the Home Assistant My button below to open the app on your Home
   Assistant instance.

   [![Open this app in your Home Assistant instance.][addon-badge]][addon]

1. Click the "Install" button to install the app.
1. Start the "Dispatcharr" app.
1. Check the logs of the "Dispatcharr" app to see if everything went well.
1. Click "Open Web UI" to create your account.

## Logging in for the first time

The first time you open this app there are no accounts yet, and it asks you to
make one. That account is an administrator, and it is what guards everything
this app serves from that point on.

Do this before you publish anything. Until an account exists, anybody who can
reach this app can claim the first one.

## The port, and why you need it

Ingress, the "Open Web UI" button and the sidebar entry, is for browsers. It is
the comfortable way to sit down and sort out your channels, and it needs no
port published and no password beyond the one you already use for Home
Assistant.

It is not how anything watches television. An Ingress address is tied to a
browser session and authenticated by Home Assistant, so a set top box, a phone
app or a media server can do nothing with it. That is what port `9191` is for,
and unlike most apps here it is published from the start, because an app that
serves streams is not much use with it closed.

The interface knows about this. The playlist, guide and HDHomeRun addresses it
shows you are always built from the address on your network, never from the
Ingress path, whichever way you happen to be looking at it. Copy them and they
work.

If this app sits behind a reverse proxy, or you reach it by a name rather than
an address, tell it so with the [`base_url`](#option-base_url) option.

### Plex, Emby and Jellyfin

These discover this app as an HDHomeRun tuner, which they all support out of
the box as a live television source.

1. Copy the HDHomeRun address from the channels page.
1. In Plex, Emby or Jellyfin, add a live TV source and choose the HDHomeRun
   option.
1. Paste the address.
1. For the guide, choose the XMLTV option and paste the guide address from the
   same page.

### Everything else

Players like VLC, TiviMate and IPTV Smarters take a playlist address instead.
Copy the M3U address from the channels page, and the guide address alongside it
if the player has somewhere to put one.

## Hardware acceleration

Turning one video format into another is the most expensive thing this app
does, and a graphics chip does it far better than a processor. An Intel or AMD
GPU shows up as `/dev/dri`, and this app is given access to it automatically.

Whether it gets used is up to the stream profile you pick in the interface: the
profiles that ask FFmpeg for VA-API are the ones that reach the GPU.

**Note**: _NVIDIA cards are not supported here. They need drivers on the host
and a container runtime that hands the card over, neither of which is something
an app can arrange for itself._

## Recording

The DVR writes to `/data` inside this app by default, which is backed up along
with everything else and is fine for the occasional recording.

For anything more, point it at `/media` in the DVR settings. That is the same
folder the media browser and apps like Jellyfin, Sonarr and Radarr use, so a
recording lands somewhere the rest of your house can already see. `/share` is
available too.

Recordings under `/media` and `/share` are not part of this app's backups,
which is deliberate: an app backup is not the place for hours of video.

## Configuration

Example app configuration:

```yaml
log_level: info
base_url: http://192.168.1.10:9191
ssl: false
certfile: fullchain.pem
keyfile: privkey.pem
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

### Option: `log_level`

The `log_level` option controls the level of log output by the app and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`: Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. App becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

### Option: `base_url`

The address everything outside Home Assistant reaches this app at, for example
`http://192.168.1.10:9191`. It is what the playlist, guide and HDHomeRun links
shown in the interface are built from.

Leave it empty and this app works the address out from your network, which is
the right answer for the ordinary case of a machine on your own network. Set it
when that is not where things should be pointed: a reverse proxy in front of
this app, or a name you reach it by rather than an address.

### Option: `ssl`

Enables/Disables encrypted SSL (HTTPS) for direct access to the app.

**Note**: _This has no effect on the Ingress service, which is always
encrypted by Home Assistant. It only applies to port `9191`._

Set it to `true` to encrypt, `false` otherwise. Leave it off when something
else in front of this app, such as the [NGINX Proxy Manager app][nginx-proxy-manager],
is already terminating the encryption.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

## Known quirks

- The Django administration interface is not reachable. This app has its own
  user management on the users page, and a second, separate way in is not
  something worth leaving open.

- The "ML enhanced" option for matching channels to guide data does nothing.
  It is built on PyTorch, which is around two gigabytes of machine learning
  libraries for one optional pass over a list of channel names, so it is left
  out. The ordinary matching, which is what does the work in almost every case,
  is unaffected.

- The database is PostgreSQL, kept inside this app under `/data`, and it is not
  reachable from anywhere else. There is nothing to set up and nothing to
  point at it. Backups of this app include it, and because the app is stopped
  while a backup is taken, what comes out is consistent.

  PostgreSQL cannot read a database written by a different major version of
  itself, so this app checks before it starts and stops with an explanation
  rather than trying to convert one quietly. Nothing here changes the major
  version on its own: when it does eventually change, that is a release of
  this app with the steps written in its notes.

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality.

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Community Apps Discord chat server][discord] for app
  support and feature requests.
- The [Home Assistant Discord chat server][discord-ha] for general Home
  Assistant discussions and questions.
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

You could also [open an issue here][issue] GitHub.

## Authors & contributors

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License

MIT License

Copyright (c) 2026 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[addon-badge]: https://my.home-assistant.io/badges/supervisor_addon.svg
[addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=a0d7b954_dispatcharr&repository_url=https%3A%2F%2Fgithub.com%2Fhassio-addons%2Frepository
[contributors]: https://github.com/hassio-addons/app-dispatcharr/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord]: https://discord.me/hassioaddons
[dispatcharr]: https://github.com/Dispatcharr/Dispatcharr
[forum]: https://community.home-assistant.io/t/?u=frenck
[frenck]: https://github.com/frenck
[issue]: https://github.com/hassio-addons/app-dispatcharr/issues
[nginx-proxy-manager]: https://github.com/hassio-addons/app-nginx-proxy-manager
[reddit]: https://reddit.com/r/homeassistant
[releases]: https://github.com/hassio-addons/app-dispatcharr/releases
[semver]: https://semver.org/spec/v2.0.0.html
