# Changelog since v4.0.0
- :hammer: Re-branding 
- :arrow_up: Upgrades Pi-hole core to v4.4 
- :hammer: Re-branding 
- :arrow_up: Upgrades sudo to 1.8.31-r0 
- :arrow_up: Upgrades php7 to 7.3.15-r0 
- :arrow_up: Upgrades ncurses to 6.1_p20200118-r2 
- :arrow_up: Upgrades libxml2 to 2.9.10-r2 
- 🔨Add access control to api.conf (#114) 
- :arrow_up: Upgrades add-on base image to v7.0.2 
- 🔨Admin scripts rewrite (#123)

* 🔨Re-write admin/scripts for direct users

* 🔨Re-write admin/scripts for ingress 
- :ambulance: Fix broken Home Assistant DNS servers in list 
- :hammer: Updates for upstream Supervisor changes 
- :hammer: Update add-on config with new password & list features 
- :hammer: Re-branding 
- :books: Update add-on documentation to use new YAML configuration format 
- :arrow_up: Upgrades nginx to 1.16.1-r6 
- :arrow_up: Upgrades add-on base image to v7.0.0 
- :books: Update Home Assistant integration instruction 
- :ambulance: Hot patch FTL for nettle 3.5 compatibility 
- :arrow_up: Upgrades procps to 3.3.16-r0 
- :arrow_up: Upgrades ncurses to 6.1_p20191130-r0 
- :arrow_up: Upgrades lua-resty-http to 0.15-r0 
- :arrow_up: Upgrades git to 2.24.1-r0 
- :arrow_up: Upgrades perl to 5.30.1-r0 
- :arrow_up: Upgrades nginx to 1.16.1-r4 
- :arrow_up: Upgrades logrotate to 3.15.1-r0 
- :arrow_up: Upgrades bind-tools to 9.14.8-r5 
- :arrow_up: Upgrades openssl to 1.1.1d-r3 
- :arrow_up: Upgrades psmisc to 23.3-r0 
- :arrow_up: Upgrades sudo to 1.8.29-r0 
- :arrow_up: Upgrades sqlite to 3.30.1-r1 
- :arrow_up: Upgrades libxml2 to 2.9.10-r1 
- :arrow_up: Upgrades php7 to 7.3.13-r0 
- :arrow_up: Upgrades nettle-dev to 3.5.1-r0 
- :arrow_up: Upgrades musl-dev to 1.1.24-r0 
- :arrow_up: Upgrades gcc to 9.2.0-r3 
- :arrow_up: Upgrades add-on base image to v6.0.1 
- :pencil2: Fixes some spelling and grammar 
- :pencil2: Funding adjustments 
- :fireworks: Updates maintenance/license year to 2020 
- :shirt: Fixes Markdownlint warnings 
- :arrow_up: Upgrades add-on base image to v5.0.3 
- :books: Update add-on installation instructions 
- :hammer: Updated fix killall brain damage patch 
- :arrow_up: Upgrades bind-tools to 9.14.8-r0 
- :fire: Removed coffee patch 
- ⬆️ Upgrades Pi-hole core to v4.3.2 (#106)



Co-authored-by: Franck Nijhof <frenck@addons.community> 
- ⬆️ Upgrades Pi-hole web interface to v4.3.2 (#107) 
- :books: Update documentation on how to integrate with Home Assis… (#102)

* Update README.md

Fix configuration example

* Update README.md

* More changes and fix anchor 
- 💄Fix error log path to /dev/stderr (#91) 
- 🚑Fix admin/queries.php for direct users (#98)

* 🚑Move root folder for direct access

* 👌Change to sub_filter to allow easy reverse proxy 
- 🚑Fix admin/queries.php for ingress users (#97) 
- :arrow_up: Upgrades sqlite to 3.28.0-r1 
- :arrow_up: Upgrades openssl to 1.1.1d-r0 
- :arrow_up: Upgrades php7 to 7.3.11-r0 
- :arrow_up: Upgrades nginx to 1.16.1-r1 
- :arrow_up: Upgrades bind-tools to 9.14.7-r0 
- :arrow_up: Upgrades add-on base image to v5.0.2 
- Remove virtual host configuration (#90)

* 🔨Remove Virtual Host

* 🚑Move HTTP_HOST to fastcgi.param 
- 🚑 Fixes issues with HTTP header checking (#89)

fixes #88 Admin interface from addon should always be trusted 
