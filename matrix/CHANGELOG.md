# Changelog since v0.3.1

2019/04/22 18:24 UTC - [38351f8](https://github.com/hassio-addons/addon-matrix/commit/38351f857dcf2f4a653e15a1c4ece8ee56026d6b) by [@frenck](https://github.com/frenck)
> :ambulance: Ensure key are generated on first run 

2019/04/22 18:24 UTC - [2ac6f21](https://github.com/hassio-addons/addon-matrix/commit/2ac6f21cc87720b420e88e9eab9b66ae5d4e66af) by [@renovate[bot]](https://github.com/apps/renovate)
> :arrow_up: Updates pysaml2 to v4.7.0 (#12) 

2019/04/22 18:24 UTC - [f5e8919](https://github.com/hassio-addons/addon-matrix/commit/f5e89194ceec5ede0f480f268ecfeb78cbfd3602) by [@frenck](https://github.com/frenck)
> :hammer: Major refactor of add-on (#11)

- Moves add-on onto Python base images
- Moves requirements into a separate TXT file, so renovatebot can help out
- Adds support for Ingress
- Adds port descriptions
- Adds HA authentication when accessing riot directly
- Replaces NGinx configuration
- Improved python cleanup logic in Dockerfile
- Updated documentation
- Makes NGinx wait for synapse to start
- Forces ports & interfaces to use 

