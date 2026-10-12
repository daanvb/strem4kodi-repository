# Strem4Kodi 1.8.89

Search title opening now reuses the existing window during Kodi's native Info
transition and normalizes metadata before assigning Kodi properties. Startup
opens cached Home, and browsing no longer starts page-wide source/logo workers;
focused-title checks still begin after 1.5 seconds or immediately with a trailer.

Up Next no longer repeats an unverified previous-episode title. Optional
next-episode autoplay begins only after Kodi confirms a natural ending and is
limited to three automatically started episodes in one continuous session.
Series also gain Play random episode across all aired regular episodes and keep
that mode for Up Next and autoplay during the current session. A confirmed
natural-end source search now survives Kodi's temporary no-video handoff gap.

Validation: 1,552 automated tests passed. Python compilation, whitespace and
known-credential checks passed. App package/source agreement, Python/XML parsing,
ZIP integrity, declared versions and feed checksums are verified before
publication. Player skin remains 0.1.23 and repository installer remains 1.0.4.
Native Kodi rendering, decoder handoff, TV power events and low-powered-device
timing still require confirmation on representative devices.
