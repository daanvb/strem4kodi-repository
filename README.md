<p align="center">
  <img src="https://raw.githubusercontent.com/daanvb/strem4kodi-repository/main/script.strem4kodi/icon.png" width="160" alt="Strem4Kodi blue play logo">
</p>

# Strem4Kodi

**Your Stremio library, built for the Kodi remote.**

Strem4Kodi is daanvb’s independent Kodi addon: a cinematic browsing interface, clearer source selection and configurable playback, using your Stremio account and installed addons. Kodi handles video playback; Strem4Kodi supplies its own browsing interface and an optional companion player skin.

**Latest published version: 1.8.50.** [Install and update](https://daanvb.github.io/strem4kodi-repository/) · [Full changelog](changelog.txt)

## What's new in 1.8.50

- Separate **Favourites** and **Watch Later** menus, matching context actions, a wider shaded side menu and a football icon for Sports. Add-ons are managed through Settings.
- Movie collection search and saved collection cards, using your existing TMDB key. Shared saved collections require this update on every device.
- Stream results appear as each add-on responds. Autoplay can start an exact preference match early; duplicate counts do not trigger playback. Quality limits and source filters still apply.
- Refreshed loading cards with optional local trivia, italic title taglines, consistent fonts/colours and a purple player with tidier chapter markers.
- Clearer settings statuses, full help through Info, better request-failure explanations and a clean Back route from add-on management.
- Stronger trailer containment, no previews for upcoming episodes, consistent cached formats and protection against concurrent account updates.
- Final audit keeps cached sources available if optional logo-data storage fails. Provider budgets and cautious background discovery are retained.

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
