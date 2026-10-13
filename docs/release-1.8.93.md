# Strem4Kodi 1.8.93

Removes Strem4Kodi's native poster-tag overlays, Trending tags setting, and the background chart lookup used only to populate those overlays. Poster art and its badges can now be supplied by the separately hosted PostersPlus service through AIOMetadata's image proxy.

Poster-tag-only diagnostic counts have also been removed. Playback, metadata, ratings, artwork selection, and poster progress indicators are unchanged. Player skin remains 0.1.23.

The native tag modules and tag-only assets have now been removed from the package,
along with the optional background scanning queue, worker and setting. Hero
quality badges prefer identity-checked PostersPlus JSON facts from configured
artwork. Cached source formats remain the fallback; exact selected-source and
Kodi-detected playback information are preserved. No poster-service credentials
or hostnames are hardcoded into the addon. Player skin remains 0.1.23; restart Kodi after updating.

Artwork follow-up: remove the legacy BetterPosters template/wrapper override,
strip old native tag facts from cached rows, and reject old baked-in wrapper
images (including image-proxy failure images). Resolved artwork uses a new cache
namespace/generation, and a generated layout containing retired sash controls
is regenerated rather than reused. Neither native tag settings screen exposes
the retired toggle.

Artwork refresh now carries poster, landscape and title-logo fields from the
same configured provider. AIOMetadata's landscapePoster field is normalized so
wide catalogue cards actually use its configured PostersPlus landscape art.
Episode thumbnails, cast photos and sports art retain their existing suppliers.
Backgrounds follow the separately configured AIOMetadata background pattern. Watch state and selection are preserved.

Release validation: all 1,537 tests passed on the final Windows source checkout
using the bundled interpreter and Pillow 12.3.0. The configured internal and
public logo routes both returned valid PNG images. Source credential scanning,
package/source agreement and the public-feed checks remain required release gates.
The remaining Search crash is still under investigation; no Kodi device crash
fix is claimed by this artwork release.
