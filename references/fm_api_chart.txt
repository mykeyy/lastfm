chart.getTopArtists

Get the top artists chart

Example URLs

Example URL: /2.0/?method=chart.gettopartists&api_key=YOUR_API_KEY[&format=json]

Params

page (Optional) : The page number to fetch. Defaults to first page.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
api_key (Required)

Auth

Auth: None

Sample Response

<artists page="1" perPage="50" totalPages="20" total="1000">
  <artist>
    <name>The Beatles</name>
    <playcount>1550293</playcount>
    <listeners>114106</listeners>
    <mbid>b10bbbfc-cf9e-42e0-be17-e2c3e1d2600d</mbid>
    <url>http://www.last.fm/music/The+Beatles</url>
    <streamable>1</streamable>
    <image size="small">http://userserve-ak.last.fm/serve/34/880929.jpg</image>
    <image size="medium">http://userserve-ak.last.fm/serve/64/880929.jpg</image>
    <image size="large">http://userserve-ak.last.fm/serve/126/880929.jpg</image>
    <image size="extralarge">http://userserve-ak.last.fm/serve/252/880929.jpg</image>
    <image size="mega">http://userserve-ak.last.fm/serve/500/880929/The+Beatles.jpg</image>
  </artist>
  ...
</artists>

chart.getTopTags

Get the top artists chart

Example URLs

Example URL: /2.0/?method=chart.gettoptags&api_key=YOUR_API_KEY[&format=json]

Params

page (Optional) : The page number to fetch. Defaults to first page.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
api_key (Required)

Auth

Auth: None

Sample Response

<tags page="1" perPage="50" totalPages="5" total="250">
  <tag>
    <name>rock</name>
    <url>http://www.last.fm/tag/rock</url>
    <reach>309437</reach>
    <taggings>3064604</taggings>
    <streamable>1</streamable>
    <wiki>
      <published>Sun, 24 Oct 2010 17:40:33 +0000</published>
      <summary>
Rock music is a genre of music started in America. It h...
      </summary>
      <content>
Rock music is a genre of music started in America. It has its roots in 1940s and 1950s rock and roll and rockabilly, which evolved from blues, country music and other influences. According to the All Music Guide, “In its pu...
      </content>
    </wiki>
</tag>
...
</tags>

chart.getTopTracks

Get the top tracks chart

Example URLs

Example URL: /2.0/?method=chart.gettoptracks&api_key=YOUR_API_KEY[&format=json]

Params

page (Optional) : The page number to fetch. Defaults to first page.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
api_key (Required)

Auth

Auth: None

Sample Response

<tracks page="1" perPage="50" totalPages="20" total="1000">
  <track>
    <name>Dark Fantasy</name>
    <playcount>124394</playcount>
    <listeners>42141</listeners>
    <mbid/>
    <url>http://www.last.fm/music/Kanye+West/_/Dark+Fantasy</url>
    <streamable fulltrack="0">0</streamable>
    <artist>
      <name>Kanye West</name>
      <mbid>164f0d73-1234-4e2c-8743-d77bf2191051</mbid>
      <url>http://www.last.fm/music/Kanye+West</url>
    </artist>
  </track>
  ...
</tracks>
