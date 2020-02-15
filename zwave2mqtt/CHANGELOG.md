# Changelog since v0.4.2
- :hammer: Updates for upstream Supervisor changes 
- :hammer: Update add-on config with new password & list features 
- :hammer: Re-branding 
- :books: Update add-on documentation to use new YAML configuration format 
- :arrow_up: Upgrades nodejs to 12.15.0-r1 
- :arrow_up: Upgrades add-on base image to v7.0.0 
- :arrow_up: Upgrades Zwave2Mqtt to v2.1.1 
- :arrow_up: Upgrades open-zwave database to 0d94c9427bbd19e47457578bccc60b16c6679b49 
- :arrow_up: Upgrades nginx to 1.16.1-r6 
- :ambulance: Fix Patreon link 
- :art: Config.json file formatting 
- :arrow_up: Update OpenZWave database to 07acd31 
- :arrow_up: Upgrades Zwave2Mqtt to to 
- :pencil2: Fixes some spelling and grammar 
- :ambulance: Upgrade node-serialport on the fly for Node 12.x support 
- :arrow_up: Upgrades OpenZWave device database to 71220f4 
- :arrow_up: Upgrades openssl to 1.1.1d-r3 
- :arrow_up: Upgrades openzwave to 1.6.974-r0 
- :arrow_up: Upgrades nginx to 1.16.1-r4 
- :arrow_up: Upgrades libusb to 1.0.23-r0 
- :arrow_up: Upgrades lua-resty-http to 0.15-r0 
- :arrow_up: Upgrades eudev to 3.2.9-r1 
- :arrow_up: Upgrades yarn to 1.19.2-r0 
- :arrow_up: Upgrades nodejs to 12.14.0-r0 
- :arrow_up: Upgrades git to 2.24.1-r0 
- :arrow_up: Upgrades add-on base image to v6.0.1 
- :pencil2: Fixes some spelling and grammar 
- :pencil2: Funding adjustments 
- :fireworks: Updates maintenance/license year to 2020 
- Update OpenZwave DB to latest on 1.4 (#20)

* Update openzwave-db

I ran into the issue that my Fibaro Dimmer 2 (FGD-212) wasn't recognized and resulted in the following product in the control panel:

Unknown: type=0102, id=1000 (Unknown: id=010f)

Looking at the commits done on the OpenZwave repo after the previous version that was downloaded I expect this dimmer to be recognized. I am not sure why `3d6374c831998595744cc34ef862a80ee51973c9` was used until now, but this PR updates to the latest on `master`. Is there a reason not to update to the latest OpenZwave DB?

* Update open-zwave db to latest commit on 1.4 branch 
