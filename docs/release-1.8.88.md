# Strem4Kodi 1.8.88

Technical quality indicators now stay in the hero, retaining the 1.5-second
focused lookup and immediate trailer preloading. Poster quality badges and their
Appearance setting are removed. Contextual and Trending poster sashes sit at the
very top in natural title case. Exit app is a smaller separated main-menu footer
with a clear power icon, and background refresh preserves its focus.

The release audit also fixed package construction: hidden audit and test scratch
directories were previously traversed by the app builder. They are now excluded,
preventing recursive development artifacts from entering installable packages.

Validation: 1,533 automated tests passed. App package/source agreement, Python/XML
parsing, ZIP integrity, known credential signatures and feed checksum checks
passed. The unchanged published skin 0.1.23 agrees with every checked-in source
member. Repository installer remains 1.0.4. Kodi device behavior still requires
confirmation on a supported device.
