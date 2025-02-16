# Changelog since v5.18.1
- user-init: Safeguarded linking directories via the --no-dereference flag to avoid link-loops. Catching linking of .gitignore and .ssh via a warning, so that s6 does does not crash (and with it, the container) (#922) 
- 🎆 Updates maintenance/license year to 2025 (#924) 
- ⬆️ Update ghcr.io/hassio-addons/debian-base Docker tag to v7.7.1 (#923)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_12/git to v1:2.39.5-0+deb12u2 (#919)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
