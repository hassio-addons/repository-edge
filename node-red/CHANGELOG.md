# Changelog since v1.2.6

2019/02/05 20:30 UTC - [2e8a568](https://github.com/hassio-addons/addon-node-red/commit/2e8a5682a6635c2492e7d02b534a42d3f2f8133d) by [@frenck](https://github.com/frenck)
> :shirt: Fixes missing link 

2019/02/05 20:30 UTC - [d500af7](https://github.com/hassio-addons/addon-node-red/commit/d500af72854d8653ee8d9ca726b773fc29251be6) by [@frenck](https://github.com/frenck)
> :books: Updates documentation to include the dark mode 

2019/02/05 20:30 UTC - [8405b53](https://github.com/hassio-addons/addon-node-red/commit/8405b535793f9a5c80ad3537d2ec8256637edb20) by [@frenck](https://github.com/frenck)
> :ambulance: Hotfixes the dark theme 

2019/02/05 20:30 UTC - [94baf70](https://github.com/hassio-addons/addon-node-red/commit/94baf70f71a9ffa71db303f615f4b5e343031cd3) by [@tjorim](https://github.com/tjorim)
> :sparkles: Add option for dark mode (#122)

* Prepare config option for dark mode

* Download and move the theme files

* Use /node-red subfolder of /etc

seems like other edits were missing in the last commit as well

* Update config.js

* Make sure mv puts the files in a subfolder

`/` at the end was missing

* No need to move files to /config

* Use theme files from /etc directly

* Use same folder as the rest

* Upgrade midnight-red to 0.2.6

* Forgot those names

* :pencil2: Darkmode off by default

* Revert SSL change 

