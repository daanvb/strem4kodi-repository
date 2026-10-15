# Strem4Kodi 1.8.104

- Fix the stuck Opening title screen when selecting a Search or collection result. Replace the blocking transition dialog with a modeless branded cover while retaining native-window retirement and Search return state.
- Verify that Kodi has opened Home or title details before entering the modal wait. Allow brief notifications to finish; recover refused or disappearing-window activation without waiting indefinitely or closing another addon's dialog.
- Show a local branded startup splash while importing the browsing interface and loading Home. Remove it when Home is ready, on failed initialization, and on exit.
- Add safe diagnostic evidence for blocked window activation. Remove the obsolete modal cover layout and verify cleanup, cancellation, notification timing and failed-loading recovery.
- Player skin remains 0.1.25 and repository installer remains 1.0.4. Restart Kodi after updating. Automated checks do not replace a physical Fire TV transition/startup test.

The old cover used Python WindowXMLDialog, which Kodi treats as modal even with show(). It blocked the title WindowXML activation; its onInit callback could never remove the cover. A regression reproduces that refusal against the old implementation and accepts the modeless replacement.

The replacement uses three local controls on Kodi's modeless background progress window. It removes only its controls and its progress handle; unrelated background jobs remain intact. The original poster window is still retired before the next one is allocated. Native activation is verified before doModal, with up to four seconds for transient modal notifications to close; failed activation restores results with a static error message.

The startup cover appears before the heavy browsing/provider imports and disappears after Home initialization/input readiness or on failure. It uses bundled branding and requires no provider requests or new settings.

Validation: complete automated regression suite, focused activation/cancellation/cleanup tests, a published-code negative regression, Python 3.8 parsing, package/source agreement, XML/ZIP integrity, feed versions/checksum/listings, credential scanning and GitHub validation before public publication. No physical Kodi device was available; native Fire TV rendering and remote timing remain to be verified. No profile recapture is needed.

Native references: [Kodi WindowXML](https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/interfaces/legacy/WindowXML.h), [window activation](https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/guilib/GUIWindowManager.cpp), [modeless progress window](https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/dialogs/GUIDialogExtendedProgressBar.cpp).
