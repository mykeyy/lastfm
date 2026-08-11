album.addTags

Tag an album using a list of user supplied tags.

Params

artist (Required) : The artist name
album (Required) : The album name
tags (Required) : A comma delimited list of user supplied tags to apply to this album. Accepts a maximum of 10 tags.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<lfm status="ok">
</lfm>

album.getInfo

Get the metadata and tracklist for an album on Last.fm using the album name or a musicbrainz id.

Example URLs

Example URL: /2.0/?method=album.getinfo&api_key=YOUR_API_KEY&artist=Cher&album=Believe[&format=json]

Params

artist (Required (unless mbid)] : The artist name
album (Required (unless mbid)] : The album name
mbid (Optional) : The musicbrainz id for the album
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
username (Optional) : The username for the context of the request. If supplied, the user's playcount for this album is included in the response.
lang (Optional) : The language to return the biography in, expressed as an ISO 639 alpha-2 code.
api_key (Required)

Auth

Auth: None

Sample Response

<album>
  <name>Believe</name>
  <artist>Cher</artist>
  <id>2026126</id>
  <mbid>61bf0388-b8a9-48f4-81d1-7eb02706dfb0</mbid>
  <url>http://www.last.fm/music/Cher/Believe</url>
  <releasedate>6 Apr 1999, 00:00</releasedate>
  <image size="small">...</image>
  <image size="medium">...</image>
  <image size="large">...</image>
  <listeners>47602</listeners>
  <playcount>212991</playcount>
  <toptags>
    <tag>
      <name>pop</name>
      <url>http://www.last.fm/tag/pop</url>
    </tag>
    ...
  </toptags>
  <tracks>
    <track rank="1">
      <name>Believe</name>
      <duration>239</duration>
      <mbid/>
      <url>http://www.last.fm/music/Cher/_/Believe</url>
      <streamable fulltrack="0">1</streamable>
      <artist>
        <name>Cher</name>
        <mbid>bfcc6d75-a6a5-4bc6-8282-47aec8531818</mbid>
        <url>http://www.last.fm/music/Cher</url>
      </artist>
    </track>
    ...
  </tracks>
</album>

Attributes

    duration : In seconds

album.getTags

Get the tags applied by an individual user to an album on Last.fm. To retrieve the list of top tags applied to an album by all users use album.getTopTags.

Example URLs

Example URL: /2.0/?method=album.gettags&artist=cher&album=believe&api_key=YOUR_API_KEY[&format=json]

Params

artist (Required (unless mbid)] : The artist name
album (Required (unless mbid)] : The album name
mbid (Optional) : The musicbrainz id for the album
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
user (Optional) : If called in non-authenticated mode you must specify the user to look up
api_key (Required)

Auth

Auth: None

Sample Response

<tags artist="Sally Shapiro" album="Disco Romance">
  <tag>
    <name>swedish</name>
    <url>http://www.last.fm/tag/swedish</url>
  </tag>
  ...
</tags>

album.getTopTags

Get the top tags for an album on Last.fm, ordered by popularity.

Example URLs

Example URL: /2.0/?method=album.gettoptags&artist=radiohead&album=the%20bends&api_key=YOUR_API_KEY[&format=json]

Params

artist (Required (unless mbid)] : The artist name
album (Required (unless mbid)] : The album name
autocorrect[0|1] (Optional) : Transform misspelled artist names into correct artist names, returning the correct version instead. The corrected artist name will be returned in the response.
mbid (Optional) : The musicbrainz id for the album
api_key (Required)

Auth

Auth: None

Sample Response

<?xml version="1.0" encoding="utf-8"?>
<lfm status="ok">
    <toptags artist="Radiohead" album="The Bends">
        <tag>
            <name>albums I own</name>
            <count>100</count>
            <url>http://www.last.fm/tag/albums%20i%20own</url>
        </tag>
        ...
    </toptags>
</lfm>

Attributes

    count : A weighted count of how often the tag was applied, with a maximum of 100

album.removeTag

Remove a user's tag from an album.

Params

artist (Required) : The artist name
album (Required) : The album name
tag (Required) : A single user tag to remove from this album.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<lfm status="ok">
</lfm>

album.search

Search for an album by name. Returns album matches sorted by relevance.

Example URLs

Example URL: /2.0/?method=album.search&album=believe&api_key=YOUR_API_KEY[&format=json]

Params

limit (Optional) : The number of results to fetch per page. Defaults to 30.
page (Optional) : The page number to fetch. Defaults to first page.
album (Required) : The album name
api_key (Required)

Auth

Auth: None

Sample Response

<results for="believe">
  <opensearch:Query role="request" searchTerms="believe" startPage="1"/>
  <opensearch:totalResults>734</opensearch:totalResults>
  <opensearch:startIndex>0</opensearch:startIndex>
  <opensearch:itemsPerPage>20</opensearch:itemsPerPage>
  <albummatches>
    <album>
      <name>Make Believe</name>
      <artist>Weezer</artist>
      <id>2025180</id>
      <url>http://www.last.fm/music/Weezer/Make+Believe</url>
      <image size="small">http://userserve-ak.last.fm/serve/34/8673675.jpg</image>
      <image size="medium">http://userserve-ak.last.fm/serve/64/8673675.jpg</image>
      <image size="large">http://userserve-ak.last.fm/serve/126/8673675.jpg</image>
      <streamable>0</streamable>
    </album>
    ...
  </albummatches>
</results>
