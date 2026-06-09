tag.getInfo

Get the metadata for a tag

Example URLs

Example URL: /2.0/?method=tag.getinfo&tag=disco&api_key=YOUR_API_KEY[&format=json]

Params

lang (Optional) : The language to return the wiki in, expressed as an ISO 639 alpha-2 code.
tag (Required) : The tag name
api_key (Required)

Auth

Auth: None

Sample Response

<tag>
    <name>disco</name>
    <url>http://www.last.fm/tag/disco</url>
    <reach>27199</reach>
    <taggings>114210</taggings>
    <streamable>1</streamable>
    <wiki>
        <published>Thu, 19 Aug 2010 03:22:16 +0000</published>
        <summary><!\[CDATA\[Disco is a genre of dance-oriented music\]\]></summary>
        <content><!\[CDATA\[Disco is a genre of dance-oriented music that originated in African American, gay and Hispanic American communities in 1970s. (truncated for readability in sample)\]\]></content>
    </wiki>
</tag>

Attributes

    reach : The number of users that have used this tag
    streamable : A value of '1' indicates this tag can be used as a radio station
    taggings : The total number of times this tag has been used

tag.getSimilar

Search for tags similar to this one. Returns tags ranked by similarity, based on listening data.

Example URLs

Example URL: /2.0/?method=tag.getsimilar&tag=disco&api_key=YOUR_API_KEY[&format=json]

Params

tag (Required) : The tag name
api_key (Required)

Auth

Auth: None

Sample Response

<similartags tag="Disco">
  <tag>
    <name>high energy</name>
    <url>http://www.last.fm/tag/high energy</url>
    <streamable>1</streamable>
  </tag>
  ...
</similartags>

tag.getTopAlbums

Get the top albums tagged by this tag, ordered by tag count.

Example URLs

Example URL: /2.0/?method=tag.gettopalbums&tag=disco&api_key=YOUR_API_KEY[&format=json]

Params

tag (Required) : The tag name
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<topalbums tag="Disco">
  <album rank="">
    <name>Overpowered</name>
    <mbid/>
    <url>
      http://www.last.fm/music/Róisín+Murphy/Overpowered
    </url>
    <artist>
      <name>Róisín Murphy</name>
      <mbid>4c56405d-ba8e-4283-99c3-1dc95bdd50e7</mbid>
      <url>http://www.last.fm/music/Róisín+Murphy</url>
    </artist>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </album>
  ...
</topalbums>

tag.getTopArtists

Get the top artists tagged by this tag, ordered by tag count.

Example URLs

Example URL: /2.0/?method=tag.gettopartists&tag=disco&api_key=YOUR_API_KEY[&format=json]

Params

tag (Required) : The tag name
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<topartists tag="Disco">
  <artist rank="">
    <name>ABBA</name>
    <mbid>d87e52c5-bb8d-4da8-b941-9f4928627dc8</mbid>
    <url>http://www.last.fm/music/ABBA</url>
    <streamable>1</streamable>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </artist>
  ...
</topartists>

tag.getTopTags

Fetches the top global tags on Last.fm, sorted by popularity (number of times used)

Example URLs

Example URL: /2.0/?method=tag.getTopTags&api_key=YOUR_API_KEY[&format=json]

Params

api_key (Required)

Auth

Auth: None

Sample Response

<toptags>
  <tag>
    <name>rock</name>
    <count>1994155</count>
    <url>www.last.fm/tag/rock</url>
  </tag>
  ...
</toptags>

tag.getTopTracks

Get the top tracks tagged by this tag, ordered by tag count.

Example URLs

Example URL: /2.0/?method=tag.gettoptracks&tag=disco&api_key=YOUR_API_KEY[&format=json]

Params

tag (Required) : The tag name
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<toptracks tag="Disco">
  <track rank="">
    <name>Stayin' Alive</name>
    <mbid/>
    <url>
      http://www.last.fm/music/Bee+Gees/_/Stayin'+Alive
    </url>
    <streamable fulltrack="0">1</streamable>
    <artist>
      <name>Bee Gees</name>
      <mbid>bf0f7e29-dfe1-416c-b5c6-f9ebc19ea810</mbid>
      <url>http://www.last.fm/music/Bee+Gees</url>
    </artist>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </track>
  ...
</toptracks>

tag.getWeeklyChartList

Get a list of available charts for this tag, expressed as date ranges which can be sent to the chart services.

Example URLs

Example URL: /2.0/?method=tag.getweeklychartlist&tag=disco&api_key=YOUR_API_KEY[&format=json]

Params

tag (Required) : The tag name
api_key (Required)

Auth

Auth: None

Sample Response

<weeklychartlist tag="rock">
  <chart from="1108296002" to="1108900802"/>
  <chart from="1108900801" to="1109505601"/>
  ...
</weeklychartlist>
