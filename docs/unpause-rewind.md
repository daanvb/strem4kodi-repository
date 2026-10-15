# Native unpause rewind

Settings > Playback > Unpause rewind enables a short recap for long pauses. Defaults: disabled, minimum pause 30 seconds, rewind 10 seconds.

After the pause reaches its minimum duration, the service requests one backward seek while Kodi is still paused and not buffering. The paused frame/position moves back once. Press Play to resume using Kodi's ordinary controls: S4K adds no wait, pause/play toggle or post-resume seek. If Play arrives before preparation, skip the recap rather than jumping backwards after playback starts. Native seeking and buffering can still take time; this does not guarantee immediate decoder readiness on every device.

Only a verified Strem4Kodi movie/episode session can arm the recap. Live playback, trailers and pre-rolls are excluded. Stop, error, end, changed source and manual seeks discard/disarm preparation. A duplicate pause cannot restart the timer or repeat the seek. The active file/session and native pause/buffering state are checked at dispatch. The target clamps to zero. Unsupported seeks fail quietly without retries. Our seek callback is identified separately from manual seeking, so it cannot re-arm another recap. Progress sampling excludes the backward jump from watched time.
