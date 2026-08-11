library.getArtists

A paginated list of all the artists in a user's library, with play counts and tag counts.

Example URLs

Example URL: /2.0/?method=library.getartists&api_key=YOUR_API_KEY&user=joanofarctan[&format=json]

Params

user (Required) : The user whose library you want to fetch.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number you wish to scan to.
api_key (Required)

Auth

Auth: None

Sample Response

<artists user="RJ" page="1" perPage="50" totalPages="20">
  <artist rank="1">
    <name>Dream Theater</name>
    <playcount>1346</playcount>
    <tagcount>0</tagcount>
    <mbid>28503ab7-8bf2-4666-a7bd-2644bfc7cb1d</mbid>
    <url>http://www.last.fm/music/Dream+Theater</url>
    <streamable>1</streamable>
    <image size="small">http://userserve-ak.last.fm/serve/50/95853.jpg</image>
    <image size="medium">http://userserve-ak.last.fm/serve/85/95853.jpg</image>
    <image size="large">http://userserve-ak.last.fm/serve/160/95853.jpg</image>
  </artist>
  ...
</artists>
