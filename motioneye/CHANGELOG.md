# Changelog since v0.23.0
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
