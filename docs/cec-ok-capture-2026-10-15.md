# Capture TV HDMI-CEC OK hold behaviour

The app 1.8.106 diagnostic parser retains only native `PushCecKeypress` Select/Enter hold duration (up to 60 seconds), the timestamp, and fixed Select/Enter/ContextMenu action/window identifiers. Other key names, typed characters, raw CEC traffic and device names remain excluded.

After the app update containing this parser is installed:

1. In Kodi Settings → System → Logging, enable debug logging. If needed enable component-specific logging and select the libCEC library.
2. Restart Kodi normally to capture a fresh log.
3. On a harmless menu item, tap OK once. Wait about three seconds, hold OK for two seconds, release, then wait three seconds and hold for four seconds. Return to the same item between trials if a short press opens a page. Do not start playback during the test.
4. Send a private S4K diagnostic report promptly, identifying the device and approximate test time. Turn debug/component logging back off afterward.

Interpret actual CEC durations and repeated action timing before attempting a mapping. A nonzero CEC duration confirms hold information reached Kodi's CEC adapter; it does not by itself prove Kodi exposes a long-press modifier to the addon. This capture does not alter ordinary OK or install a remote long-press binding.

References: Kodi 21.3 `CPeripheralCecAdapter::PushCecKeypress` and `CInputManager::HandleKey`; Kodi Wiki logging instructions.
