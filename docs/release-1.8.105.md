# Strem4Kodi 1.8.105

- Keep the branded cover visible when returning from title details to Search or a collection, until the original results and selection are restored.
- Start the splash before setup and provider imports. Use a lightweight ordinary launcher, retaining explicit playback and maintenance routes and safe cleanup around sign-in/skin changes.
- Open title details without waiting for extra ratings, title enrichment, secondary quality lookups or movie recommendations. Fill these in afterward without moving focus; discard results after leaving the page.
- Keep episode identity/runtime enrichment ready before showing series details. Retain source facts as the primary quality data and PostersPlus as a gap fallback.
- Player skin remains 0.1.25 and repository installer remains 1.0.4. Restart Kodi after updating. Physical Fire TV rendering and the exact loading-time saving still require a device retest.

The return cover is transferred through native title-window retirement to the restored browse/search window, which removes it only after restoring results and focus. Startup avoids provider imports in the ordinary video-addon launch path and shows its local cover before app setup. Explicit helper/maintenance routes remain unchanged. Pending skin changes release controls before a reload.

Title readiness uses primary metadata without the secondary quality request. One optional worker computes ratings, title enrichment, source-checked quality fallback and movie recommendations. The existing progress loop applies queued updates under the row lock while input is idle, outside source picking and return transitions. Closed windows discard results; menus and selected items are preserved. Series do not gain an unsolicited Similar request, and initial episode identity/runtime enrichment stays in the ready path.

Validation: the 1,757-test local suite plus passing focused reruns after correcting two lightweight fixtures, six new optional-loading regressions, cold-launch and return-cover tests, published-code negative checks for the two video issues, package/source agreement, Python 3.8 parsing, XML/ZIP integrity, credentials and feed checks. Exact committed-source GitHub checks gate public publication. No physical Kodi device is attached; native rendering, remote timing and measured speed need device retesting. Python cannot cover frames before Kodi invokes it. No profile recapture is needed.
