# Diagnostics v3 validation — 15 October 2026

Changes included in app 1.8.107, following app 1.8.106. No claim is made that the Fire TV
native Play Next exit is reproduced, diagnosed or fixed by this instrumentation.

The full Windows regression suite ran 1,794 tests. Two failures were addressed:
the manual-worker test now checks the added collection-only flag, and a fake
relative test profile exposed unintended diagnostic output beside addon sources.
Failure capture now requires an existing absolute profile and the generated
fixture was removed. Both failed groups then passed (4 UI crash tests and 6
release/artwork tests), alongside 38 diagnostic tests. A further actual Play Next
handoff test checks that breadcrumbs precede native dispatch/card destruction;
all 52 Up Next tests and 10 service/app audit tests passed afterward.

Focused coverage includes credential/URL/path scrubbing, unfamiliar native
errors, repetitive error floods, input/output bounds, slot rotation across
restarts, interrupted manifest recovery, unchanged-input deduplication, private
repository enforcement, opt-out, attachment read-back verification, capture while
playing without network I/O, Android UID scoping/timeout/access restrictions,
safe exception frames, preserved Kodi thread handling, and first/repeat startup
offsets with stale-worker protection.

Python 3.8 syntax compatibility, addon/skin builds and public-source credential
checks passed. The larger redactor processed a synthetic 1 MiB repeated-error
flood in 27 ms on the development Windows machine after avoiding repeated
scrubbing of identical bodies. This is not a Fire TV performance measurement.
Unchanged old logs are not reprocessed on each collection pass.

Still required after release: real Fire TV startup samples and another Play Next
reproduction/report, checking which Android crash evidence that Fire OS build
actually permits. No diagnostics from the new version exist on the device yet.
