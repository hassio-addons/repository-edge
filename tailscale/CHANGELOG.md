# Changelog since v0.27.1
- Make always use DERP option configurable (#592)

* Make always use derp option configurable

* Fix small typo in English translation (#261)

---------

Co-authored-by: David Bishop <teancom@users.noreply.github.com> 
- Reinitialize bashio log outputs to the redirected stdout (#567) 
- Make all config options mandatory (#541)

* Revert "Fix DNS service default option value handling (#618)"

This reverts commit 07bbd49b88d520f4a12769f293e7daaecda0bc6c.

* Revert "Fix DNS service default option value handling (#616)"

This reverts commit bd27080a1bce66ebcf8757c04a6e9ded0b27db79.

* make config options mandatory

* mandatory - update docs

* Accept Copilot's suggestion

Co-authored-by: Copilot <175728472+Copilot@users.noreply.github.com>

* match exactly local_subnets only

* simplify grep

* rename add-on to app

---------

Co-authored-by: Copilot <175728472+Copilot@users.noreply.github.com> 
- ⬆️ Update hassio-addons/workflows action to v2.0.4 (#621)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- Fix DNS service default option value handling (#618) 
- Fix DNS service default option value handling (#616) 
- fix missed add-on to app renames (#615) 
- Fix MagicDNS incompatibility with Home Assistant's DNS (#455)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>
Co-authored-by: Franck Nijhof <git@frenck.dev> 
- drop path for ipcalc (#613) 
