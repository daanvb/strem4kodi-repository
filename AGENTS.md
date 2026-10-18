# Strem4Kodi public Kodi feed — Codex guidance

This **public** repository (`daanvb/strem4kodi-repository`, `main`) hosts the GitHub Pages install site, Kodi addon index, release ZIPs and retained rollback packages. It is **not the Strem4Kodi development repository**.

## Where development happens
- Application source, unit tests and release tooling: **private** `daanvb/Stremio-for-Kodi-private`, active `strem4kodi` branch. Start coding sessions there; follow its root `AGENTS.md`, `STATUS.md` and `docs/repository-layout.md`.
- Private device sync and diagnostic data: separate `daanvb/strem4kodi-sync`. Never copy that data, tokens or sensitive configuration into this public feed.

## Feed safety
- Do not edit `addons.xml`, `addons.xml.sha256`, addon XML, `script.strem4kodi/`, `skin.strem4kodi/`, installer ZIPs, `index.html` or release package archives for a normal coding or documentation task.
- A release must be explicitly authorised and built/validated from the private source using the established package/index/checksum tools. Preserve the index, ZIP versions, dependencies, rollback retention and working Kodi package links.
- Never commit secrets, private device details, sync records, Stremio tokens, playback URLs or diagnostic logs here. This repository is publicly visible and GitHub Pages publishes its contents.
- GitHub Pages may rebuild on changes to `main`; documentation-only changes must not be misrepresented as a new app/skin release.
- If README, copied manifests or package listings disagree about the latest version, check the published `addons.xml` and source `addon.xml`, document the discrepancy, and repair only in a separately validated release/maintenance task.

## Working method
Keep changes minimal, run feed/package validation for release changes and verify the actual changed-file list before publishing. Record repository-source versus public-feed versus installed-device versions separately. Prefer raising source-code problems in the private development repository.
