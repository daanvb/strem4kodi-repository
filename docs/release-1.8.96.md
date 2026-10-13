# Strem4Kodi 1.8.96

Search suggestions omitted valid provider titles whenever the configured artwork
resolver temporarily withheld their images. Submitting the full search kept the
same titles. The suggestion builder now validates the original deferred image
without restoring it for display, preserving AIOmetadata-first artwork and strict
identity, type and relevance checks. Regression queries cover "jinx", "the jinx"
and "this country", plus production suggestion rendering and selection.

Optional hero enrichment now uses one pending slot on the existing browse worker.
It waits for 200 ms of settled focus and normally begins within 200-450 ms because
the worker ticks every 250 ms. Preview text and cached details remain immediate.
Rapid navigation retains only the latest request; page generation, focus identity,
modal visibility and closure safeguards still apply. No extra timer is created
for each hero enrichment request. Cached heroes render once; unchanged next-row
labels and focused artwork are not written again.

Artwork refresh still uses four workers and batches of eight. Ready responses are
coalesced at 50 ms intervals and delivered before slower requests in the batch.
Row order is preserved and stale/cancelled work remains blocked. A controlled
stalled request verifies that ready posters arrive before it is released.

Validation: all 1,594 automated tests passed on Windows with Python 3.12 and
Pillow 12.3.0, including production controller, poster cancellation, navigation,
trailer and artwork tests. Addon/skin builds, source credential scanning and
package/feed integrity checks passed. The previous 1.8.95 search crash workaround
was confirmed by the user on their tested Fire TV; no native crash stack proves
the inferred root cause. Actual frame rate and perceived scrolling smoothness
have not been measured on Fire TV. Player skin remains 0.1.23.
