# Changelog since v0.5.0
- 🔨 Move the user bundle to user-bundles.d (#61)

s6-overlay 3.2.3.2 moved the user bundle definitions out of
/etc/s6-overlay/s6-rc.d and into /etc/s6-overlay/user-bundles.d. The
bundle was still defined in the old location, so every container start
logged:

  rc.init: warning: defining user bundles in /etc/s6-overlay/s6-rc.d is
  deprecated, please define them in /etc/s6-overlay/user-bundles.d
  instead

Upstream still accepts the old location, but drops that compatibility in
the next major release, at which point the bundle would no longer be
picked up and the service would stop being started.

Only the bundle moves; the service definition stays in s6-rc.d. The type
file at the new location is shipped by s6-overlay itself. 
- 📝 Prepare for the add-on to app rename (#60)

* 🔨 Refresh repository meta files

Housekeeping across the repository meta files:

* The maintainer email address is now opensource@frenck.dev.
* The copyright year became a range, 2025-2026.
* YAMLLint allows a single space before inline comments and no longer
  enforces a line length, matching the other app repositories.
* The Code of Conduct is updated to Contributor Covenant 3.0, with the
  reporting placeholder pointing at opensource@frenck.dev and the
  editorial note about remedies removed.
* The security policy is replaced with the current one. It previously
  carried an inline PGP key and spanned 1839 lines; it now points at
  GitHub private vulnerability reporting and documents a disclosure
  timeline. The wording is adapted from the reference policy, dropping
  the parts that only apply to a Python package.

* 👷 Move to the app workflows

Home Assistant renames add-ons to apps in the 2026.2 release, and the
shared workflows gained app variants for that. This repository now uses
them:

* CI and Deploy call app-ci.yaml and app-deploy.yaml.
* CI no longer runs on every push. Deploy runs the CI workflow itself on
  a push to main and only deploys once it succeeds, which replaces the
  workflow_run trigger.
* Permissions are declared per workflow, as the shared workflows expect
  since v3.0.0.
* The Release Drafter workflow is a standalone workflow again, also a
  v3.0.0 change.
* All references are pinned to the v4.0.0 digest.

The lock and stale workflows are dropped entirely.

* 📝 Rename add-on to app

Home Assistant renames add-ons to apps in the 2026.2 release. All prose,
titles and labels follow that rename, keeping the capitalization that
was already in place:

* "Home Assistant Community Add-on" became "Home Assistant Community
  App", and the plural form became "Home Assistant Community Apps".
* Repository links moved from addon-whisparr to app-whisparr.
* The maintenance badge points at 2026.
* https://addons.community became https://frenck.dev/home-assistant-apps.

The architecture badges and the chat and community forum badges are
removed from the README and the README template. The Discord and forum
links themselves stay, as the support section still refers to them.

Identifiers that belong to the Supervisor schema are deliberately left
alone: the io.hass.type label, the addon_config mapping, the My Home
Assistant links and the hassio-addons organization in URLs. 
- ⬆️ Pin hassio-addons/workflows action to e0c532a (#59)

* ⬆️ Pin hassio-addons/workflows action to e0c532a

* 👷 Allow a single space before inline YAML comments

Renovate pins reusable workflow references to a commit digest and adds
the original ref as a trailing comment, using one space before the #.
The YAMLLint configuration required two, so every pinned workflow failed
the comments rule:

  12:106  error  too few spaces before comment  (comments)

The other app repositories already allow a single space here, so this
brings the configuration in line with them.

---------

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>
Co-authored-by: Franck Nijhof <git@frenck.dev> 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v21 (#56)

* ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v21

* ⬆️ Update Alpine packages for Alpine 3.24

The base image bump to v21 moves the add-on onto Alpine 3.24, so the
pinned apk packages are refreshed to the latest versions available there:

* icu-libs 76.1-r1 -> 78.1-r0
* sqlite-libs 3.49.2-r1 -> 3.53.4-r0
* xmlstarlet stays on 1.6.1-r2 (already the latest)

The Renovate configuration was still tracking alpine_3_22 through
Repology, which would have proposed downgrades on top of these pins. It
now uses the Alpine CDN datasource on v3.24, matching the app base image
and the other *arr add-ons, with xmlstarlet pointed at the community
repository.

* 🚨 Fix Shellcheck warnings in the finish script

Shellcheck flagged two issues in the Whisparr finish script:

* SC2155: the container exit code was declared and assigned in a single
  readonly statement, which masks the return value of the command
  substitution. It is now declared, assigned and marked readonly in
  separate steps.
* SC2004: dropped the unnecessary $ on the arithmetic variable in the
  signal exit code calculation.

This matches the finish script used by the other *arr add-ons.

* ⬆️ Upgrades Whisparr to 2.2.0-release.231

The add-on downloaded Whisparr from the Servarr nightly update endpoint,
which redirects to an Azure DevOps build artifact. Those artifacts are
purged after a while, so the pinned 2.0.0.1331 build disappeared and the
image build started failing on a 404 that was handed to tar:

  tar: invalid magic

The download now uses the GitHub release assets instead, matching the
other *arr add-ons. Those assets are not purged, so the pin stays
installable for as long as the release exists.

Renovate could not help here either: it tracked GitHub releases, but
upstream tags (2.2.0-release.231) never matched the 2.0.0.x scheme used
by the nightly endpoint, so the pin stayed frozen until it rotted. With
the download moved to the same releases, the version now uses loose
versioning so it can be tracked again.

Both versions store their database in whisparr2.db, so existing
databases are migrated in place rather than started from scratch.

---------

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>
Co-authored-by: Franck Nijhof <git@frenck.dev> 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v19 (#55)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
