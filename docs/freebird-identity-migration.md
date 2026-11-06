# freeBird fresh installation

Automatic migration from Strem4Kodi is no longer supported in current source.
The former migration wizard, profile copier, startup gates and compatibility
updater builder have been removed in release 1.8.242. Previously published
packages remain unchanged.

## Install as new

1. Back up any existing Kodi/addon data you want to retain.
2. Switch to Kodi's Estuary skin before removing an old player skin. Disable or
   uninstall Strem4Kodi before using freeBird so the two background services
   do not run together. Restart Kodi after disabling the old service.
3. If freeBird already contains a partial imported setup and you want a truly
   fresh start, uninstall freeBird and choose to remove its addon data only
   after saving anything you need. Reinstalling over retained data is not a reset.
4. Install the freeBird repository, then freeBird and its required player skin.
   Follow ordinary first-run setup to sign in and configure your preferences.
   Select freeBird Player in Kodi's interface settings when ready.

The app does not copy, clear, delete or inspect old addon profiles on launch.
Old migration locks and wizard flags are ignored. It does not disable another
addon, switch skins or request a restart as part of an identity handoff.
Normal device setup and player appearance controls remain available.

Canonical package IDs remain `script.freebird`, `skin.freebird` and
`repository.freebird`. Normal freeBird updates retain the current profile;
internal data-format upgrades and opt-in viewer/sync features remain supported.
Retarget old favourites or external helpers manually using the current
`resources/freebird-player.json` routes.

## Release maintenance

The feed builder emits only current freeBird packages; legacy bridge options
are no longer accepted. Do not republish an old migration bridge or advertise
the retired wizard. Historical recovery downloads remain in Git history;
retired legacy directories must not be recreated in the active feed.
