# Changelog since v0.7.0

2018/10/29 21:03 UTC - [8f046cb](https://github.com/hassio-addons/addon-node-red/commit/8f046cb40535b5c89fd02f3bddcd4f4857d90f0f) by [@frenck](https://github.com/frenck)
> :lock: Up the security level of the Hassio API to manager

Closes #55 

2018/10/29 21:03 UTC - [8e4f61c](https://github.com/hassio-addons/addon-node-red/commit/8e4f61c6027a7dae04c423339373e88b42bb4e56) by [@frenck](https://github.com/frenck)
> :books: Updates the README to reflect the latest changes 

2018/10/29 21:03 UTC - [5c561ce](https://github.com/hassio-addons/addon-node-red/commit/5c561ceaa739b87d968ca94f17238f53fef10e92) by [@frenck](https://github.com/frenck)
> :sparkles: Adds possibility to disable HA Authentication 

2018/10/29 21:03 UTC - [05c3207](https://github.com/hassio-addons/addon-node-red/commit/05c32079f2ad44783a272163d0f3b6e6496bf876) by [@frenck](https://github.com/frenck)
> :fire: Removes requirement for setting http node/static credential 

2018/10/29 21:03 UTC - [b6e8029](https://github.com/hassio-addons/addon-node-red/commit/b6e8029f01b6c4710a7ae8da16c928743a021974) by [@frenck](https://github.com/frenck)
> :fire: Removes Auto API token script, not needed anymore 

2018/10/29 21:03 UTC - [ae98f92](https://github.com/hassio-addons/addon-node-red/commit/ae98f92839f66a7aa7391b0621a7930592ef35c3) by [@frenck](https://github.com/frenck)
> :fire: Removes unneeded warning about no users 

2018/10/29 21:03 UTC - [3621669](https://github.com/hassio-addons/addon-node-red/commit/36216691050f8a566b8f5abbc72884553c4552d2) by [@frenck](https://github.com/frenck)
> :ambulance: Fixes incorrect JSON formatting in package.json 

2018/10/29 21:03 UTC - [1f788c6](https://github.com/hassio-addons/addon-node-red/commit/1f788c61cd1e31f120e1ff1f41224bda5199ee20) by [@heytcass](https://github.com/heytcass)
> :arrow_up: Upgrades google-tts-api to 0.0.3 (#61)

* Remove google-home-notify

The google-home-notify component is currently broken. There is an issue filed upstream, and even a PR to fix the issue proposed, but the developer seems to be unresponsive. See here: https://github.com/nabbl/node-red-contrib-google-home-notify/issues/25 Propose removing as a pre-installed module until fixed.

* :arrow_up: google-tts-api to 0.0.3 

2018/10/29 21:03 UTC - [2419c60](https://github.com/hassio-addons/addon-node-red/commit/2419c60dd6ae9d075b5733a03bc9e7faa04347b0) by [@greenkeeper[bot]](https://github.com/apps/greenkeeper)
> :arrow_up: Updates node-red-contrib-actionflows to version 2.0.1 (#65) 

2018/10/29 21:03 UTC - [b6b0367](https://github.com/hassio-addons/addon-node-red/commit/b6b036723a0707e8835a8d053127652832d1032c) by [@greenkeeper[bot]](https://github.com/apps/greenkeeper)
> :arrow_up: Updates node-red-contrib-home-assistant-websocket to version 0.1.3 (#66) 

2018/10/29 21:03 UTC - [5b74ab4](https://github.com/hassio-addons/addon-node-red/commit/5b74ab48eaddf1f58b1cc0c927c69b6be796ae6a) by [@frenck](https://github.com/frenck)
> :arrow_up: Upgrades git to 2.18.1-r0 

2018/10/29 21:03 UTC - [94cca7a](https://github.com/hassio-addons/addon-node-red/commit/94cca7aab042664c0c2bd02d96c3297f4063f8a9) by [@greenkeeper[bot]](https://github.com/apps/greenkeeper)
> :arrow_up: Updates node-red-contrib-moment to version 3.0.1 (#63) 

2018/10/29 21:03 UTC - [fed00f6](https://github.com/hassio-addons/addon-node-red/commit/fed00f620b0c367b7694abd21c73fbe234117ef6) by [@greenkeeper[bot]](https://github.com/apps/greenkeeper)
> :arrow_up: Updates node-red-contrib-home-assistant-websocket to version 0.1.2 (#56) 

2018/10/29 21:03 UTC - [8be1856](https://github.com/hassio-addons/addon-node-red/commit/8be1856676bbdbbec0a9d9a21d1f91b03e7c56cb) by [@frenck](https://github.com/frenck)
> :tractor: Renames authentication config option (#53) 

2018/10/29 21:03 UTC - [67b4125](https://github.com/hassio-addons/addon-node-red/commit/67b4125d5b5c0912f7b793e72109adb99d88d9a7) by [@frenck](https://github.com/frenck)
> :sparkes: Adds HA Authentication to Node-RED (#52)

* :sparkles: Adds HA Authentication to Node-RED

* :fire: Removes users configuration option

* :books: Updates configuration options in README

* :books: Adds clarification to installation steps 

2018/10/29 21:03 UTC - [31f3cfe](https://github.com/hassio-addons/addon-node-red/commit/31f3cfe7f149f903c1cd46470010b2cfce02f2f5) by [@bonanitech](https://github.com/bonanitech)
> :fire: Removes node-red-node-ping (#48)

This package has been deprecated. See https://www.npmjs.com/package/node-red-contrib-change-detect 

2018/10/29 21:03 UTC - [e5311c5](https://github.com/hassio-addons/addon-node-red/commit/e5311c5bd1f15e4f811b87487b94416f615a7cb1) by [@frenck](https://github.com/frenck)
> :warning: Forcing broken world to enable latest NodeJS 

2018/10/29 21:03 UTC - [76bbfac](https://github.com/hassio-addons/addon-node-red/commit/76bbfac085dab23e8e7651e353802f91458df37e) by [@frenck](https://github.com/frenck)
> :tractor: Switches add-on to node-red-contrib-home-assistant-websocket 

2018/10/29 21:03 UTC - [c25814d](https://github.com/hassio-addons/addon-node-red/commit/c25814d3b627a1bb4f787d40cd012a984c470db0) by [@frenck](https://github.com/frenck)
> :arrow_up: Upgrades nodejs to 8.12.0-r0 

2018/10/29 21:03 UTC - [205fd9e](https://github.com/hassio-addons/addon-node-red/commit/205fd9e17f4d8baf773c511ea07f8b1b4067b159) by [@frenck](https://github.com/frenck)
> :arrow_up: Upgrades gcc to 6.4.0-r9 

2018/10/29 21:03 UTC - [1c37532](https://github.com/hassio-addons/addon-node-red/commit/1c37532b02fde5517caddba5edabb89c2bd9919f) by [@greenkeeper[bot]](https://github.com/apps/greenkeeper)
> :arrow_up: Upgrades node-red-contrib-influxdb to version 0.2.2 (#41) 

2018/10/29 21:03 UTC - [6144dd7](https://github.com/hassio-addons/addon-node-red/commit/6144dd77185e0f04aa676803c4518171c0db5be7) by [@zpartal](https://github.com/zpartal)
> :books: Fix typo in README (#40) 

