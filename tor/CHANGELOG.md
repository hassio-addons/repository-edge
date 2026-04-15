# Changelog since v7.0.2
- Fix Tor failing to start with persistent DataDirectory

- Set /data permissions to 0700 before use, as Tor requires its
  DataDirectory to not be world-readable
- Track the temporary Tor PID via $! instead of pgrep, so only
  the correct process is killed
- Detect early Tor exit in the wait loop to fail fast instead of
  hanging indefinitely
- Wait for the temporary Tor to fully exit before continuing, to
  avoid a lock file race with the main daemon
- Remove the unreliable bootstrap grep; the hostname file is
  sufficient to confirm the hidden service is ready

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com> 
- Add documentation for resetting the onion address (#312)

Co-authored-by: frenck <195327+frenck@users.noreply.github.com>
Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com> 
- Persist Tor data directory across restartsPersist Tor data directory across restarts (#311)

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com> 
- Various spelling & grammar (#310) 
- Various spelling & grammar (#309) 
- ⬆️ Update ghcr.io/hassio-addons/base Docker tag to v20 (#308)

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>
Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com>
Co-authored-by: Franck Nijhof <git@frenck.dev> 
- Refactoring and renaming add-ons to apps (#307) 
- ⬆️ Update alpine_3_22/go to v1.24.11-r0 (#302)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
