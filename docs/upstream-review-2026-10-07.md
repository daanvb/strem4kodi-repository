# Upstream adaptations — 7 October 2026

Reviewed original-project main through `9ee6613705a3e2faddc4679de85b65050e998f18` against the prior reviewed head `521612600c040529b765599e287d86ad3299380a`. Six new commits; adapted the two improvements selected by the user.

| Original change | Adaptation |
| --- | --- |
| `9a69998`: subtitle provider/FPS display | Retain supplying add-on names and supplied frame rates, with bounded labels and inline-stream attribution. Preserve Strem4Kodi's language filtering, deduplication, forced flags, release filenames, subtitles-off default and multi-provider access. Do not import supporter restrictions or change automatic selection based on FPS. |
| `fedc738`, `9a7ad12`: font cleanup/notices | Remove unused SF-Pro and replace Nick-Titling, Engebrechtre and Westmeath references with bundled Inter weights in both font definition copies. Preserve font identifiers, sizes and aspect settings. Copy matching Inter/Noto/Remix notices after verifying that each retained font is byte-identical to the upstream copy described by those notices. Keep Strem4Kodi branding in the new bundle notice. |
| `9a69998`: stream sorting/provider tiers | Excluded: existing Strem4Kodi functionality covers source collection, filtering, size reporting and sorting. No original-project supporter-tier limits imported. |
| `296a84f`: preview artwork | No upstream screenshot assets imported. A future Strem4Kodi-specific preview refresh remains separate. |
| `5539f07`, `9ee6613`: releases | No original-project release versions, workflows or feeds imported. |

The previously deferred account-concurrency adaptation remains excluded. The user clarified that the earlier issue concerned sports streams and has stayed resolved; this review does not attribute it to storage concurrency or reopen that issue.

Tests cover provider attribution, FPS validation, duplicate URL/language priority, forced flags and filename preservation, isolated provider failure, retained font definitions and final ZIP font/notice contents. Existing forced-subtitle and playback-default regressions also run. Kodi visual verification of the replacement display fonts remains device-dependent. Changes join the pending Strem4Kodi 1.8.17 package; no publication is implied by this adaptation.
