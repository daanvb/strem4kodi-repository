# Home and discovery

Home is dedicated to Continue Watching, Up Next and Upcoming Episodes. Installed
provider catalogues appear in Discover or Sports, regardless of their former Home
placement. Provider configurations are not changed.

Discover offers Type, Browse group and List controls. Popular,
Trending, All-time Greats, New Releases, Hidden Gems and Most Watched lists are
combined when their names identify the same category. Marvel, DC and Star Wars
remain separate collections. Other custom lists retain their names.

Binge-Worthy, Quick Watches, Box Office Hits, Recommendations, Most Anticipated,
Community Favourites, My Favourites, Watchlist, Watch History and Genres are also
recognised. Provider prefixes are removed from display names. Franchise lists
are available through Collections; streaming-service lists through Streaming
services. Mixed (All) catalogues retain their provider request type, then filter
their results into Movies or Series. Individual franchises remain distinct.
Supplier names and original list names remain available under Discover options →
List sources, rather than taking space in primary category labels.

Results interleave provider rankings and remove duplicates by media type and
canonical identifiers. Different IDs without a shared IMDb identifier can still
represent the same title; titles alone are not treated as reliable identity.
Pagination retains a separate cursor for every supplier. A failed supplier does
not prevent others from returning results. Optional chart filters stay under Discover options and are offered only when
every supplier in the group supports those choices. Dedicated genre lists use
one genre selection under By genre.

Sports has its own sidebar section for sport catalogues. The source provider still
controls live/upcoming event availability.

Upcoming Episodes uses confirmed future release dates from metadata for series
saved in the Stremio library, including series with playback history. The existing
background account worker resolves series metadata in bounded batches; newly
saved series can take a sync cycle to appear. Unknown release dates are omitted.
Selecting a card opens episode details rather than starting playback.


## Search catalogues

Search now includes configured movie/series catalogue names alongside individual titles. Select a catalogue suggestion or a card in the Catalogues result row to open it directly. Each catalogue keeps its supplier's original ordering and original content type, including mixed movie/series lists. A chronological Star Wars list therefore stays chronological; the app does not invent a timeline for other lists.

The catalogue view offers All titles, Unwatched only, List sources and paging when the supplier supports it. Watched ticks and progress use local synced Stremio library state. A single watched episode does not mark its entire series watched: series completion requires available episode metadata and a matching watched bitmap for every regular episode. Unknown completion stays visible. Changes made elsewhere appear after account sync. Poster and wide card layouts both show watched markers.


## Simpler Discover controls

Discover uses Type → Browse group → List. Groups are Highlights, My lists, By genre, Collections, Streaming services and Other lists. Favourites is now My Favourites. For example, choose Series → By genre → Comedy, or Movies → Highlights → Trending.

Genre catalogues that advertise genre choices are expanded into named lists and merged by genre across suppliers. The original genre spelling is preserved in each supplier request. This is a single genre selection: the third header does not apply a second genre filter. Other provider filters remain available through the remote context menu under Discover options. Changing a list clears its previous filters and paging. Movies and Series remember independent lists, filters and card positions. Switching type restores its loaded page during the current app session. After reopening the app, cursor-based lists start at their first page, with saved filters and positions clamped to the available cards. Removed lists or filter options fall back safely.


## Multiple rows

Discover initially opens Most Anticipated when available, otherwise All lists in the first available group. A saved preference takes priority on later visits. All lists in a selected browse group shows a separate row for each list. For example, Series → Highlights → All lists shows Popular, Trending and other enabled highlight lists as separate rows. Select a named list in the third control to focus on one row.

Six list rows load per batch with two concurrent list requests. A More lists row opens the next batch; Discover options → First lists returns to the start. No configured lists are omitted from the list selector. Duplicate titles are removed within each merged list, while titles shared by different categories remain in both rows. Row-specific paging and thumbnail settings are available through Discover options → Options for this row. Catalogue search continues to open its own supplied-order view. Returning from settings restores the overview, row artwork choices and position.


## Artwork details and upcoming releases

Long-press a movie or series card and choose **Artwork details** to see the supplying poster provider, preferred/fallback selection and whether the response was fresh or cached. On episode cards the report also explains the actual thumbnail supplier, watched state, app blur and recognised provider blur routes. It does not inspect image pixels or claim to know Kodi's texture-cache contents. Image/configuration links stay private. **Browse options** remains available in the same menu on Discover, Sports and Library.

Long-press an episode for **Mark this episode watched** and **Mark this episode unwatched**. Both actions are always available, including for partially played episodes. This changes only the selected episode and syncs with your Stremio account. **Mark all up to here watched/unwatched** changes every regular episode from the start of the series through that episode, including earlier seasons; specials are excluded. Marking an episode unwatched refreshes its thumbnail immediately: **Blur unwatched episodes** blurs it again, **Off** leaves it clear, and **Blur unless provider artwork** keeps provider thumbnails untouched while blurring fallback artwork.

Upcoming Episodes labels the next dated unwatched episode **Airs today**, **Airs tomorrow** or **Expected [date]**. Midnight provider dates remain visible throughout their release day; this is an air-date estimate, not confirmation that a stream is available. Unknown dates remain omitted, and watched episodes are skipped. Open the card for the episode description and sources.

Settings reveal dependent options when their parent feature is enabled, retaining all saved choices while hidden. Automatic attempts appear only when a profile uses Auto play; manual profiles hide ranking preferences. Trailer, skip, Up Next and episode-rating options follow their parent switches. Subtitle appearance controls unavailable in the current Kodi build are omitted with an explanation. API keys retain their single home at the top of the menu.


Preferred posters remain visible during progress updates even when their response cache has expired. Only artwork fields are retained: watched markers, descriptions and progress still update from the new data. Home progress refreshes recheck configured posters in the background. Newer successful artwork replaces older artwork; provider/configuration changes and **Refresh artwork** invalidate the previous selection. A temporary network failure keeps the currently displayed valid poster rather than replacing it with an older rated snapshot. This does not strip provider overlays or change BetterPosters settings.

Discover hides captions underneath portrait posters to avoid clipped text; the selected title and description remain in the hero, and provider artwork and its integrated overlays are unchanged.

Sports always uses wide thumbnails, including every catalogue page and saved sports rows elsewhere in browsing. Older per-catalogue poster preferences cannot override this. Landscape artwork is preferred, followed by thumbnails, backgrounds and the supplied poster as a fallback. Movie and series catalogue layout preferences still apply.

## Choose the Discover opening list

Open Settings > General > Discover opening list. Choose a specific movie or series list, Most Anticipated, or Last visited list. A fixed list opens from its beginning when entering Discover from another sidebar page; returning from title details keeps your browsing position. If a selected list is removed, Discover safely falls back to an available list. This preference stays on this device.

## My Lists: Favourites and Watchlist

Open a movie or series, choose More, then Add to My Watchlist or Add to My Favourites. A title can belong to both. Long-press a card in My Lists for direct move/remove options. More also offers moving between the lists, removing from either list, and removing from both. Moving preserves playback progress. Removing one classification keeps the Stremio save while the other classification remains; removing both removes the save, preserving playback history.

Open My Lists in the sidebar and use the List control to switch between My Watchlist and My Favourites. Existing Stremio saves start in My Watchlist. Titles remain in their lists after being watched until you remove them. Trakt/Simkl favourites remain separate provider catalogues.

Stremio syncs the underlying saved titles and watch progress. To share the classifications, enable Settings > Account & Stremio > Sync favourites and watchlist tags on each device signed into the same Stremio account. Under API keys, use the existing Private GitHub sync token for the private strem4kodi-sync repository (Contents read/write). This option is independent of smart credits sync. Check Saved lists sync for the result; tags normally refresh within a minute while Kodi is running. Devices without tag sync enabled retain local classifications.

Tags use a separate saved-lists.json file containing title IDs, Favourite/Watchlist flags and per-tag update times. Changes merge independently, including removals, so editing a different title or classification on another device does not overwrite unrelated changes. Account credentials, stream links and progress are not stored in that file. Without a connection, local tags are retained and syncing retries.

Single-episode watched/unwatched changes use the same canonical episode ordering as playback and watched markers, including numeric strings and the alternate number field from providers. Single actions also support specials. Manual changes verify the returned watched bits before replacing local account state; an unconfirmed update reports an error rather than success.

### Compact catalogue browsing

Every Discover list, including All lists in My lists, uses an eight-column grid
with the same 206 × 309 artwork as Home. The grid scrolls vertically only; Left
and Right select titles within the visible columns. The hero area is unchanged.
Load more titles appends the next batch in individual lists; More lists appends
the next overview batch. Duplicate titles are removed. Sports retain wide cards.
Home and Discover hide the clipped captions beneath posters, using the hero to
show the selected title. Up at the top goes to Discover filters, which do not
lead upward into the sidebar. Home stays on its top row. Use Left from the
leftmost item to enter the sidebar.

### Franchise catalogues

Collections recognises franchise names and advertised custom content types,
including Marvel, StarWars and DC from AIOStreams. Generic names become descriptive
choices such as **Marvel Movies**, **DC Animations**, and **Star Wars Movies & Series
Chronological**. Chronological, release-order, era and character lists stay
separate. Movies and series are requested using the original provider type, then
placed in their respective Discover sections using the returned item types.
Collection-name search also includes the franchise in generic catalogue names.

Collections now group franchise lists beneath their parent, such as Star Wars
Universe. The list selector first chooses the collection, then its chronological,
release-order, era or character list. All lists shows only rows from that parent.


## Adding a new provider list

Add the list in your catalogue provider, such as AIOMetadata, and save its configuration. Make sure the updated add-on is installed in your Stremio account: if the provider supplies a new installation link, install/update that link. Then use Strem4Kodi **Settings → Account & Stremio → Sync account now** and reopen Discover. A browser save alone does not guarantee that Stremio's stored add-on manifest has the new list.

The app reads the installed provider's catalogue names and types:

| Supplied list | Where it appears |
| --- | --- |
| Popular or Trending | The matching **Highlights** list, merged with other suppliers of that category and deduplicated. |
| A recognised streaming service | **Streaming services**, with Apple TV variants kept as their own named lists. |
| A recognised genre | **By genre**, merged with suppliers for the same genre. |
| A franchise / collection list | **Collections**, retaining distinct curated order variants. |
| A custom list, such as Dolby Vision Profile 7 FEL | **Other lists**, retaining its name unless it also matches a recognised category or collection label. |

Grouping uses the displayed name after removing provider prefixes, not an inspection of the list's contents. A custom name containing “Popular” or “Trending” can therefore match that category. A movie list appears under Movies; a series list under Series. Supported mixed lists appear in both, with results filtered by type.

**All lists** shows separate rows for the lists in the selected group, loading six rows per batch. It is different from merging the suppliers inside one category. **Discover options → List sources** shows which catalogues supply a merged list. New catalogue lists do not add a new main sidebar menu item or become a Home row; Home remains focused on watch progress and upcoming episodes.
