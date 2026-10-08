# Rotten Tomatoes award badges

Title ratings use Certified Fresh or Verified Hot only when the existing MDBList
response explicitly supplies the corresponding award. Percentages alone cannot
award certification. These badges use the existing critics/audience switches;
there are no additional API requests or background lookups.

Supported evidence is MDBList's documented `certified-fresh` / `certified-hot`
keywords (strings or keyword objects), or explicit boolean
`whatson_features.rotten_tomatoes_critics_certified` /
`whatson_features.rotten_tomatoes_users_certified` fields. An explicit false
flag overrides a keyword. Unknown/missing evidence uses Fresh/Rotten or
Hot/Stale. Existing cached responses remain usable. A response without award
metadata cannot display an award until a normal ratings refresh supplies it.

Confirmed awards are suppressed below the published retention floors (70%
critics / 80% verified audience) to avoid showing contradictory cached awards.
Episode scores continue to use their own basic badges; title/season awards
are never copied onto individual episodes.

The existing Certified Fresh artwork is retained. The Verified Hot image is
bundled locally with source attribution and its accompanying licence. No
runtime image downloads are needed.

Provider keyword documentation: https://docs.mdblist.com/docs/keywords
Rotten Tomatoes award definitions: https://www.rottentomatoes.com/about
Rotten Tomatoes badge guidelines: https://www.rottentomatoes.com/help_desk/licensing
