# Format catalogue research — 8 October 2026

## Result

- 249 reviewed movie records added to the bundled offline catalogue.
- Series coverage increased from 88 to 172: 84 additional series.
- 190 of these movie identities were absent from the existing
  1,177-row community disc snapshot. Overlapping records can add explicit
  streaming formats to disc hints; they are not counted as new disc records.
- Every record retains its technical source and check date. Exact title/year
  matching and IMDb identities prevent remake and similarly named-title mixups.

Primary source distribution (main evidence link per bundled record):

| Source | Records |
| --- | ---: |
| tv.apple.com | 377 |
| www.stan.com.au | 36 |
| www.dolby.com | 6 |
| professional.dolby.com | 2 |

## Evidence and limitations

Apple UK product pages provide explicit title-header format badges. Related
titles, episode tiles and trailers are excluded by the parser. Stan listings
provide explicit per-title badges. Dolby home-entertainment case studies add
individually confirmed formats. Metadata identity checks use public TVmaze and
Cinemeta responses, not stream addon searches. TVmaze identity links attribute
its CC BY-SA metadata: https://www.tvmaze.com/api.

The public title pages may describe current or announced releases. These are
high-level format hints, not a promise that a file is available, every season
uses a format, or every region/subscription carries the same master. Generic
HD and 5.1 labels do not imply 1080p or a specific Dolby/DTS codec. Cinema-only
Dolby releases are not treated as home-video evidence. Uncertain identities and
pages without title-scoped technical badges are skipped.

Some additional sources could not be verified: the WBD pressroom returned 403,
and generic service-format marketing pages did not establish individual-title
facts. No access restrictions were bypassed. Research caches remain outside
the repository/package. The bounded Apple passes reused cached responses;
all collection tools are developer-only and excluded from the installed app.
No AIOStreams, Pengu or Usenet Ultimate source searches were made.

## Runtime integration and validation

Reviewed movie hints are available through the same format database lookup
used by the app. They combine with disc hints; complete source observations
override both, including lower-quality or empty results. Series continue to use
the broader reviewed overview. Seed hints do not become observed source facts
and are not uploaded as private device observations. Addon updates distribute
the reviewed catalogues to every device.

Tests cover title-boundary isolation, missing headers, Stan row boundaries,
bundled evidence integrity, combined disc/streaming hints and source precedence.

Validation completed: 926 tests passed; the public-source credential audit
passed; the addon package built successfully and contains both catalogues
(249 films, 172 series), with research tools excluded. Changes are local and
have not been published as a new release.
