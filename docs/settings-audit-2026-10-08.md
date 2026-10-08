# Settings usability audit — 8 October 2026

The troubleshooting layout previously reduced the settings list to four rows and assigned excessive space to descriptions. Rebuilding a category after a change also lost focus on the selected setting.

## Changes

- Use the same eight-row settings list across categories, including troubleshooting.
- Keep the selected row and focus after changing a setting.
- Fit all sidebar categories on screen.
- Indicate additional options with a native scrollbar and subtle up/down arrows. Do not display item counts.
- Keep help compact; open long diagnostic details in a separate paged reader.
- Wrap setting values, add clear toggle switches, and simplify the background for readability.
- Explain each category with a short subtitle. Retain the existing category order rather than introduce unnecessary nested menus.

## Validation

Settings tests cover focus retention, list capacity, overflow indicators, information pagination, and navigation to the last item. The add-on package builds successfully. Actual remote navigation and rendering still need confirmation on Kodi; no connected Kodi device was available during this audit.

## Second pass

- Checked 93 static controls against the saved setting declarations: types, enum slot counts and default ranges match. Main labels and enum choices fit their allocated width using the bundled 23px Inter font as an estimate.
- Fixed custom cache durations and sizes appearing as Disabled or as a different preset. Existing custom values remain selectable; malformed saved values display the same fallback used by the cache policy. Reading settings does not rewrite stored values.
- Left returns from a chooser to its parent setting. Focus cannot get stranded on the sidebar while a chooser is open. Returning restores the selected setting and overflow arrows immediately.
- Invalid enum indices now highlight the same fallback value shown in the summary.
- Trailer sub-options respect both the master trailer switch and automatic-preview switch. Slow discovery is hidden when format sharing is off. Hidden saved preferences remain intact.
- Subtitle summaries reuse the page's capability response rather than requesting all Kodi settings again for every row. Opening an individual control still checks its current availability.
- Shortened the slow-discovery description and completed parent-switch guidance for Popcornmeter, pre-rolls and format sharing.

Validation: 66 settings-focused tests and the full 963-test suite pass. No connected Kodi device was available; actual TV rendering, font substitution and remote navigation remain unverified. Included in release 1.8.48. Popup font validation was subsequently added; the full suite now has 965 passing tests.


## TV feedback follow-up

- Removed the up/down font glyphs that render as empty boxes on the TV. The native scrollbar remains; there are no item counts.
- Expanded the list to ten complete rows and placed a smaller help panel 20 pixels below it, reclaiming the former empty area.
- Replaced row-value textboxes with single-line labels. Long values ellipsize horizontally rather than spilling a clipped second line. The selected value is repeated in help when long; Info opens the complete value and description. Picker help is compact too; the existing paged diagnostic reader retains its full height.
- Shortened the forced-subtitle mode caption without changing its stored enum index or behaviour.
- Catalogue merging now fills missing display fields from later duplicates, including across pages and explicit IMDb/TMDB/TVDB aliases. It retains the first card's ranking, identity and playback state, never merges by title name, and guards conflicting IMDb IDs.
- Blank posters now populate the image art with the independent fallback, so the layout does not hide the image before Kodi can use it.

These fixes do not increase stream searches or change rate-limit budgets. TV rendering still needs device confirmation.
