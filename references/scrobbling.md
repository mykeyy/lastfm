# Scrobbling

Use this file for `track.updateNowPlaying`, `track.scrobble`, batching, filtering, and retry behavior.

## Expected client behavior

For a track a user listens to, Last.fm recommends sending:

* `track.updateNowPlaying` when playback starts
* `track.scrobble` after the track qualifies as a scrobble

Scrobbling 2.0 is separate from the deprecated Submissions Protocol 1.2.1.

## When a track qualifies

A track should be scrobbled only when both conditions are met:

1. The track is longer than 30 seconds.
2. The user has listened to at least half of the track or 4 minutes, whichever happens first.

Once the threshold is reached, the scrobble may be sent. Many clients send it when playback finishes.

Do not infer metadata from filenames. Use structured metadata such as ID3 tags.

Do not automatically copy corrections returned by the now playing service into a later scrobble unless the user has approved those corrections.

## Now playing

`track.updateNowPlaying` is optional but recommended. Send it as soon as playback begins.

It is an authenticated write method and uses HTTP POST with form encoded parameters.

A failed now playing request should not be retried.

## Scrobble request

`track.scrobble` is an authenticated write method. Send it as HTTP POST with form encoded UTF-8 parameters.

Read [fm_api_track.txt](fm_api_track.txt) for the exact method parameters.

## Batch scrobbling

A request may contain up to 50 scrobbles. Batch requests are useful when sending cached scrobbles after a temporary failure.

Cached scrobbles should be sent in playback order before newer scrobbles.

## `chosenByUser`

Use `chosenByUser=false` when the user did not directly choose the music, such as a radio stream, recommendation service, or DJ selected program.

For ordinary user selected playback, the parameter can normally be omitted. If the source is ambiguous, Last.fm says not to send the value.

## Inspect the response body

Do not treat HTTP 200 as proof that the scrobble succeeded.

Inspect the Last.fm response status and error code. A request can receive HTTP 200 while the Last.fm operation itself failed.

For scrobbles:

* Error 11: retry later.
* Error 16: retry later.
* Error 9: obtain a new session, then retry.
* Other API errors generally mean the request needs to be corrected instead of retried unchanged.

Read [errors.md](errors.md) for the full error code table.

## Filtered scrobbles

A scrobble or now playing request may be ignored because of bad metadata while the overall response still reports success.

Ignored message codes documented by Last.fm:

| Code | Meaning |
|---|---|
| `0` | Passed all filters |
| `1` | Filtered artist |
| `2` | Filtered track |
| `3` | Timestamp too far in the past |
| `4` | Timestamp too far in the future |
| `5` | Maximum daily scrobbles exceeded |

In a batch request, Last.fm evaluates each scrobble separately. One ignored item does not imply that every item in the batch failed.

## Metadata corrections

Last.fm may return corrected artist, track, or album names. Corrections are advisory. They should not be applied to the user's metadata automatically.

## Sources

* https://www.last.fm/api/scrobbling
* https://www.last.fm/api/show/track.scrobble
* https://www.last.fm/api/show/track.updateNowPlaying
