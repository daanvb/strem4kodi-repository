<p align="center">
  <img src="https://raw.githubusercontent.com/daanvb/strem4kodi-repository/main/script.strem4kodi/icon.png" width="160" alt="Strem4Kodi blue play logo">
</p>

# Strem4Kodi

**Your Stremio library, built for the Kodi remote.**

Strem4Kodi is daanvb’s independent Kodi addon: a cinematic browsing interface, clearer source selection and configurable playback, using your Stremio account and installed addons. Kodi handles video playback; Strem4Kodi supplies its own browsing interface and an optional companion player skin.

**Latest published version: 1.8.51.** [Install and update](https://daanvb.github.io/strem4kodi-repository/) · [Full changelog](changelog.txt)

## What's new in 1.8.51

- **Any quality now prefers 1080p**, with 720p/lower fallbacks and 4K as a last resort. Explicit 4K preferences and quality ceilings still apply.
- Automatic searches stay behind the title loading card. Matching sources start without the extra one-second pause; Up Next uses the same selection rule.
- Settings statuses stay visible without hovering, direct actions have clearer buttons, and ratings have room for **100%**.
- Tidier Favourites/Watch Later poster text, restored action-menu icons and a solid rounded Cancel button.
- Stronger cancellation during search/playback handover. All **1,088 tests passed**; provider budgets, source filters and retry limits remain intact.

Includes **player skin 0.1.15**. Restart Kodi after updating. Collection sharing requires saved-list sync on each device.

## Install and configure

Requires **Kodi 21 or later**. Install the repository ZIP, then install Strem4Kodi from **Program add-ons**. The required player skin installs automatically. Restart Kodi after updating both packages.

- [Install / update and current downloads](https://daanvb.github.io/strem4kodi-repository/)
- [Configuration guide](docs/configuration.md)
- [New lists, categories and Discover](docs/discovery.md)
- [Shared format / logo database](docs/format-database.md)
- [Audio pre-roll uploads](https://github.com/daanvb/strem4kodi-repository/tree/main/prerolls)
- [Full changelog](changelog.txt) and [earlier release highlights](docs/release-highlights.md)

## Repository roles

| Repository | Purpose |
| --- | --- |
| [Private development source](https://github.com/daanvb/Stremio-for-Kodi-private/tree/strem4kodi) | Active code, tests and build tools on `strem4kodi`. Access required. |
| [Public installation feed](https://github.com/daanvb/strem4kodi-repository) | Kodi update packages, installation guide and public pre-roll release assets. |

The live feed retains the current release and one previous version for rollback. Earlier packages remain in Git history. See [repository layout and maintenance](docs/repository-layout.md).

## Credits and licence

Based on [Stremio-for-Kodi](https://github.com/0eroiQ/Stremio-for-Kodi), with Nimbus layouts/artwork credited to Ivar Brandt. Original contributor credits, third-party notices and **GPL-2.0-or-later** are retained. See [full acknowledgements](docs/configuration.md#source-builds-and-credits) and [LICENSE](LICENSE).

Strem4Kodi is an independent community project, not endorsed by Kodi or Stremio. It uses the TMDB API but is not endorsed or certified by TMDB.
