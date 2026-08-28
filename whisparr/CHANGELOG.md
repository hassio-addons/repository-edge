# Changelog since v0.5.0
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
