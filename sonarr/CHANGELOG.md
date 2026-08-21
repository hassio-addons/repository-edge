# Changelog since v0.5.0
- 👷 Replace Repology with Alpine CDN datasource for package pins (#94)

Renovate's repology datasource stopped resolving Alpine package pins,
so every alpine_3_24/* lookup returned no-result and the pins were no
longer updated at all. Repology rate limits its tools/project-by
endpoint hard.

Resolve the pins against the Alpine CDN directory listing instead, via
a custom html datasource. Each href in the listing (xmlstarlet-1.6.1-r2
.apk) becomes a version candidate, and extractVersionTemplate pulls the
version out of it. The \d in that pattern keeps a package from matching
a longer sibling name.

Custom datasources use registryStrategy "first", so the community
repository needs its own packageRule with an explicit registryUrls;
xmlstarlet is the only pinned package that lives there. 
- 👷 Update workflows to v3.0.1, restore Release Drafter & tidy README (#93)

* 👷 Update workflows to v3.0.0, restore Release Drafter & tidy README

Follows hassio-addons/workflows v3.0.0, which made Release Drafter a
standalone workflow again instead of part of the CI workflow:

- Restore .github/workflows/release-drafter.yaml, now that the reusable
  workflow exists again.
- Bump all reusable workflow references to v3.0.1.
- Drop the permissions the CI workflow only needed for the embedded
  Release Drafter (contents: write, pull-requests: read); CI now runs
  with contents: read.
- Drop pull-requests: write from the label sync workflow, which only
  needs issues: write.

Also removes the lock and stale workflows entirely, and trims the
architecture, chat, and community forum badges from the README.

* 📝 Use "App" terminology in the s6 service script headers

The repository was renamed from add-on to app in 9d36f5b, but the header
comments of the s6 service scripts were missed. Comment-only change. 
- ⬆️ Update Sonarr/Sonarr to v4.0.19.2979 (#90) 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v21 (#88) 
- ⬆️ Update alpine_3_23/sqlite-libs to v3.53.4-r0 (#92)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update App base image to v20.2.0 (#87)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v20.1.1 (#86) 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v20.1.0 (#85)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
