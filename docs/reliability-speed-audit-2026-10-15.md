# Follow-up reliability and speed audit

Scope: pending Fire TV transitions, remote input guards, startup refresh, hero metadata workers, Home pagination, artwork scheduling, and playback/loading lifecycle. No publication performed and no provider or device configuration changed.

## Confirmed defects corrected

- Input ownership is now claimed atomically across callbacks. A slow action installs its settling deadline before releasing ownership; previously another callback could enter during cleanup. Readiness updates retain the later deadline instead of shortening protection established by another operation. Ownership is also released if native busy-feedback setup fails, and cleanup tolerates a retired native window.
- Pagination captures the Home revision as well as the screen generation. An old provider page cannot append into rows replaced by an incremental refresh or overwrite their cursor. Duplicate results within a single provider page are removed while advancing the cursor by the provider's actual response count.
- Hero request publication, queue consumption, cache writes and retirement checks share the existing row lock. Worker exit releases the loading state atomically with checking the queue; a worker token prevents an older worker's final cleanup from clearing a newer worker's state. Metadata from an obsolete screen generation is discarded before writing either the cache or native UI. Cached hero hits also respect retirement.
- Failed background-thread creation leaves hero, Home and pagination flags retryable. Optional artwork startup cannot interrupt navigation. Home startup feedback is cleared if its refresh worker cannot start. A transient native-control RuntimeError no longer permanently stops the Home update loop.

## Speed changes

- Artwork refresh reuses one pool of at most four workers across all batches, instead of constructing a new pool every eight titles. A controlled 24-title test now constructs one pool rather than the previous three, with no change to incremental delivery, title ordering, cancellation or provider precedence.
- Artwork lookup deduplication uses dictionary membership rather than repeatedly scanning a growing pending list. The test also covers a repeated catalogue: 48 entries representing 24 titles produce only 24 provider lookups.
- Stale metadata and pagination work cannot trigger unnecessary native redraws after a screen refresh or retirement. Network work stays outside the row lifecycle lock.

## Evidence and limits

New failure-injection tests reproduced the old-page append, duplicate posters, retired-window cached hero write, stuck hero-thread startup, input owner leak, shortened readiness deadline, and cleanup activation race before the corrections. Additional tests reproduced failed Home worker startup and a dead Home watcher after a native RuntimeError. Corrected controller tests also exercise an in-flight hero request superseded by a new screen generation, confirming that only the newer hero is cached and displayed.

The regression suite uses replaced Kodi/API boundaries and controlled thread scheduling. It does not reproduce Fire TV firmware, GPU memory pressure, arbitrary remote repeat timings or real provider latency. No on-device startup-speed improvement has been measured, and a clean test suite is not a guarantee that every device-specific defect has been found.

Validation outcome: the full 1,716-test run passed 1,714 checks and exposed two older AST-extracted test fixtures missing the newly required row lock/decorator. Both fixtures were updated to use the real lifecycle lock; their complete affected modules passed on rerun (24 tests). The production-controller, input and artwork checks passed (44, 9 and 16 tests respectively). Package integrity/XML, Python 3.8 syntax compatibility, source/package byte agreement and the credential-pattern scan also passed. No physical-device test was performed.
