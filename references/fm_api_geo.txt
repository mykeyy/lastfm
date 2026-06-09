geo.getTopArtists

Get the most popular artists on Last.fm by country

Example URLs

Example URL: /2.0/?method=geo.gettopartists&country=spain&api_key=YOUR_API_KEY[&format=json]

Params

country (Required) : A country name, as defined by the ISO 3166-1 country names standard
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<topartists country="Spain">
  <artist rank="1">
    <name>Coldplay</name>
    <playcount>3199</playcount>
    <mbid>cc197bad-dc9c-440d-a5b5-d52ba2e14234</mbid>
    <url>http://www.last.fm/music/Coldplay</url>
    <streamable>1</streamable>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </artist>
  ...
</topartists>

geo.getTopTracks

Get the most popular tracks on Last.fm last week by country

Example URLs

Example URL: /2.0/?method=geo.gettoptracks&country=spain&api_key=YOUR_API_KEY[&format=json]

Params

country (Required) : A country name, as defined by the ISO 3166-1 country names standard
location (Optional) : A metro name, to fetch the charts for (must be within the country specified)
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<toptracks country="Spain">  
  <track rank="1">
    <name>Violet Hill</name>
    <playcount>1055</playcount>
    <mbid/>
    <url>http://www.last.fm/music/Coldplay/_/Violet+Hill</url>
    <streamable fulltrack="0">1</streamable>
    <artist>
      <name>Coldplay</name>
      <mbid>cc197bad-dc9c-440d-a5b5-d52ba2e14234</mbid>
      <url>http://www.last.fm/music/Coldplay</url>
    </artist>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </track>
  ...
</toptracks>
