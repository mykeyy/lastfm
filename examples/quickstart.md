# Quickstart examples

These examples are for developers reading the repository. Agents should still read the matching reference file before generating production code.

## Read an album as JSON

```sh
curl --get 'http://ws.audioscrobbler.com/2.0/' \
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
curl --get 'http://ws.audioscrobbler.com/2.0/' \
  --data-urlencode 'method=user.getRecentTracks' \
  --data-urlencode 'api_key=YOUR_API_KEY' \
  --data-urlencode 'user=LASTFM_USERNAME' \
  --data-urlencode 'limit=20' \
  --data-urlencode 'format=json' \
  -H 'User-Agent: your-app-name/1.0 contact@example.com'
```

## Sign an authenticated request

For authenticated calls, create `api_sig` from the parameters documented in `references/authentication.md`.

Conceptually:

```text
sort parameters by name
exclude format and callback
concatenate name + value with no separators
append shared secret
MD5 the UTF-8 string
```

Never put the shared secret in frontend code or commit it to a repository.

## Submit a scrobble

A scrobble uses HTTP POST and requires a session key plus a valid signature.

```sh
curl -X POST 'http://ws.audioscrobbler.com/2.0/' \
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

Before sending a scrobble, read `references/scrobbling.md` for the playback threshold, retry rules, and filtering behavior.
