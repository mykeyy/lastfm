---
name: lastfm-api
description: Comprehensive reference for the Last.fm Music Discovery API. Use this skill when the user asks about Last.fm API methods, authentication flows, scrobbling, signing requests, error codes, or how to build something with the Last.fm API. Also use it when helping edit or maintain the local API documentation files in the lastfm workspace.
---

# Last.fm API Reference Skill

This skill contains everything needed to answer questions about and work with the Last.fm API.

## Documentation Files

The full API reference docs are in the `references/` folder alongside this skill:

| File | Contents |
|---|---|
| `references/fm_a_main.txt` | Overview, all 3 auth flows, scrobbling guide, signing calls, API ToS |
| `references/fm_api_album.txt` | album.* methods |
| `references/fm_api_artist.txt` | artist.* methods |
| `references/fm_api_auth.txt` | auth.* methods |
| `references/fm_api_chart.txt` | chart.* methods |
| `references/fm_api_geo.txt` | geo.* methods |
| `references/fm_api_library.txt` | library.* methods |
| `references/fm_api_tag.txt` | tag.* methods |
| `references/fm_api_track.txt` | track.* methods (incl. scrobble + nowplaying) |
| `references/fm_api_user.txt` | user.* methods |

Always read the relevant reference file before answering specific method questions.

---

## API Basics

**Base URL:** `http://ws.audioscrobbler.com/2.0/`

**Request format:** REST — send a `method` parameter (e.g. `album.getinfo`) plus method-specific params.

**Response format:** XML by default. Append `&format=json` for JSON.

**Encoding:** All arguments must be UTF-8. Use a User-Agent header on all requests.

**Example GET request:**
```
GET http://ws.audioscrobbler.com/2.0/?method=album.getinfo&api_key=YOUR_KEY&artist=Cher&album=Believe&format=json
```

**Example URL pattern used in docs:**
```
/2.0/?method=album.getinfo&api_key=YOUR_API_KEY&artist=Cher&album=Believe[&format=json]
```
The `[&format=json]` suffix is optional — omit for XML.

---

## Authentication

There are 3 authentication flows. All write services require auth. Read-only methods do not.

### Auth Type Summary

| Method | When to use |
|---|---|
| Web app | You have a callback URL; user logs in via browser redirect |
| Desktop app | No callback URL; user logs in via browser then returns to app |
| Mobile app | You have the user's password; use `auth.getMobileSession` over HTTPS POST |

### Signing Calls (all flows share this)

To generate `api_sig`:
1. Take all parameters for the call **except** `format` and `callback`.
2. Sort them alphabetically by parameter name.
3. Concatenate as `<name><value><name><value>...` (no separators).
4. Append your shared secret.
5. MD5 hash the whole string.

Example for `auth.getSession`:
```
api_sig = md5("api_keyXXXXmethodauth.getSessiontokenYYYYmysecret")
```

The result is a 32-character hex string.

> **Important:** When using array notation (e.g. for batch scrobbles), parameters MUST be sorted by ASCII order — `artist[10]` sorts before `artist[1]`.

### Session Keys

- Session keys are **infinite lifetime** by default.
- Store them securely — users can revoke them in their Last.fm settings.
- Auth tokens (used to get a session) expire after **60 minutes** and can only be used **once**.

### Web App Flow
1. Redirect user to `http://www.last.fm/api/auth/?api_key=XXX` (optionally `&cb=YOUR_CALLBACK`)
2. Last.fm redirects back to your callback with `?token=YYYY`
3. Call `auth.getSession` with `api_key`, `token`, `api_sig` → receive `sk` (session key)
4. Sign all authenticated calls with `api_key`, `sk`, `api_sig`

### Desktop App Flow
1. Call `auth.getToken` with `api_key` + `api_sig` → receive `token`
2. Open browser to `http://www.last.fm/api/auth/?api_key=XXX&token=YYY`
3. User grants access, returns to app
4. Call `auth.getSession` with `api_key`, `token`, `api_sig` → receive `sk`
5. Sign all authenticated calls with `api_key`, `sk`, `api_sig`

### Mobile App Flow
1. Call `auth.getMobileSession` via **HTTPS POST** with `username`, `password`, `api_key`, `api_sig`
2. Receive `sk` directly (no browser redirect needed)
3. Sign all authenticated calls with `api_key`, `sk`, `api_sig`

---

## Common Parameters

These appear in many methods:

| Param | Meaning |
|---|---|
| `api_key` | Your 32-char API key (always required) |
| `api_sig` | MD5 signature (required for auth'd calls and write services) |
| `sk` | Session key from auth flow (required for write services) |
| `autocorrect[0\|1]` | Fix misspelled artist/track names automatically |
| `mbid` | MusicBrainz ID — can substitute for artist+track/album name |
| `limit` | Results per page (default usually 30 or 50) |
| `page` | Page number (1-indexed) |
| `format` | `json` or omit for XML |
| `lang` | ISO 639 alpha-2 language code (for bio/wiki text) |

---

## Method Index

### album.*
| Method | Auth | Description |
|---|---|---|
| `album.addTags` | Required (POST) | Tag an album with up to 10 user tags |
| `album.getInfo` | None | Get metadata + tracklist for an album |
| `album.getTags` | None | Get tags applied by a specific user to an album |
| `album.getTopTags` | None | Get top tags for an album across all users |
| `album.removeTag` | Required (POST) | Remove a user's tag from an album |
| `album.search` | None | Search for albums by name |

### artist.*
| Method | Auth | Description |
|---|---|---|
| `artist.addTags` | Required (POST) | Tag an artist with user tags |
| `artist.getCorrection` | None | Check if artist name has a canonical correction |
| `artist.getInfo` | None | Get artist metadata and biography |
| `artist.getSimilar` | None | Get similar artists based on listening data |
| `artist.getTags` | None | Get tags applied by a user to an artist |
| `artist.getTopAlbums` | None | Get top albums for an artist |
| `artist.getTopTags` | None | Get top tags for an artist |
| `artist.getTopTracks` | None | Get top tracks for an artist |
| `artist.removeTag` | Required (POST) | Remove a user's tag from an artist |
| `artist.search` | None | Search for an artist by name |

### auth.*
| Method | Auth | Description |
|---|---|---|
| `auth.getMobileSession` | None (but needs HTTPS POST) | Get session key using username + password |
| `auth.getSession` | None | Exchange an auth token for a session key |
| `auth.getToken` | None | Get an unauthorized request token (desktop apps) |

### chart.*
| Method | Auth | Description |
|---|---|---|
| `chart.getTopArtists` | None | Get the top artists chart |
| `chart.getTopTags` | None | Get the top tags chart |
| `chart.getTopTracks` | None | Get the top tracks chart |

### geo.*
| Method | Auth | Description |
|---|---|---|
| `geo.getTopArtists` | None | Get top artists by country |
| `geo.getTopTracks` | None | Get top tracks by country |

### library.*
| Method | Auth | Description |
|---|---|---|
| `library.getArtists` | None | Get artists in a user's library |

### tag.*
| Method | Auth | Description |
|---|---|---|
| `tag.getInfo` | None | Get metadata for a tag |
| `tag.getSimilar` | None | Get similar tags |
| `tag.getTopAlbums` | None | Get top albums for a tag |
| `tag.getTopArtists` | None | Get top artists for a tag |
| `tag.getTopTags` | None | Get the overall top tags on Last.fm |
| `tag.getTopTracks` | None | Get top tracks for a tag |
| `tag.getWeeklyChartList` | None | Get available weekly chart date ranges for a tag |

### track.*
| Method | Auth | Description |
|---|---|---|
| `track.addTags` | Required (POST) | Tag a track with user tags |
| `track.getCorrection` | None | Check if track/artist name has a canonical correction |
| `track.getInfo` | None | Get metadata for a track |
| `track.getSimilar` | None | Get similar tracks |
| `track.getTags` | None | Get tags applied by a user to a track |
| `track.getTopTags` | None | Get top tags for a track |
| `track.love` | Required (POST) | Love a track on a user's profile |
| `track.removeTag` | Required (POST) | Remove a user's tag from a track |
| `track.scrobble` | Required (POST) | Submit a track play to a user's history |
| `track.search` | None | Search for tracks by name |
| `track.unlove` | Required (POST) | Unlove a track |
| `track.updateNowPlaying` | Required (POST) | Notify Last.fm a user started listening |

### user.*
| Method | Auth | Description |
|---|---|---|
| `user.getFriends` | None | Get friends of a user |
| `user.getInfo` | None | Get a user's profile info |
| `user.getLovedTracks` | None | Get a user's loved tracks |
| `user.getPersonalTags` | None | Get tracks/artists/albums a user has tagged |
| `user.getRecentTracks` | None | Get a user's recent listening history |
| `user.getTopAlbums` | None | Get a user's top albums |
| `user.getTopArtists` | None | Get a user's top artists |
| `user.getTopTags` | None | Get a user's top tags |
| `user.getTopTracks` | None | Get a user's top tracks |
| `user.getWeeklyAlbumChart` | None | Get weekly album chart for a user |
| `user.getWeeklyArtistChart` | None | Get weekly artist chart for a user |
| `user.getWeeklyChartList` | None | Get available chart date ranges for a user |
| `user.getWeeklyTrackChart` | None | Get weekly track chart for a user |

---

## Scrobbling Guide

### When to Scrobble
A track qualifies for scrobbling when **both** are true:
- Track duration > 30 seconds
- User has listened for at least **50% of the track duration** OR **4 minutes** (whichever comes first)

### Now Playing vs Scrobble
- **`track.updateNowPlaying`** — Send immediately when a track starts. Optional but recommended. Shows on the user's profile in real time. Failed nowplaying requests should **not** be retried.
- **`track.scrobble`** — Send when scrobble conditions are met (usually at end of track). Failed scrobbles should be cached and retried.

### Batch Scrobbling
Send up to **50 scrobbles** in one request using array notation:
```
artist[0]=Cher&track[0]=Believe&timestamp[0]=1234567890
artist[1]=Madonna&track[1]=Ray+of+Light&timestamp[1]=1234568130
```
Timestamps must be **UTC Unix timestamps**. Sort array params by ASCII order when signing.

### chosenByUser Parameter
Set to `0` when the track was chosen by someone other than the user (e.g., radio, recommendations). Otherwise omit it (defaults to `1`).

### Do NOT
- Determine track metadata from filenames — use ID3 tags or structured sources only.
- Use now-playing corrections as scrobble input unless explicitly approved by the user.

### Scrobble Ignored Message Codes
| Code | Meaning |
|---|---|
| 0 | None — passed all filters |
| 1 | Filtered artist (e.g. "Unknown Artist") |
| 2 | Filtered track |
| 3 | Timestamp too far in the past |
| 4 | Timestamp too far in the future |
| 5 | Daily scrobble limit exceeded |

---

## Error Handling

### Response Structure
Always inspect the **response body** — a `200 OK` HTTP status does NOT mean the request succeeded.

Check the `<lfm status="...">` attribute:
- `"ok"` → success
- `"failed"` → inspect `<error code="N">` for details

### Retry Logic for Scrobbles
| Error | Action |
|---|---|
| Code 9 (Invalid session key) | Re-authenticate, then retry |
| Code 11 (Service Offline) | Retry later |
| Code 16 (Temporarily unavailable) | Retry later |
| Any other code | Do NOT retry — fix the request |

### Standard Error Codes (all methods)
| Code | Meaning |
|---|---|
| 2 | Invalid service — this service does not exist |
| 3 | Invalid Method — no method with that name |
| 4 | Authentication Failed — no permission to access |
| 5 | Invalid format — service doesn't exist in that format |
| 6 | Invalid parameters — missing required parameter |
| 7 | Invalid resource specified |
| 8 | Operation failed — something else went wrong |
| 9 | Invalid session key — please re-authenticate |
| 10 | Invalid API key — must be granted a valid key |
| 11 | Service Offline — temporarily offline, try again |
| 13 | Invalid method signature supplied |
| 16 | Temporary error / service temporarily unavailable |
| 26 | Suspended API key — account suspended |
| 29 | Rate limit exceeded — too many requests from your IP |

---

## Tips & Gotchas

- **Rate limits:** Don't hammer the API. Avoid calling on every page load. Your key can be suspended.
- **Write services** always require HTTP POST with form-urlencoded body. Never GET for write operations.
- **HTTPS required** for `auth.getMobileSession` specifically.
- **`autocorrect=1`** is handy — it fixes misspelled artist/track names and returns the corrected name in the response.
- **`mbid`** (MusicBrainz ID) is usually more reliable than artist+track name strings when you have it.
- **`duration`** in `track.getInfo` is in **milliseconds**; in `track.scrobble` it's in **seconds**.
- The `format=json` parameter is **excluded** from signature calculation.
- Commercial or research use requires contacting partners@last.fm before use.
