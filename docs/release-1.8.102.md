# Strem4Kodi 1.8.102

- Retire native browse windows before opening movie details from Search or collections, keeping the selected results and return route intact.
- Paint the loading card before dispatching manual and automatic playback. Keep large/4K source startup covered until video is ready, with cancellation and stale-attempt protection.
- Correct zero/low watch-progress fill on poster bars, including Continue Watching and episode cards.
- Hold Left at the far-left edge to open the main menu on all devices; replace double-Left and strengthen the Exit app highlight.
- Suppress queued OK activations after slow actions. Defer Home refreshes while navigating, preserve selection, and show compact startup feedback without a fixed startup input lock.
- Prevent stale pagination/hero updates, duplicate provider posters and stuck worker flags. Reuse a bounded artwork worker pool across batches.
- Regression, Python 3.8 compatibility, package/source, XML and credential checks passed. Native Fire TV rendering, remote timing and startup speed still require device retesting. Player skin remains 0.1.25; restart Kodi after updating.

Validation includes the complete 1,716-test Windows run and corrected-fixture module reruns, controlled production-window tests, archive/source agreement, Python 3.8 parsing and credential checks. GitHub validates the committed source before the public feed is pushed. No physical Kodi device is attached; this release does not claim measured Fire TV speed or universal remote certification. No profile recapture is required.
