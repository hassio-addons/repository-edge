- Fix the WebUI failing to start up inside the Ingress iframe

Ingress frames the panel in Home Assistant, and three places in the web
interface assume the window above them is qBittorrent's own. That is true
of its dialogs and false for the main window, so color-scheme.js, misc.js
and MochaUI's underlay each threw before the interface had been built,
leaving a half drawn page with an unfinished toolbar.

The scripts are Qt resources inside qbittorrent-nox, so NGINX corrects the
three lines on the way through, falling back to the app's own window the
way dynamicTable.js already does for the same value.
