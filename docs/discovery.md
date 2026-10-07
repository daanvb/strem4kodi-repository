# Home and discovery

Home is dedicated to Continue Watching, Up Next and Upcoming Episodes. Installed
provider catalogues appear in Discover or Sports, regardless of their former Home
placement. Provider configurations are not changed.

Discover offers Series and Movies, then categories and collections. Popular,
Trending, All-time Greats, New Releases, Hidden Gems and Most Watched lists are
combined when their names identify the same category. Marvel, DC and Star Wars
remain separate collections. Other custom lists retain their names.

Binge-Worthy, Quick Watches, Box Office Hits, Recommendations, Most Anticipated,
Community Favourites, Favourites, Watchlist, Watch History and Genres are also
recognised. Provider prefixes are removed from display names. Franchise lists
are available through Collections; streaming-service lists through Streaming
services. Mixed (All) catalogues retain their provider request type, then filter
their results into Movies or Series. Individual franchises remain distinct.
Supplier names and original list names remain available under More options →
List sources, rather than taking space in primary category labels.

Results interleave provider rankings and remove duplicates by media type and
canonical identifiers. Different IDs without a shared IMDb identifier can still
represent the same title; titles alone are not treated as reliable identity.
Pagination retains a separate cursor for every supplier. A failed supplier does
not prevent others from returning results. Genre filters are offered only when
every supplier in the group supports those genre choices.

Sports has its own sidebar section for sport catalogues. The source provider still
controls live/upcoming event availability.

Upcoming Episodes uses confirmed future release dates from metadata for series
saved in the Stremio library, including series with playback history. The existing
background account worker resolves series metadata in bounded batches; newly
saved series can take a sync cycle to appear. Unknown release dates are omitted.
Selecting a card opens episode details rather than starting playback.
