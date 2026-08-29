- Modernize the app and update Syncthing to v2.1.3

The app was last touched in 2020. It built Syncthing v1.3.1 from Go source
against hassioaddons/base:7.0.5, ran on s6-overlay v2, and carried vendored
yq binaries for five architectures.

- Build on ghcr.io/hassio-addons/base:21.0.3 for aarch64 and amd64, taking
  Syncthing v2.1.3 from the upstream release tarball.
- Move to config.yaml and build.yaml, s6-rc v3 services, and translations.
- Serve the web interface through NGINX so Ingress works. Syncthing sends
  X-Frame-Options and rejects a non-loopback Host when bound to loopback;
  both are handled in the proxy rather than by rewriting the user's own
  Syncthing configuration.
- Run on the host network, so local discovery finds devices the way it would
  on any other machine.
- Seed the default folder path to /share on first run only. Syncthing leaves
  it empty and resolves a relative path against the working directory, so a
  folder added as "Documents" would land in the container filesystem and be
  destroyed on the next update.
- Map the Home Assistant directories in for syncing, and keep Syncthing's
  file index out of Home Assistant backups.
- Add CI, deployment, Renovate and repository documentation.
