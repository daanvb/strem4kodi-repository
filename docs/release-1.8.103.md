# Strem4Kodi 1.8.103

- Cover the Search/collection-to-movie handoff before stopping the trailer or retiring the old full window. Keep the opaque cover through details initialization and clean it up on cancellation or failed loading.
- Preserve native-window retirement protection and exact Search/collection return state. Prevent pending handoffs from rebuilding collection rows or accepting duplicate activations.
- Suppress repeated navigation clicks while holding Left at a row edge and opening the sidebar. Restore navigation sounds after the hold, other input or window close; keep saved sound settings and media volume unchanged.
- Display the installed Strem4Kodi app version beneath the Settings heading.
- Automated regression, package/source, XML, Python 3.8 and credential checks passed. Physical Fire TV transition rendering and remote audio still need a device retest. Skin remains 0.1.25; restart Kodi after updating.

Local validation: the full 1,728-test run passed, followed by affected-module checks for the added cover-lifecycle case and Settings label. GitHub validates the final committed source before public publication. Native TV rendering and sound timing remain subject to on-device verification. No profile recapture is required.
