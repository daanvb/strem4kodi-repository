# Loading and consistency audit - 8 October 2026

Release: 1.8.47; companion skin remains 0.1.14.

Reviewed the format database, sync merge paths, source-result persistence, canonical title IDs, series overview presentation, duplicate/failing poster paths, automatic request gates and troubleshooting help geometry. This is a focused performance and correctness audit, not a claim of exhaustive security or device rendering verification.

## Findings addressed

- Learning one observation read and rewrote every source fact. Foreground learning now reads only the exact observation and series overview under the existing write transaction. Sync still merges the full snapshot safely, but writes only changed rows. Deterministic newest-result selection, cumulative series overviews and separate disc provenance remain intact.
- Series overview reads used a LIKE predicate that could scan unrelated records. Indexed identity ranges plus an exact overview lookup preserve older episode-only records and exclude neighbouring IDs.
- Upcoming episode context could hide the series overview shown elsewhere. All browsing heroes now read the same overview without changing exact playback/source identities. IMDb aliases resolve the same canonical facts.
- Metadata-supplied streams bypassed persistent fact learning. Both source paths now remember their reported capabilities locally, without querying other providers.
- Blank duplicate posters now share supplied artwork by canonical type/ID. Failed configured image requests have original-image or independent IMDb poster fallbacks. Title text is never used to merge identities.
- The new optional slow scanner could not create its initial slot: the GitHub transport treated a missing slot file as an access error. Missing-file reads now permit first creation; repository and write failures still fail closed. Added a transport-level regression beyond the mock repository tests.
- Slow scanning uses one AIOStreams provider, a five-minute shared SHA reservation, local foreground budget, daily unknown-title retry, playback pause, cancellation on page changes and 30-minute shared error backoff. It remains off by default and cannot measure quota spent by unrelated apps.
- Troubleshooting help now has a 445-pixel reading area below four visible settings rows. Other categories have a 195-pixel area below seven rows. Help remains static, above the footer, with no new scrolling.
- Expanded the evidenced offline series seed from 48 to 88. No formats inferred from poster badges or provider marketing.
- Updated stale release metadata and installation documentation.

## Validation

- 920 regression tests pass, including shared-slot contention, malformed data, first-run transport, quota/cancellation/playback gates, cross-device format updates, exact-source downgrades, series aliases, duplicate artwork and no-op database writes.
- Local synthetic benchmark: 10,000 existing source facts, seven new series observations per implementation, median update 219.80 ms for published 1.8.46 versus 10.33 ms for 1.8.47. This measures storage work on the development Windows machine, not TV performance or network latency.
- A database-trigger test confirms an unchanged 1,000-record sync writes no facts, then learning an episode inserts only the episode and overview.
- Package validation and publication checks are recorded with the release. Existing real-device low-power and remote-focus checks remain necessary; no Kodi TV session is attached here.

## Boundaries retained

No unrestricted page-wide source fan-out, unknown Pengu/Usenet Ultimate quota assumptions, upstream remote-account integration, automatic online translation or credential sharing added. The older account-storage concurrency adaptation remains deferred; no evidence connects it to the current artwork issues. Database size safeguards retain local data and pause sharing rather than deleting facts to fit.
