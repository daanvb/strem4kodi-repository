# Strem4Kodi 1.8.90

Opening a title from the full Search results page now destroys the poster-grid
WindowXML first and opens details as the only full Kodi window. Returning from
details reconstructs the exact loaded Search rows, focus and selected poster.
This removes the overlapping native full-window lifetime observed when Search
terminated Kodi on constrained Fire TV hardware.

Poster tag verification is now policy-versioned. Cached rows carrying an older
verified Emmy label are ignored until current catalogue evidence rebuilds them,
and combined award lists no longer manufacture one award family for every
member. Contextual tags are horizontally centred at the absolute top of both
normal and compact posters while retaining natural title case.

The complete automated suite and focused Search, app-shell, poster geometry and
layout-cache tests passed. Python compilation, package construction and known
credential checks passed. Player skin remains 0.1.23 and repository installer
remains 1.0.4. Native device confirmation is still required.
