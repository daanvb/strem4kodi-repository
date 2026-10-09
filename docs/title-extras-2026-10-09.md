# Loading facts and title taglines

**Included in Strem4Kodi 1.8.59, with player skin 0.1.17.**

The playback loading screen keeps its existing card and adds an optional fact
strip. Opening a movie or series starts a separate Wikimedia lookup by the exact
IMDb identity. Episodes use their parent series identity. No API key or new
setting is needed. An IMDb ID is sent to Wikidata; the confirmed article title
is sent to English Wikipedia. No stream URL, account data or viewing progress is
sent to these services.

The lookup checks active Wikidata IMDb claims and requires a single matching
English article, including when a deprecated cancelled adaptation appears in
search. It never selects a film by its name alone. Three serial API calls retrieve
identity, article and current production text. Requests use an identifying
User-Agent, compressed transfers, five-second socket/read budgets and a
12-second lookup budget checked between calls. Compressed and decoded responses
are capped at 2 MiB. Rate limits and busy-service responses trigger backoff.

Facts are complete 65–190-character sentences from cited paragraphs in production,
filming, development, effects, design, animation or music sections. They are
selected without generation or rewriting. Plot, cast, release, episode and review
sections are excluded; additional filters remove dependent fragments and common
spoiler wording. This is conservative filtering, not a guarantee against all
spoilers. Wikipedia is community edited; citations are evidence, not independent
verification. The strip attributes Wikipedia contributors under CC BY-SA 4.0
and displays a permanent link to the source revision. The licence is available at
https://creativecommons.org/licenses/by-sa/4.0/ .

A single daemon worker coalesces requests for the same title, with at most four
outstanding titles and eight subscribers per title. Only explicitly opened titles
are prefetched, not every poster passed while browsing. The loading card reads
memory or the bundled offline catalogue immediately. All HTTP and persistent
cache work runs on the worker, with no fetch wait in the stream search, resolver,
Cancel or input callback. Results can update the existing card during either
search or playback preparation; completed/cancelled/replaced dialogs ignore them.
No new card or minimum loading duration is introduced.

Positive results use the existing metadata cache lifetime, capped at seven days;
the default and unlimited-policy refresh interval is 24 hours. Empty results are
cached for up to six hours; failures have a ten-minute session cooldown. The
memory cache is capped at 128 titles. Persistent storage uses the existing
metadata category and size/disable policy. An explicit record expiry keeps empty
results refreshable even when the metadata policy is unlimited. Clearing or
expiry of disk data does not clear an already loaded session memory entry.

The bundled 37 sourced facts for 15 titles remain an offline fallback. A title
without live or bundled facts hides the strip. Only facts about the current title
are shown. Availability varies with article coverage and the strict filters;
we do not replace missing trivia with cast/director credits or general trivia.

Selection avoids the immediately previous fact for that title in this app session;
the visible card then rotates through the available facts every ten seconds.
The history is bounded to 512 titles and resets when the Python session ends.
One-fact titles can repeat. There is no minimum screen duration: the card closes
on the current attempt's AVStarted, including pre-rolls. A missed-callback fallback
checks progressing video with the matching attempt property or source URL hash;
fullscreen and caching state do not delay dismissal. Attempt ownership and
cancellation stay active throughout.
The fact strip uses the same owned fonts and theme colours as the card.

Taglines supplied by metadata add-ons are preserved when merging title details.
With the existing TMDB key, taglines and safe title details are fetched alongside
GB classifications using TMDB's `append_to_response`, replacing the previous
classification-only request. This retains the existing exact-ID lookup and
two-request cold path, with the same metadata cache policy and no additional
stream-provider calls. Cached older classification-only entries don't contain
taglines; the new operation uses a distinct cache key. Optional enrichment failure
keeps the provider metadata usable.

The movie/series hero synopsis starts with an italic, quoted tagline when present.
It is display formatting only; stored plot text is unchanged, existing opening
taglines are not duplicated, and the plot visibility setting hides both.
Selected episode synopses remain episode-specific and don't gain their parent
series tagline. Sparse saved entries carry taglines through hero enrichment.

Validation covers both TMDB types, exact identity rejection, request counts,
cache/error handling, rotation, source attribution, strip geometry and episode
synopsis/visibility. Kodi hardware rendering still needs device confirmation.

## Local validation of live fetching

All 1,166 automated tests passed after the final changes. Checks cover exact
identity and deprecated adaptations, cited sentence extraction, abbreviations,
response limits and compression, API backoff, cache expiry, bounded/coalesced
workers, source attribution, late updates, search-to-playback handover and stale
results after closing/cancelling/replacing a card. Live public API checks returned
facts for Tetris, Rick and Morty, The Last of Us, Jurassic Park and Back to the
Future. A compressed live request was also exercised through the actual worker.

The isolated local preview contains 638 entries and passes source-byte agreement,
ZIP integrity, Python/XML parsing and known credential-signature checks. It has
not been uploaded or distributed. No release version has been advanced and no
feed changes were made. Rendering and input responsiveness on Kodi hardware
still need device confirmation.

## Loading dismissal correction in 1.8.59

Waiting for fullscreen and cleared caching after AVStarted could keep the modal
card above an already playing video. The callback now dismisses the matching card
before other native GUI updates. The independent watcher also accepts AVStarted
without making more native player queries. Its fallback recognises progressing
current video even when no AVStarted callback arrives, while rejecting older or
unrelated playback. Each new manual playback gets its own readiness callback.

Every rendered layer, including the backdrop and trivia, is bound in XML to its
dialog lifetime's Home ownership token. Dismissal clears that token before native
close, and a late first update checks ownership again before doModal. This prevents
queued show/close work from drawing a dismissed card over video. Attempt-specific
temporary theme files prevent overlapping construction from reading another
attempt's ownership condition; those files are removed when the modal thread ends.

The companion skin hides its separate DialogBusy artwork while video is playing
or fullscreen video is visible, so closing the owned card does not reveal another
busy screen. Kodi's fullscreen buffering indicator remains available for actual
buffering. This companion change requires installation of the matching skin when
1.8.59 is installed; updating only the script is insufficient.

Regression checks cover callback dismissal independent of fullscreen/cache queries,
missed callbacks, repeated playback, close during first update, visibility cleared
before a blocked native close, isolated generated layouts, stale callbacks and
existing cancellation and late trivia updates. The full suite passed: 1,173 tests.
Kodi device rendering remains
unverified. The release includes both app 1.8.59 and companion skin 0.1.17.
