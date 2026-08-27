# Changelog since v0.23.0
- 👷 Replace Repology with Alpine CDN datasource for package pins (#606)

Renovate's repology datasource has stopped resolving Alpine package
pins across the organisation. Every alpine_X_YY/* lookup returns
no-result, so Alpine pins are no longer updated at all, and builds break
whenever upstream moves a pinned package. Repology rate limits its
tools/project-by endpoint hard, and each run resolves every pin through
it.

This replaces it with a custom datasource that reads the Alpine CDN
directory listings directly, matching what has already landed on
app-ssh.

Packages from the community repository need an explicit registry URL,
since custom datasources use a "first" registry strategy and do not hunt
through multiple URLs. For this repository that is ffmpeg, ffmpeg-dev,
ffmpeg-libs, v4l-utils and v4l-utils-dev. 
- ⬆️ Update motioneye-project/motioneye to v0.44.0 (#587)

* ⬆️ Update motioneye-project/motioneye to v0.44.0

* 🐛 Fix startup failure from hardcoded Python path

The init script referenced motionEye's migrateconf.sh through a
hardcoded /usr/lib/python3.12 path. Alpine 3.24 ships Python 3.14, so
that path no longer resolves. Because bashio enables errexit, the
missing file aborted init-motioneye with exit code 127 on every start,
which took down the S6 supervision tree and the whole add-on.

The location is now resolved from the installed motioneye package, so a
future Python bump cannot break it again.

Also drops http_basic_auth from the shipped configuration, since
motionEye 0.44.0 removed the option and warns about it on every start,
and updates the installation docs for the passwords that 0.44.0 now
requires for both the admin and surveillance user.

---------

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>
Co-authored-by: Franck Nijhof <git@frenck.dev> 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v21 (#580)

* ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v21

* ⬆️ Update add-on base image to v21.0.3 and Alpine packages

Bumps the add-on base image to 21.0.3 (Alpine 3.24.1) and updates all
pinned apk packages to the latest versions available for Alpine 3.24.

Base image 21.0.2 pinned libcrypto3/libssl3 at 3.5.7-r0, which conflicts
with openssl-dev 3.5.8-r0 in the Alpine 3.24 repositories. Base image
21.0.3 carries the OpenSSL 3.5.8-r0 bump and resolves that conflict.

Also points the Renovate Repology tracking at alpine_3_24 instead of the
now outdated alpine_3_22.

* 🐛 Fix Shellcheck findings in S6 finish scripts

The shared CI workflow now passes `run`, `finish`, and `healthcheck` to
Shellcheck, since those S6 service scripts are extensionless and use a
bashio shebang the action does not recognise as shell on its own. That
exposed pre-existing findings in both finish scripts:

- SC2034: `declare exit_code` was dead, only the `exit_code_container`,
  `exit_code_service` and `exit_code_signal` variables are used.
- SC2155: splits the command substitution from the readonly declaration
  so a failing read is not masked.
- SC2004: drops the needless `$` on an arithmetic variable.

Also adds the missing `shellcheck shell=bash` directive to the Nginx
finish script, matching its motionEye sibling.

---------

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>
Co-authored-by: Franck Nijhof <git@frenck.dev> 
- ⬆️ Update motioneye-project/motioneye to v0.43.1 (#577)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update alpine_3_22/rsync to v3.4.1-r1 (#576)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v19 (#575)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
