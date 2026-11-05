<p align="center">
  <img src="https://raw.githubusercontent.com/daanvb/freeBird-repository/main/script.strem4kodi/resources/branding/freebird-icon-v1.png" width="160" alt="freeBird logo">
</p>

# freeBird

**Your Stremio library, built for the Kodi remote.**

freeBird is daanvb’s independent Kodi addon: a cinematic browsing interface, clearer source selection and configurable playback, using your Stremio account and installed addons. Kodi handles video playback; freeBird supplies its own browsing interface and an optional companion player skin.

**Latest release: freeBird 1.8.239 · Player 0.1.47 · Repository 1.0.6.** [Install and update](https://daanvb.github.io/freeBird-repository/) · [Full changelog](changelog.txt)

**Upgrading from Strem4Kodi:** install [repository 1.0.6](repository.freebird.zip), then install and open freeBird. Follow its guided migration, close and reopen Kodi when prompted, and reopen freeBird after keeping the player skin. The migration copies settings and account data into new addon profiles while retaining originals for recovery.

[Earlier release highlights](docs/release-highlights.md) describe past releases; the installation page lists current downloads.

## Development

```sh
python -m pip install -r requirements-test.txt
python tools/run-tests.py
python tools/build-stremio-addon.py --output dist
python tools/build-player-skin.py --output dist
```

Use the same Python interpreter for dependency installation and testing. The runner reports its interpreter and Pillow version, and uses the ignored `.test-run-tmp` directory inside the checkout for temporary files. On Windows, it uses Codex's bundled Python if the selected interpreter lacks Pillow and the bundled interpreter is available. Pass unittest discovery options such as `-p test_disk_cache.py` or `-v` to the runner.

Build the update feed using an explicit HTTPS `--feed-url` with `tools/build-kodi-repository.py`. The landing page is generated from the same package versions as the feed, so its download links stay current. App and skin versions must satisfy the declared dependency. Never replace an already published version's package.

Source development and validation records live in the [private development repository](https://github.com/daanvb/freeBird-private/tree/firebird) (access required).

## Install and configure

Requires **Kodi 21 or later**. Install the repository ZIP, then install freeBird from **Program add-ons**. The required player skin installs automatically. Restart Kodi after updating both packages.

- [Install / update and current downloads](https://daanvb.github.io/freeBird-repository/)
- TV installation: add `https://daanvb.github.io/freeBird-repository/` in Kodi's
  File manager, then Install from zip file → that source → `repository.strem4kodi.zip`.
- [Configuration guide](docs/configuration.md)
- [New lists, categories and Discover](docs/discovery.md)
- [Shared format / logo database](docs/format-database.md)
- [Audio pre-roll uploads](https://github.com/daanvb/freeBird-repository/tree/main/prerolls)
- [Full changelog](changelog.txt) and [earlier release highlights](docs/release-highlights.md)

## Repository roles

| Repository | Purpose |
| --- | --- |
| [Private development source](https://github.com/daanvb/freeBird-private/tree/firebird) | Active code, tests and build tools on `firebird`. Access required. |
| [Public installation feed](https://github.com/daanvb/freeBird-repository) | Kodi update packages, installation guide and public pre-roll release assets. |

The live feed retains the current release and one previous version for rollback. Earlier packages remain in Git history. See [repository layout and maintenance](docs/repository-layout.md).

## Credits and licence

Based on [Stremio-for-Kodi](https://github.com/0eroiQ/Stremio-for-Kodi), with Nimbus layouts/artwork credited to Ivar Brandt. Original contributor credits, third-party notices and **GPL-2.0-or-later** are retained. See [full acknowledgements](docs/configuration.md#source-builds-and-credits) and [LICENSE](LICENSE).

freeBird is an independent community project, not endorsed by Kodi or Stremio. It uses the TMDB API but is not endorsed or certified by TMDB.
