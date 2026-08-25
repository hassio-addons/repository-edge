# Changelog since v3.0.0
- Migrate the app to the Debian base image (#759)

Moves the app from Alpine to the Debian base image, matching the platform upstream builds on. nginx comes from the nginx project's own repository at 1.31.4 rather than Debian's 1.26.3, and Certbot moves to a pip venv at /opt/certbot, which lets patch 0003 be dropped entirely. 
- Bump the Timeweb and Websupport DNS plugin pins (#758) 
- Keep certbot DNS plugin installs from breaking certbot (#757) 
- Report the actual Nginx Proxy Manager version in the web UI (#755) 
- Migrate the user bundle to /etc/s6-overlay/user-bundles.d (#756) 
