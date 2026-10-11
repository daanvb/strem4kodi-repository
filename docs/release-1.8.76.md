# Strem4Kodi 1.8.76

The loading cover now remains through the pre-roll to movie transition, including when an intro is skipped. It waits briefly for the movie's fullscreen view after Kodi announces playback, with a bounded fallback for skins that need the overlay to close first. Kodi uses one player, so the movie cannot buffer simultaneously with the pre-roll.

Back from a title with an active trailer preview returns to the previous screen in one press. Automatic episode selection now checks each available filename against the episode number and a unique complete episode title when metadata permits. A filename identifying another episode is excluded from autoplay even if its S/E number matches. Uncertain sources remain available for manual choice; this cannot detect incorrectly encoded content when all labels agree on the wrong episode.

Validation: 1,390 Windows tests and package/feed checks passed. Kodi device playback and the reported one-off full-process exit still need device evidence. Player skin remains 0.1.23. Restart Kodi after updating.
