# Home Assistant Community App: SparkyFitness

[SparkyFitness][sparkyfitness] is a self-hosted alternative to MyFitnessPal.
It tracks what you eat, the exercise you do, how you sleep, your water intake
and your body measurements, and shows you where all of that is heading.

It looks food up in Open Food Facts, USDA and other databases, can scan a
barcode, and takes in the steps, workouts and sleep your phone collects through
its mobile app. It also has an AI assistant you can bring your own provider to,
which can log a meal from a photo or a sentence. Everything it keeps stays in
this app.

## Installation

The installation of this app is pretty straightforward and not different in
comparison to installing any other Home Assistant app.

1. Click the Home Assistant My button below to open the app on your Home
   Assistant instance.

   [![Open this app in your Home Assistant instance.][addon-badge]][addon]

1. Click the "Install" button to install the app.
1. Start the "SparkyFitness" app.
1. Check the logs of the "SparkyFitness" app to see if everything went well.
1. Click "Open Web UI" to open SparkyFitness.
1. Enjoy the app!

The first start takes a little longer than usual, because the database is
created from scratch and SparkyFitness sets up its tables in it. Every update
of the app does the latter again for whatever changed, so the first start
after an update takes a moment as well.

You are signed in automatically as your own Home Assistant user, so there is
nothing to log in with. SparkyFitness then asks a few questions about you, to
work out your calorie needs. You can skip those and fill them in later.

## How signing in works

Home Assistant has already established who you are by the time you open the
app from its sidebar, and it tells the app who that is. Every Home Assistant
user therefore gets a SparkyFitness account of their own, created the first
time they open the app. Nobody sees anybody else's diary, unless they give
each other access from within SparkyFitness, under "Settings" -> "Family
Access".

**The first person to open the app administers SparkyFitness.** Home Assistant
tells an app who is asking, but not whether that person administers Home
Assistant itself, so the app cannot work out who ought to hold that role. The
first arrival is the one it can name, and everybody after them is an ordinary
user. Open the app yourself before handing the link around, and you keep the
"Admin" tab. An administrator can promote others from there afterwards.

Accounts are tied to your Home Assistant user, not to your username, so
renaming yourself in Home Assistant keeps your data where it is. SparkyFitness
wants an email address for every account. You get one ending in
`@homeassistant.local`, named after your Home Assistant username where that
makes for a valid address. Nothing is ever sent to it. It is what family
members use to find you when you share your diary with them.

Only Ingress signs you in. The name is handed to SparkyFitness by the app's own
web server, which clears it on every other way in, and SparkyFitness itself
only listens inside the app. So the published port, if you publish it, cannot
be used to walk in as somebody else.

Signing out from within SparkyFitness signs you straight back in, since Home
Assistant still says it is you. To use SparkyFitness' own login instead, turn
off the `ingress_auto_login` option.

## Using the mobile app

SparkyFitness has [mobile apps][mobile] for Android and iOS. They log your
food and sync health data from your phone, like steps and workouts from Apple
Health or Health Connect.

The apps cannot use Home Assistant's address, since that only reaches the app
inside a Home Assistant session. To use them:

1. Publish the app's port `3004` in the "Network" section of the app's
   configuration, and restart the app.
1. In SparkyFitness, go to "Settings" -> "Developer & Integrations", and
   create an API key.
1. In the mobile app, add a server with the address
   `http://<your-home-assistant-ip>:<the port you published>`, and sign in
   with that API key.

Accounts made by Home Assistant have no password, so an API key is the way in
for them. Accounts you create with a password, over the published port or with
`ingress_auto_login` turned off, can sign in with that password as well.

Publishing the port makes SparkyFitness reachable to everything on your
network. Consider enabling the `ssl` option if you do. Keep in mind that
anybody who can reach it can create an account there too, unless you turn that
off, see "Option: `env_vars`" below.

## Connecting fitness services

Fitbit, Google Health, Oura, Polar, Strava and Withings are connected by
approving SparkyFitness on their own site, which then sends your browser back
to SparkyFitness. That way back has to be registered with them beforehand, in
the developer app you create there for yourself, and it has to be an address
your browser can reach.

The Ingress address Home Assistant uses behind the scenes cannot be that
address, since it is only valid inside a Home Assistant session. What can be,
is the page Home Assistant shows SparkyFitness on. So:

1. Set the `home_assistant_url` option to the address you open Home Assistant
   with, for example `https://homeassistant.example.com`, and restart the app.
1. In SparkyFitness, go to "Settings" -> "Developer & Integrations" -> "Food &
   Exercise Data Providers", and add the service. The form shows the address to
   register with it, which ends in something like
   `/app/a0d7b954_sparkyfitness/fitbit/callback`.
1. Register exactly that address in your developer app at the service, and
   click "Connect".

The service sends you back to Home Assistant, which opens SparkyFitness and
hands it the result. Connect services from the Home Assistant sidebar, so that
the account you come back to is the one you started from.

Pick the address you use most, since only one can be registered. If you reach
Home Assistant through several, like a local one and a Nabu Casa one, connect
services from the one you registered.

## Configuration

**Note**: _Remember to restart the app when the configuration is changed._

Example app configuration:

```yaml
ingress_auto_login: true
home_assistant_url: https://homeassistant.example.com
ssl: false
certfile: fullchain.pem
keyfile: privkey.pem
log_level: info
env_vars:
  - name: SPARKY_FITNESS_DISABLE_SIGNUP
    value: "true"
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

### Option: `ingress_auto_login`

Whether opening the app from the Home Assistant sidebar signs you in as your
own Home Assistant user. It defaults to `true`.

Left on, every Home Assistant user gets a SparkyFitness account of their own,
and the first one to open the app administers SparkyFitness. See "How signing
in works" above.

Set it to `false` to have SparkyFitness show its own login page instead, in
the sidebar and on the published port alike. The accounts Home Assistant made
stay where they are, but have no password to sign in with.

### Option: `home_assistant_url`

The address you open Home Assistant with, like
`https://homeassistant.example.com`. Only the scheme, host and port, without a
path.

It is only needed for connecting the fitness services that send your browser
back to SparkyFitness after you approve it on their site. See "Connecting
fitness services" above. Leave it out if you do not use those.

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the published port. Set it to `true` to enable
it, `false` otherwise.

This option has no effect on Ingress. Home Assistant handles the encryption of
Ingress connections.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

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

SparkyFitness logs every request it handles when set to `debug`. At `trace`,
it also writes out the health data it receives, heart rate series and GPS
tracks included, so only use that one for as long as you need it.

### Option: `env_vars`

SparkyFitness takes a number of settings from
[environment variables][sparkyfitness-env], which this app has no options of
its own for. This option sets any of them, as a list of `name` and `value`
pairs:

```yaml
env_vars:
  - name: SPARKY_FITNESS_DISABLE_SIGNUP
    value: "true"
  - name: SPARKY_FITNESS_EMAIL_HOST
    value: smtp.example.com
```

A few that are worth knowing about:

- `SPARKY_FITNESS_DISABLE_SIGNUP`: set to `true` to stop anybody from creating
  an account on the published port. Home Assistant users still get theirs.
- `SPARKY_FITNESS_EMAIL_HOST`, `SPARKY_FITNESS_EMAIL_PORT`,
  `SPARKY_FITNESS_EMAIL_USER`, `SPARKY_FITNESS_EMAIL_PASS` and
  `SPARKY_FITNESS_EMAIL_FROM`: an email server, for the accounts that have a
  real email address to send to.

The variables this app sets to make SparkyFitness work inside Home Assistant,
such as the database it uses, where it keeps its files and its secrets, win
over anything set here. The log only mentions the names of what you set, never
the values, since passwords end up here.

## Your data and backups

SparkyFitness keeps its data in a PostgreSQL database that comes with this app,
and which nothing outside of it can reach. Uploaded pictures sit next to it.
All of it is part of the app's data, and so part of every Home Assistant backup
that includes this app. The app is stopped for the moment such a backup is
taken, which is what makes the copy of the database in it consistent.

SparkyFitness can make backups of itself as well, from the "Admin" tab. Those
are kept inside the app's data too, and can be downloaded from there. They are
the way to move your data to a SparkyFitness that runs elsewhere, or back from
one. A Home Assistant backup is the simpler way to restore this app itself.

The encryption key SparkyFitness protects stored API keys with, and the secret
it signs sessions with, are made on the first start and kept with the rest of
the data. Restoring a Home Assistant backup brings them back along with
everything else. A backup made by SparkyFitness itself does not contain them,
so API keys for AI and fitness services have to be entered again after
restoring one into a different installation.

## Known issues and limitations

- Garmin Connect is not available. SparkyFitness talks to Garmin through a
  separate service of its own, which this app does not include.
- Links SparkyFitness sends by email, like a password reset or a magic link,
  and signing in with OpenID Connect or a passkey, do not work. They all need
  SparkyFitness to be reachable at an address of its own, outside of Home
  Assistant, which it is not. With Home Assistant signing you in, none of them
  are needed.
- Removing a Home Assistant user does not remove their SparkyFitness account.
  An administrator can do that from the "Admin" tab.
- The star count next to the logo stays at zero. SparkyFitness' own security
  policy stops the page from asking GitHub for it.

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
[addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=a0d7b954_sparkyfitness&repository_url=https%3A%2F%2Fgithub.com%2Fhassio-addons%2Frepository
[contributors]: https://github.com/hassio-addons/app-sparkyfitness/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord]: https://discord.me/hassioaddons
[forum]: https://community.home-assistant.io/c/community-add-ons/57
[frenck]: https://github.com/frenck
[mobile]: https://github.com/CodeWithCJ/SparkyFitness#readme
[issue]: https://github.com/hassio-addons/app-sparkyfitness/issues
[reddit]: https://reddit.com/r/homeassistant
[releases]: https://github.com/hassio-addons/app-sparkyfitness/releases
[semver]: https://semver.org/spec/v2.0.0.html
[sparkyfitness-env]: https://github.com/CodeWithCJ/SparkyFitness/blob/main/docs/src/install/environment-variables.md
[sparkyfitness]: https://github.com/CodeWithCJ/SparkyFitness
