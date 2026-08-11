# Quickstart examples

These examples use placeholders only. Keep real API secrets and session keys out of chat, source control, logs, and frontend code.

## Read an album as JSON

```sh
curl --get 'https://ws.audioscrobbler.com/2.0/' \
  --data-urlencode 'method=album.getInfo' \
  --data-urlencode 'api_key=YOUR_API_KEY' \
  --data-urlencode 'artist=Cher' \
  --data-urlencode 'album=Believe' \
  --data-urlencode 'format=json' \
  -H 'User-Agent: your-app-name/1.0 contact@example.com'
```

`album.getInfo` is a read method, so a Last.fm user session is not required.

## Read recent tracks

```sh
curl --get 'https://ws.audioscrobbler.com/2.0/' \
  --data-urlencode 'method=user.getRecentTracks' \
  --data-urlencode 'api_key=YOUR_API_KEY' \
  --data-urlencode 'user=LASTFM_USERNAME' \
  --data-urlencode 'limit=20' \
  --data-urlencode 'format=json' \
  -H 'User-Agent: your-app-name/1.0 contact@example.com'
```

## Authenticated requests

Generate `api_sig` only inside trusted application code. Read `references/authentication.md` before implementing authenticated methods.

Do not paste a real shared API secret or session key into a shell example, agent conversation, source file, or issue report.

## Submit a scrobble

A scrobble uses HTTPS POST and requires a session key plus a valid signature.

```sh
curl -X POST 'https://ws.audioscrobbler.com/2.0/' \
  --data-urlencode 'method=track.scrobble' \
  --data-urlencode 'artist=Cher' \
  --data-urlencode 'track=Believe' \
  --data-urlencode 'timestamp=UNIX_TIMESTAMP_UTC' \
  --data-urlencode 'api_key=YOUR_API_KEY' \
  --data-urlencode 'sk=YOUR_SESSION_KEY' \
  --data-urlencode 'api_sig=CALCULATED_SIGNATURE' \
  --data-urlencode 'format=json' \
  -H 'User-Agent: your-app-name/1.0 contact@example.com'
```

Before sending a scrobble, read `references/scrobbling.md` for playback thresholds, retry rules, and filtering behavior.
