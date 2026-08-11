track.addTags

Tag an album using a list of user supplied tags.

Params

artist (Required) : The artist name
track (Required) : The track name
tags (Required) : A comma delimited list of user supplied tags to apply to this track. Accepts a maximum of 10 tags.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<lfm status="ok">
</lfm>

track.getCorrection

Use the last.fm corrections data to check whether the supplied track has a correction to a canonical track

Example URLs

Example URL: [/2.0/?method=track.getcorrection&artist=guns[&format=json]

Params

artist (Required) : The artist name to correct.
track (Required) : The track name to correct.
api_key (Required)

Auth

Auth: None

Sample Response

<corrections>
  <correction index="0" artistcorrected="1" trackcorrected="1">
    <track>
      <name>Mr. Brownstone</name>
      <mbid/>
      <url>www.last.fm/music/Guns+N%27+Roses/_/Mr.+Brownstone</url>
      <artist>
        <name>Guns N' Roses</name>
        <mbid>eeb1195b-f213-4ce1-b28c-8565211f8e43</mbid>
        <url>http://www.last.fm/music/Guns+N%27+Roses</url>
      </artist>
    </track>
  </correction>
</corrections>

track.getInfo

Get the metadata for a track on Last.fm using the artist/track name or a musicbrainz id.

Example URLs

Example URL: /2.0/?method=track.getInfo&api_key=YOUR_API_KEY&artist=cher&track=believe[&format=json]

Params

mbid (Optional) : The musicbrainz id for the track
track (Required (unless mbid)] : The track name
artist (Required (unless mbid)] : The artist name
username (Optional) : The username for the context of the request. If supplied, the user's playcount for this track and whether they have loved the track is included in the response.
autocorrect[0|1] (Optional) : Transform misspelled artist and track names into correct artist and track names, returning the correct version instead. The corrected artist and track name will be returned in the response.
api_key (Required)

Auth

Auth: None

Sample Response

<track>
  <id>1019817</id>
  <name>Believe</name>
  <mbid/>
  <url>http://www.last.fm/music/Cher/_/Believe</url>
  <duration>240000</duration>
  <streamable fulltrack="1">1</streamable>
  <listeners>69572</listeners>
  <playcount>281445</playcount>
  <artist>
    <name>Cher</name>
    <mbid>bfcc6d75-a6a5-4bc6-8282-47aec8531818</mbid>
    <url>http://www.last.fm/music/Cher</url>
  </artist>
  <album position="1">
    <artist>Cher</artist>
    <title>Believe</title>
    <mbid>61bf0388-b8a9-48f4-81d1-7eb02706dfb0</mbid>
    <url>http://www.last.fm/music/Cher/Believe</url>
    <image size="small">http://userserve-ak.last.fm/serve/34/8674593.jpg</image>
    <image size="medium">http://userserve-ak.last.fm/serve/64/8674593.jpg</image>
    <image size="large">http://userserve-ak.last.fm/serve/126/8674593.jpg</image>
  </album>
  <toptags>
    <tag>
      <name>pop</name>
      <url>http://www.last.fm/tag/pop</url>
    </tag>
    ...
  </toptags>
  <wiki>
    <published>Sun, 27 Jul 2008 15:44:58 +0000</published>
    <summary>...</summary>
    <content>...</content>
  </wiki>
</track>

Attributes

    duration : In milliseconds
    fulltrack : An attribute value of 1 indicates a full length preview is available for streaming
    streamable : A tag value of 1 indicates a 30 second preview of this song is available for streaming

track.getSimilar

Get the similar tracks for this track on Last.fm, based on listening data.

Example URLs

Example URL: /2.0/?method=track.getsimilar&artist=cher&track=believe&api_key=YOUR_API_KEY[&format=json]

Params

track (Required (unless mbid)] : The track name
artist (Required (unless mbid)] : The artist name
mbid (Optional) : The musicbrainz id for the track
autocorrect[0|1] (Optional) : Transform misspelled artist and track names into correct artist and track names, returning the correct version instead. The corrected artist and track name will be returned in the response.
limit (Optional) : Maximum number of similar tracks to return
api_key (Required)

Auth

Auth: None

Sample Response

<similartracks track="Believe" artist="Cher">
  <track>
    <name>Ray of Light</name>
    <mbid/>
    <match>10.95</match>
    <url>http://www.last.fm/music/Madonna/_/Ray+of+Light</url>
    <streamable fulltrack="0">1</streamable>
    <artist>
      <name>Madonna</name>
      <mbid>79239441-bfd5-4981-a70c-55c3f15c1287</mbid>
      <url>http://www.last.fm/music/Madonna</url>
    </artist>
    <image size="small">http://cdn.last.fm/coverart/50x50/1934.jpg</image>
    <image size="medium">http://cdn.last.fm/coverart/130x130/1934.jpg</image>
    <image size="large">http://cdn.last.fm/coverart/130x130/1934.jpg</image>
  </track>
  ...
</similartracks>

track.getTags

Get the tags applied by an individual user to a track on Last.fm. To retrieve the list of top tags applied to a track by all users use track.getTopTags.

Example URLs

Example URL: /2.0/?method=track.getTags&api_key=YOUR_API_KEY&artist=AC/DC&track=Hells+Bells&use...[&format=json]

Params

artist (Required (unless mbid)] : The artist name
track (Required (unless mbid)] : The track name
mbid (Optional) : The musicbrainz id for the track
autocorrect[0|1] (Optional) : Transform misspelled artist and track names into correct artist and track names, returning the correct version instead. The corrected artist and track name will be returned in the response.
user (Optional) : If called in non-authenticated mode you must specify the user to look up
api_key (Required)

Auth

Auth: None

Sample Response

<tags artist="Sally Shapiro" track="I'll be by your side">
  <tag>
    <name>swedish</name>
    <url>http://www.last.fm/tag/swedish</url>
  </tag>
  ...
</tags>

track.getTopTags

Get the top tags for this track on Last.fm, ordered by tag count. Supply either track & artist name or mbid.

Example URLs

Example URL: /2.0/?method=track.gettoptags&artist=radiohead&track=paranoid+android&api_key=YOUR...[&format=json]

Params

track (Required (unless mbid)] : The track name
artist (Required (unless mbid)] : The artist name
mbid (Optional) : The musicbrainz id for the track
autocorrect[0|1] (Optional) : Transform misspelled artist and track names into correct artist and track names, returning the correct version instead. The corrected artist and track name will be returned in the response.
api_key (Required)

Auth

Auth: None

Sample Response

<toptags artist="Cher" track="Believe">
  <tag>
    <name>pop</name>
    <count>97</count>
    <url>www.last.fm/tag/pop</url>
  </tag>
  <tag>
    <name>dance</name>
    <count>88</count>
    <url>www.last.fm/tag/dance</url>
  </tag>
  ...
</toptags>

track.love

Love a track for a user profile.

Params

track (Required) : A track name (utf8 encoded)
artist (Required) : An artist name (utf8 encoded)
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<lfm status="ok">
</lfm>

Errors

    8 : Operation Failed - Server Error. Please try again later.
    6 : Invalid track name supplied

track.removeTag

Remove a user's tag from a track.

Params

artist (Required) : The artist name
track (Required) : The track name
tag (Required) : A single user tag to remove from this track.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<lfm status="ok">
</lfm>

track.scrobble

Used to add a track-play to a user's profile. Scrobble a track, or a batch of tracks. Tracks are passed to the service using array notation for each of the below params, up to a maximum of 50 scrobbles per batch [0<=i<=49]. If you are only sending a single scrobble the array notation may be ommited. Note: Extra care should be taken while calculating the signature when using array notation as the parameter names MUST be sorted according to the ASCII table (i.e., artist[10] comes before artist[1]). It is important to not use the corrections returned by the now playing service as input for the scrobble request, unless they have been explicitly approved by the user. Parameter names are case sensitive.

Params

artist[i] (Required) : The artist name.
track[i] (Required) : The track name.
timestamp[i] (Required) : The time the track started playing, in UNIX timestamp format (integer number of seconds since 00:00:00, January 1st 1970 UTC). This must be in the UTC time zone.
album[i] (Optional) : The album name.
context[i] (Optional) : Sub-client version (not public, only enabled for certain API keys)
streamId[i] (Optional) : The stream id for this track received from the radio.getPlaylist service, if scrobbling Last.fm radio
chosenByUser[i] (Optional) : Set to 1 if the user chose this song, or 0 if the song was chosen by someone else (such as a radio station or recommendation service). Assumes 1 if not specified
trackNumber[i] (Optional) : The track number of the track on the album.
mbid[i] (Optional) : The MusicBrainz Track ID.
albumArtist[i] (Optional) : The album artist - if this differs from the track artist.
duration[i] (Optional) : The length of the track in seconds.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

Example for a single scrobble sent:
<?xml version='1.0' encoding='utf-8'?>
<lfm status="ok">
  <scrobbles accepted="1" ignored="0">
    <scrobble>
      <track corrected="0">Test Track</track>
      <artist corrected="0">Test Artist</artist>
      <album corrected="0"></album>
      <albumArtist corrected="0"></albumArtist>
      <timestamp>1287140447</timestamp>
      <ignoredMessage code="0"></ignoredMessage>
    </scrobble>
  </scrobbles>
</lfm>

Example for 2 scrobbles sent:
<?xml version='1.0' encoding='utf-8'?>
<lfm status="ok">
  <scrobbles accepted="2" ignored="0">
    <scrobble>
      <track corrected="0">Test Track 0</track>
      <artist corrected="0">Test Artist 0</artist>
      <album corrected="0"></album>
      <albumArtist corrected="0"></albumArtist>
      <timestamp>1287141093</timestamp>
      <ignoredMessage code="0"></ignoredMessage>
    </scrobble>
    <scrobble>
      <track corrected="0">Test Track 1</track>
      <artist corrected="0">Test Artist 1</artist>
      <album corrected="0"></album>
      <albumArtist corrected="0"></albumArtist>
      <timestamp>1287141093</timestamp>
      <ignoredMessage code="0"></ignoredMessage>
    </scrobble>
  </scrobbles>
</lfm>

Attributes

    accepted : Number of accepted scrobbles
    code : Ignored message codes:
        1: Artist was ignored
        2: Track was ignored
        3: Timestamp was too old
        4: Timestamp was too new
        5: Daily scrobble limit exceeded
    corrected : '1', if this track, artist or album name was automatically corrected, '0' otherwise
    ignored : Number of ignored scrobbles (see ignoredMessage for details)

track.search

Search for a track by track name. Returns track matches sorted by relevance.

Example URLs

Example URL: /2.0/?method=track.search&track=Believe&api_key=YOUR_API_KEY[&format=json]

Params

limit (Optional) : The number of results to fetch per page. Defaults to 30.
page (Optional) : The page number to fetch. Defaults to first page.
track (Required) : The track name
artist (Optional) : Narrow your search by specifying an artist.
api_key (Required)

Auth

Auth: None

Sample Response

<results for="Believe" xmlns:opensearch="http://a9.com/-/spec/opensearch/1.1/">
  <opensearch:Query role="request" searchTerms="Believe" startPage="1"/>
  <opensearch:totalResults>25329</opensearch:totalResults>
  <opensearch:startIndex>0</opensearch:startIndex>
  <opensearch:itemsPerPage>20</opensearch:itemsPerPage>
  <trackmatches>
    <track>
      <name>Believe</name>
      <artist>Disturbed</artist>
      <url>http://www.last.fm/music/Disturbed/_/Believe</url>
      <streamable fulltrack="0">1</streamable>
      <listeners>66068</listeners>
      <image size="small">...</image>
    </track>
    ...
  </trackmatches>
</results>

track.unlove

UnLove a track for a user profile.

Params

track (Required) : A track name (utf8 encoded)
artist (Required) : An artist name (utf8 encoded)
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Errors

    8 : Operation Failed - Server Error. Please try again later.
    6 : Invalid track name supplied

track.updateNowPlaying

Used to notify Last.fm that a user has started listening to a track. Parameter names are case sensitive.

Params

artist (Required) : The artist name.
track (Required) : The track name.
album (Optional) : The album name.
trackNumber (Optional) : The track number of the track on the album.
context (Optional) : Sub-client version (not public, only enabled for certain API keys)
mbid (Optional) : The MusicBrainz Track ID.
duration (Optional) : The length of the track in seconds.
albumArtist (Optional) : The album artist - if this differs from the track artist.
api_key (Required)
api_sig (Required)
sk (Required)

Auth

Auth: Required (POST)

Sample Response

<?xml version='1.0' encoding='utf-8'?>
<lfm status="ok">
  <nowplaying>
    <track corrected="0">Test Track</track>
    <artist corrected="0">Test Artist</artist>
    <album corrected="0"></album>
    <albumArtist corrected="0"></albumArtist>
    <ignoredMessage code="0"></ignoredMessage>
  </nowplaying>
</lfm>

Attributes

    code : Ignored message codes:
        1: Artist was ignored
        2: Track was ignored
        3: Timestamp was too old
        4: Timestamp was too new
        5: Daily scrobble limit exceeded
    corrected : '1', if this track, artist or album name was automatically corrected, '0' otherwise
