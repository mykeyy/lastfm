user.getFriends

Get a list of the user's friends on Last.fm.

Example URLs

Example URL: /2.0/?method=user.getfriends&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The last.fm username to fetch the friends of.
recenttracks (Optional) : Whether or not to include information about friends' recent listening in the response.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<lfm status="ok" total="109" page="1" perPage="50" totalPages="3">
    <friends user="joanofarctan">
        <user>
            <name>eartle</name>
            <realname>Michael Coffey</realname>
            <image size="small">http://userserve-ak.last.fm/serve/34/45718509.jpg</image>
            <image size="medium">http://userserve-ak.last.fm/serve/64/45718509.jpg</image>
            <image size="large">http://userserve-ak.last.fm/serve/126/45718509.jpg</image>
            <image size="extralarge">http://userserve-ak.last.fm/serve/252/45718509.jpg</image>
            <url>http://www.last.fm/user/eartle</url>
            <id>7737850</id>
            <country>UK</country>
            <age>29</age>
            <gender>m</gender>
            <subscriber>1</subscriber>
            <playcount>45366</playcount>
            <playlists>4</playlists>
            <bootstrap>0</bootstrap>
            <registered unixtime="1189696970">2007-09-13 15:22</registered>
            <type>subscriber</type>
        </user>
        ...
    </friends>
</lfm>

user.getInfo

Get information about a user profile.

Example URLs

Example URL: /2.0/?method=user.getinfo&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Optional) : The user to fetch info for. Defaults to the authenticated user.
api_key (Required)

Auth

Auth: None

Sample Response

<user>
    <id>1000002</id>
    <name>RJ</name>
    <realname>Richard Jones </realname>
    <url>http://www.last.fm/user/RJ</url>
    <image>http://userserve-ak.last.fm/serve/126/8270359.jpg</image>
    <country>UK</country>
    <age>27</age>
    <gender>m</gender>
    <subscriber>1</subscriber>
    <playcount>54189</playcount>
    <playlists>4</playlists>
    <bootstrap>0</bootstrap>
    <registered unixtime="1037793040">2002-11-20 11:50</registered>
</user>

user.getLovedTracks

Get the last 50 tracks loved by a user.

Example URLs

Example URL: /2.0/?method=user.getlovedtracks&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The user name to fetch the loved tracks for.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<lovedtracks user="RJ">
  <track>
    <name>The Glass Prison</name>
    <mbid/>
    <url>www.last.fm/music/Dream+Theater/_/The+Glass+Prison</url>
    <date uts="1216371514">18 Jul 2008, 08:58</date>
    <artist>
      <name>Dream Theater</name>
      <mbid>28503ab7-8bf2-4666-a7bd-2644bfc7cb1d</mbid>
      <url>http://www.last.fm/music/Dream+Theater</url>
    </artist>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </track>
  ...
</lovedtracks>

user.getPersonalTags

Get the user's personal tags

Example URLs

Example URL: /2.0/?method=user.getpersonaltags&user=rj&tag=rock&taggingtype=artist&api_key=YOUR...[&format=json]

Params

user (Required) : The user who performed the taggings.
tag (Required) : The tag you're interested in.
taggingtype[artist|album|track] (Required) : The type of items which have been tagged
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<taggings user="RJ" tag="rock" page="1" perPage="50" totalPages="1" total="11">
  <artists>
    <artist>
      <name>John Hammond</name>
      <mbid>d83e599c-2d5a-44ec-b727-587e1455b1b5</mbid>
      <url>http://www.last.fm/music/John+Hammond</url>
      <streamable>1</streamable>
      <image size="small">http://userserve-ak.last.fm/serve/34/255418.jpg</image>
      <image size="medium">http://userserve-ak.last.fm/serve/64/255418.jpg</image>
      <image size="large">http://userserve-ak.last.fm/serve/126/255418.jpg</image>
      <image size="extralarge">http://userserve-ak.last.fm/serve/252/255418.jpg</image>
      <image size="mega">http://userserve-ak.last.fm/serve/_/255418/John+Hammond.jpg</image>
    </artist>
  </artists>
</taggings>

user.getRecentTracks

Get a list of the recent tracks listened to by this user. Also includes the currently playing track with the nowplaying="true" attribute if the user is currently listening.

Example URLs

Example URL: /2.0/?method=user.getrecenttracks&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

limit (Optional) : The number of results to fetch per page. Defaults to 50. Maximum is 200.
user (Required) : The last.fm username to fetch the recent tracks of.
page (Optional) : The page number to fetch. Defaults to first page.
from (Optional) : Beginning timestamp of a range - only display scrobbles after this time, in UNIX timestamp format (integer number of seconds since 00:00:00, January 1st 1970 UTC). This must be in the UTC time zone.
extended (0|1) (Optional) : Includes extended data in each artist, and whether or not the user has loved each track
to (Optional) : End timestamp of a range - only display scrobbles before this time, in UNIX timestamp format (integer number of seconds since 00:00:00, January 1st 1970 UTC). This must be in the UTC time zone.
api_key (Required)

Auth

Auth: None

Sample Response

<recenttracks user="RJ" page="1" perPage="10" totalPages="3019">
  <track nowplaying="true">
    <artist mbid="2f9ecbed-27be-40e6-abca-6de49d50299e">Aretha Franklin</artist>
    <name>Sisters Are Doing It For Themselves</name>
    <mbid/>
    <album mbid=""/>
    <url>www.last.fm/music/Aretha+Franklin/_/Sisters+Are+Doing+It+For+Themselves</url>
    <date uts="1213031819">9 Jun 2008, 17:16</date>
    <streamable>1</streamable>
  </track>
  ...
</recenttracks>

user.getTopAlbums

Get the top albums listened to by a user. You can stipulate a time period. Sends the overall chart by default.

Example URLs

Example URL: /2.0/?method=user.gettopalbums&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The user name to fetch top albums for.
period (Optional) : overall | 7day | 1month | 3month | 6month | 12month - The time period over which to retrieve top albums for.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<topalbums user="RJ" type="overall">
  <album rank="1">
    <name>Images and Words</name>
    <playcount>174</playcount>
    <mbid>f20971f2-c8ad-4d26-91ab-730f6dedafb2</mbid>  
    <url>
      http://www.last.fm/music/Dream+Theater/Images+and+Words
    </url>
    <artist>
      <name>Dream Theater</name>
      <mbid>28503ab7-8bf2-4666-a7bd-2644bfc7cb1d</mbid>
      <url>http://www.last.fm/music/Dream+Theater</url>
    </artist>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </album>
</topalbums>

user.getTopArtists

Get the top artists listened to by a user. You can stipulate a time period. Sends the overall chart by default.

Example URLs

Example URL: /2.0/?method=user.gettopartists&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The user name to fetch top artists for.
period (Optional) : overall | 7day | 1month | 3month | 6month | 12month - The time period over which to retrieve top artists for.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<topartists user="RJ" type="overall">
  <artist rank="1">
    <name>Dream Theater</name>
    <playcount>1337</playcount>
    <mbid>28503ab7-8bf2-4666-a7bd-2644bfc7cb1d</mbid>
    <url>http://www.last.fm/music/Dream+Theater</url>
    <streamable>1</streamable>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </artist>
  ...
</topartists>

user.getTopTags

Get the top tags used by this user.

Example URLs

Example URL: /2.0/?method=user.gettoptags&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The user name
limit (Optional) : Limit the number of tags returned
api_key (Required)

Auth

Auth: None

Sample Response

<toptags user="RJ">
  <tag>
    <name>rock</name>
    <count>12</count>
    <url>www.last.fm/tag/rock</url>
  </tag>
  ...
</toptags>

user.getTopTracks

Get the top tracks listened to by a user. You can stipulate a time period. Sends the overall chart by default.

Example URLs

Example URL: /2.0/?method=user.gettoptracks&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The user name to fetch top tracks for.
period (Optional) : overall | 7day | 1month | 3month | 6month | 12month - The time period over which to retrieve top tracks for.
limit (Optional) : The number of results to fetch per page. Defaults to 50.
page (Optional) : The page number to fetch. Defaults to first page.
api_key (Required)

Auth

Auth: None

Sample Response

<toptracks user="RJ" type="overall">  
  <track rank="1">
    <name>Learning to Live</name>
    <playcount>42</playcount>
    <mbid/>
    <url>
      http://www.last.fm/music/Dream+Theater/_/Learning+to+Live
    </url>
    <streamable fulltrack="0">1</streamable>
    <artist>
      <name>Dream Theater</name>
      <mbid>28503ab7-8bf2-4666-a7bd-2644bfc7cb1d</mbid>
      <url>http://www.last.fm/music/Dream+Theater</url>
    </artist>
    <image size="small">...</image>
    <image size="medium">...</image>
    <image size="large">...</image>
  </track>
  ...
</toptracks>

user.getWeeklyAlbumChart

Get an album chart for a user profile, for a given date range. If no date range is supplied, it will return the most recent album chart for this user.

Example URLs

Example URL: /2.0/?method=user.getweeklyalbumchart&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The last.fm username to fetch the charts of.
from (Optional) : The date at which the chart should start from. See User.getChartsList for more.
to (Optional) : The date at which the chart should end on. See User.getChartsList for more.
api_key (Required)

Auth

Auth: None

Sample Response

<weeklyalbumchart user="RJ" from="1212321600" to="1212926400">
  <album rank="1">
    <artist mbid="80e577ba-841f-43ba-9f32-72e7c1692336">David Hudson</artist>
    <name>Bedarra</name>
    <mbid>dc30face-71db-413a-bcae-06accbd64aae</mbid>
    <playcount>10</playcount>
    <url>http://www.last.fm/music/David+Hudson+and+Friends/Bedarra</url>
  </album>
  ...
</weeklyalbumchart>

user.getWeeklyArtistChart

Get an artist chart for a user profile, for a given date range. If no date range is supplied, it will return the most recent artist chart for this user.

Example URLs

Example URL: /2.0/?method=user.getweeklyartistchart&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The last.fm username to fetch the charts of.
from (Optional) : The date at which the chart should start from. See User.getWeeklyChartList for more.
to (Optional) : The date at which the chart should end on. See User.getWeeklyChartList for more.
api_key (Required)

Auth

Auth: None

Sample Response

<weeklyartistchart user="RJ" from="1212321600" to="1212926400">
  <artist rank="1">
    <name>David Hudson and Friends</name>
    <mbid>80e577ba-841f-43ba-9f32-72e7c1692336</mbid>
    <playcount>18</playcount>
    <url>http://www.last.fm/music/David+Hudson+and+Friends</url>
  </artist>
  ...
</weeklyartistchart>

user.getWeeklyChartList

Get a list of available charts for this user, expressed as date ranges which can be sent to the chart services.

Example URLs

Example URL: /2.0/?method=user.getweeklychartlist&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The last.fm username to fetch the charts list for.
api_key (Required)

Auth

Auth: None

Sample Response

<weeklychartlist user="RJ">
  <chart from="1108296002" to="1108900802"/>
  <chart from="1108900801" to="1109505601"/>
  ...
</weeklychartlist>

user.getWeeklyTrackChart

Get a track chart for a user profile, for a given date range. If no date range is supplied, it will return the most recent track chart for this user.

Example URLs

Example URL: /2.0/?method=user.getweeklytrackchart&user=rj&api_key=YOUR_API_KEY[&format=json]

Params

user (Required) : The last.fm username to fetch the charts of.
from (Optional) : The date at which the chart should start from. See User.getWeeklyChartList for more.
to (Optional) : The date at which the chart should end on. See User.getWeeklyChartList for more.
api_key (Required)

Auth

Auth: None

Sample Response

<weeklytrackchart user="joanofarctan" from="1212321600" to="1212926400">
  <track rank="1">
    <artist mbid="17b0d7f1-fad3-404e-87ae-874e6e158c3a">Dirk Leyers</artist>
    <name>Wellen</name>
    <mbid/>
    <playcount>3</playcount>
    <url>http://www.last.fm/music/Dirk+Leyers/_/Wellen</url>
  </track>
  ...
</weeklytrackchart>
