artist.addTags

Tag an artist with one or more user supplied tags.

Params

artist (Required) : The artist name
tags (Required) : A comma delimited list of user supplied tags to apply to this artist. Accepts a maximum of 10 tags.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<lfm status="ok">
</lfm>

artist.getCorrection

Use the last.fm corrections data to check whether the supplied artist has a correction to a canonical artist

Example URLs

Example URL: /2.0/?method=artist.getcorrection&artist=Guns[&format=json]

Params

artist (Required) : The artist name to correct.
api_key (Required)

Auth

Auth: None

Sample Response

<corrections>
  <correction index="0">
    <artist>
      <name>Guns N' Roses</name>
      <mbid>eeb1195b-f213-4ce1-b28c-8565211f8e43</mbid>
      <url>http://www.last.fm/music/Guns+N%27+Roses</url>
    </artist>
  </correction>
</corrections>

artist.getInfo

Get the metadata for an artist. Includes biography, truncated at 300 characters.

Example URLs

Example URL: /2.0/?method=artist.getinfo&artist=Cher&api_key=YOUR_API_KEY[&format=json]

Params

artist (Required (unless mbid)] : The artist name
mbid (Optional) : The musicbrainz id for the artist
lang (Optional) : The language to return the biography in, expressed as an ISO 639 alpha-2 code.
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
username (Optional) : The username for the context of the request. If supplied, the user's playcount for this artist is included in the response.
api_key (Required)

Auth

Auth: None

Sample Response

<artist>
  <name>Cher</name>
  <mbid>bfcc6d75-a6a5-4bc6-8282-47aec8531818</mbid>
  <url>http://www.last.fm/music/Cher</url>
  <image size="small">http://userserve-ak.last.fm/serve/50/285717.jpg</image>
  <image size="medium">http://userserve-ak.last.fm/serve/85/285717.jpg</image>
  <image size="large">http://userserve-ak.last.fm/serve/160/285717.jpg</image>
  <streamable>1</streamable>
  <stats>
    <listeners>196440</listeners>
    <plays>1599101</plays>
  </stats>
  <similar>
    <artist>
      <name>Madonna</name>
      <url>http://www.last.fm/music/Madonna</url>
      <image size="small">http://userserve-ak.last.fm/serve/50/5112299.jpg</image>
      <image size="medium">http://userserve-ak.last.fm/serve/85/5112299.jpg></image>
      <image size="large">http://userserve-ak.last.fm/serve/160/5112299.jpg</image>
    </artist>
    ...
  </similar>
  <tags>
    <tag>
      <name>pop</name>
      <url>http://www.last.fm/tag/pop</url>
    </tag>
    ...
  </tags>
  <bio>
    <published>Thu, 13 Mar 2008 03:59:18 +0000</published>
    <summary>...</summary>
    <content>...</content>
  </bio>
</artist>

artist.getSimilar

Get all the artists similar to this artist

Example URLs

Example URL: /2.0/?method=artist.getsimilar&artist=cher&api_key=YOUR_API_KEY[&format=json]

Params

limit (Optional) : Limit the number of similar artists returned
artist (Required (unless mbid)] : The artist name
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
mbid (Optional) : The musicbrainz id for the artist
api_key (Required)

Auth

Auth: None

Sample Response

<similarartists artist="Cher">
  <artist>
    <name>Sonny & Cher</name>
    <mbid>3d6e4b6d-2700-458c-9722-9021965a8164</mbid>
    <match>1</match>
    <url>www.last.fm/music/Sonny%2B%2526%2BCher</url>
    <image size="small">http://userserve-ak.last.fm/serve/34/71168880.png</image>
    <image size="medium">http://userserve-ak.last.fm/serve/64/71168880.png</image>
    <image size="large">http://userserve-ak.last.fm/serve/126/71168880.png</image>
    <image size="extralarge">http://userserve-ak.last.fm/serve/252/71168880.png</image>
    <image size="mega">http://userserve-ak.last.fm/serve/500/71168880/Sonny++Cher.png</image>
    <streamable>1</streamable>
  </artist>
  ...
</similarartists>

Attributes

    match : A similarity value between 0 (not similar) and 1 (very similar)

artist.getTags

Get the tags applied by an individual user to an artist on Last.fm. If accessed as an authenticated service /and/ you don't supply a user parameter then this service will return tags for the authenticated user. To retrieve the list of top tags applied to an artist by all users use artist.getTopTags.

Example URLs

Example URL: /2.0/?method=artist.getTags&artist=Red%20Hot%20Chili%20Peppers&user=RJ&api_key=YOU...[&format=json]

Params

artist (Required (unless mbid)] : The artist name
mbid (Optional) : The musicbrainz id for the artist
user (Optional) : If called in non-authenticated mode you must specify the user to look up
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
api_key (Required)

Auth

Auth: None

Sample Response

<tags artist="Sally Shapiro">
  <tag>
    <name>italo</name>
    <url>http://www.last.fm/tag/italo</url>
  </tag>
  ...
</tags>

artist.getTopAlbums

Get the top albums for an artist on Last.fm, ordered by popularity.

Example URLs

Example URL: /2.0/?method=artist.gettopalbums&artist=cher&api_key=YOUR_API_KEY[&format=json]

Params

artist (Required (unless mbid)] : The artist name
mbid (Optional) : The musicbrainz id for the artist
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
page (Optional) : The page number to fetch. Defaults to first page.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
api_key (Required)

Auth

Auth: None

Sample Response

<topalbums artist="Cher">
  <album rank="1">
    <name>Believe</name>
    <mbid>61bf0388-b8a9-48f4-81d1-7eb02706dfb0</mbid>
    <listeners>24486</listeners>
    <url>http://www.last.fm/music/Cher/Believe</url>
    <image size="small">...</image>
    <image size=" medium">...</image>
    <image size="large">...</image>
  </album>
  ...
</topalbums>

artist.getTopTags

Get the top tags for an artist on Last.fm, ordered by popularity.

Example URLs

Example URL: /2.0/?method=artist.gettoptags&artist=cher&api_key=YOUR_API_KEY[&format=json]

Params

artist (Required (unless mbid)] : The artist name
mbid (Optional) : The musicbrainz id for the artist
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
api_key (Required)

Auth

Auth: None

Sample Response

<toptags artist="Cher">
  <tag>
    <name>pop</name>
    <url>http://www.last.fm/tag/pop</url>
  </tag>
  ...
</toptags>

artist.getTopTracks

Get the top tracks by an artist on Last.fm, ordered by popularity

Example URLs

Example URL: /2.0/?method=artist.gettoptracks&artist=cher&api_key=YOUR_API_KEY[&format=json]

Params

artist (Required (unless mbid)] : The artist name
mbid (Optional) : The musicbrainz id for the artist
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
page (Optional) : The page number to fetch. Defaults to first page.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
api_key (Required)

Auth

Auth: None

Sample Response

<toptracks artist="Cher">
  <track rank="1">
    <name>Believe</name>
    <mbid/>
    <playcount>56325</playcount>
    <listeners>23217</listeners>
    <url>http://www.last.fm/music/Cher/_/Believe</url>
    <image size="small">...</image>
    <image size=" medium">...</image>
    <image size="large">...</image>
  </track>
  ...
</toptracks>

artist.removeTag

Remove a user's tag from an artist.

Params

artist (Required) : The artist name
tag (Required) : A single user tag to remove from this artist.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<lfm status="ok">
</lfm>

artist.search

Search for an artist by name. Returns artist matches sorted by relevance.

Example URLs

Example URL: /2.0/?method=artist.search&artist=cher&api_key=YOUR_API_KEY[&format=json]

Params

limit (Optional) : The number of results to fetch per page. Defaults to 30.
page (Optional) : The page number to fetch. Defaults to first page.
artist (Required) : The artist name
api_key (Required)

Auth

Auth: None

Sample Response

<results for="cher" xmlns:opensearch="http://a9.com/-/spec/opensearch/1.1/">
  <opensearch:Query role="request" searchTerms="cher" startPage="1"/>
  <opensearch:totalResults>386</opensearch:totalResults>
  <opensearch:startIndex>0</opensearch:startIndex>
  <opensearch:itemsPerPage>20</opensearch:itemsPerPage>
  <artistmatches>
    <artist>
      <name>Cher</name>
      <mbid>bfcc6d75-a6a5-4bc6-8282-47aec8531818</mbid>
      <url>www.last.fm/music/Cher</url>
      <image_small>http://userserve-ak.last.fm/serve/50/342437.jpg</image_small>
      <image>http://userserve-ak.last.fm/serve/160/342437.jpg</image>
      <streamable>1</streamable>
    </artist>
	...
  </artistmatches>
</results>
