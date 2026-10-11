# Home state across clients

Enable **Sync saved lists and Home** and configure the existing private GitHub sync token on each Kodi client. Home state uses the same private repository as saved lists. Use that repository for one Stremio account; repository-wide records are intentionally shared even when its clients have different Stremio login keys.

Continue Watching removal still clears the Stremio progress pointer. A separate removal watermark hides recently watched/saved series consistently across Kodi clients. Later playback with a newer `lastWatched` restores the card. Watermarks stay in the shared file so an offline client cannot resurrect an old removal; newer playback wins without changing that file.

You May Also Like shares only public display cards and a watched-seed signature. Clients with the same watched seeds adopt the newest cache, including clients without a TMDB key; a key is needed to generate new suggestions locally. Equal timestamps converge deterministically. Refresh remains asynchronous and cached cards remain available if lookup or sync fails. Supplier results may change during refresh, and clients can temporarily differ while offline or before the next background sync (normally within a minute).

The allowlisted payload contains no device settings, login keys, API keys or configured addon URLs. Sync is off when the existing saved-list/Home switch is off, even if a GitHub token is configured. Other Stremio clients do not understand the Kodi removal watermarks. Existing local removals are imported into shared Home state on the first background sync.
