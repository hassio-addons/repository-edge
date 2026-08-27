# Changelog since v0.8.1
- Correct the license label and document the v5 to v6 session loss (#172) 
- Keep the EMQX node name stable across hostname changes (#171)

* Keep the EMQX node name stable across hostname changes

EMQX names its database directory after the node name, and this app
derived that name from the Home Assistant hostname. Renaming the
instance pointed EMQX at a fresh, empty database while the populated one
stayed on disk under the old name, out of reach. Getting back to it
meant reverting the hostname, since moving the directory does not work:
the old node name is recorded inside the database files.

The node name is now resolved once and kept in `/data/emqx/node.name`:

- A new installation gets `emqx@127.0.0.1`, which no hostname can move.
- An existing installation keeps the name its database already carries,
  discovered from the single directory under `data/mnesia`, so updating
  moves nothing.
- More than one such directory means an earlier hostname change already
  split the data. The names found are logged, along with a pointer at
  `EMQX_NODE__NAME`.
- `EMQX_NODE__NAME` in `env_vars` still wins over all of it, and is
  validated before EMQX gets to fail on it obscurely.

Keeping a node name whose host part no longer resolves breaks the CLI:
`emqx ctl status` answers "Node 'emqx@oldhost.local' not responding to
pings", because the Erlang distribution has nowhere to connect. That
name is now mapped onto 127.0.0.1 in `/etc/hosts`, which also fixes the
CLI on installations that never changed their hostname, where
`<hostname>.local` does not resolve inside the container either.

`EMQX_HOST` and `EMQX_NAME` are dropped. They are leftovers from the
EMQX 4 entrypoint and appear nowhere in the 5.8.9 or 6.2.3 releases. The
node cookie now follows the node name rather than the hostname, so it no
longer shifts when the instance is renamed.

Fixes #161

* Address review: node dir discovery, cookie and hosts pinning

Three findings from the Copilot review, all of them real:

- Discovery only matched `emqx@*`, but a database directory is named
  after whatever `EMQX_NODE__NAME` was set to, and DOCS.md has long
  offered `something@else.local` as the example. An installation with
  one such directory fell through to `emqx@127.0.0.1` and came up
  looking empty. The glob is now `*@*`; the result is validated either
  way.

- Deriving the cookie from the node name gave every fresh installation
  the same secret, `127.0.0.1`, which is the objection this change
  raised against #164 hardcoding one. It is now 32 random bytes drawn
  once per installation and kept in `/data/emqx/node.cookie`, mode 0600.
  For a single node the cookie only gates the Erlang distribution, so
  existing installations pick up a new one with nothing to migrate.

- `getent hosts` succeeding only proves the name resolves, not that it
  resolves here. A hostname freed up and taken by another machine would
  send `emqx ctl` there instead. The mapping is now unconditional for
  any host part that is not already an address.

DOCS.md also said the ambiguous case "carries on with one of them". It
does not: with no directory matching the current hostname it falls back
to `emqx@127.0.0.1`, an empty database, which is the case most worth
warning about.

* Address review: IPv4 literal check and the ambiguous case wording

Two more from CodeRabbit, both fair:

- The guard that skips the loopback mapping for an address matched
  `^[0-9.]+$`, so `999.999.999.999`, `1.2.3` and `256.1.1.1` all counted
  as addresses and lost the mapping they need. It now matches octets.
- DOCS.md described the two ways out of the ambiguous case as one. A
  directory matching the current hostname is used and its data appears;
  only the fall through to `emqx@127.0.0.1` starts empty. 
- Update EMQX to 6.2.3 (#170) 
- Repository maintenance: App rename, workflows and policies (#168) 
- Migrate the user bundle to /etc/s6-overlay/user-bundles.d (#169) 
- Update link to EMQX documentation. (#165)

Co-authored-by: Gary Bell <git@whiteneon.com>
Co-authored-by: Franck Nijhof <git@frenck.dev> 
- Track Debian apt pins with the Renovate deb datasource (#167) 
- ⬆️ Update ghcr.io/hassio-addons/debian-base Docker tag to v9.4.0 (#162) 
- ⬆️ Update ghcr.io/hassio-addons/debian-base Docker tag to v9.2.0 (#160)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update emqx/emqx to v5.8.9 (#159)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update ghcr.io/hassio-addons/debian-base Docker tag to v9.1.0 (#157)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update ghcr.io/hassio-addons/debian-base Docker tag to v9 (#156)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
