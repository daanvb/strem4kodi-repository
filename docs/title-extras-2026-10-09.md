# Loading facts and title taglines

The playback loading screen keeps its existing card and shows a small, optional
fact strip below it. Facts are read locally from `resources/trivia.json` by exact
movie/series IMDb identity; episode IDs use their parent series identity.
The catalogue now contains 37 paraphrased facts for 15 titles, each with a
source URL for review. Facts cover effects, filming, music and the origins of a
production. Cast/director credits and unrelated general trivia are excluded.
A title without verified trivia hides the strip. No scraping, generated facts,
new API account or playback delay is involved.

Selection avoids the immediately previous fact for that title in this app session;
the visible card then rotates through the available facts every ten seconds.
The history is bounded to 512 titles and resets when the Python session ends.
One-fact titles can repeat. There is no minimum screen duration: the card remains
until fullscreen playback is running and initial buffering has cleared. Pre-rolls
reveal at their AV start. Attempt ownership and cancellation stay active throughout.
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
