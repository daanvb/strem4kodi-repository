# Strem4Kodi 1.8.66

Autoplay and Play Next compare independent provider filenames, descriptions and
structured episode identifiers. AIOStreams streamData.filename is retained alongside
standard filenames, and source caches now retain this evidence. Old incomplete
provider-associated caches refresh. Explicit conflicts are excluded; a video that
is incorrectly labelled consistently still cannot be identified from metadata alone.

Explicit disc-image filenames and recognised redirected URLs/media types are rejected.
Automatic source checks run under the existing loading card before Kodi opens the
source, with a three-second HTTP timeout. Live streams bypass the network probe.
Recognised provider error slates are skipped before playback. Unknown responses and
native decoder failures cannot all be detected in advance. This moves the existing
check ahead of playback, so a slow source can add up to three seconds before handoff.

Failed automatic checks and the following retry search reuse the same loading-card
lifetime. The requested episode and resume position are preserved. Cancellation
blocks delayed dispatch. Play Next validates subsequent candidates before opening
them and no longer performs a redundant background check after initial preflight.
The native busy/shutdown safeguards from 1.8.65 remain active.

Validation: 1,233 automated tests passed, including error-slate preflight, same-card
retry, cancellation during validation, disc-image rejection and Play Next retries.
Package/source integrity and feed checks are required before publication. Native
Shield playback and display switching still need device confirmation.

Player skin remains 0.1.19. Restart Kodi after updating.
