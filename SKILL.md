---
name: lastfm-api
description: Reference skill for the Last.fm Music Discovery API. Use for Last.fm API methods, request parameters, authentication, request signing, scrobbling, now playing, error handling, rate limits, or implementation questions. Read only the relevant reference file for the task instead of loading the whole API reference.
---

# Last.fm API

Use this skill to answer questions or implement code against the Last.fm API without loading the full documentation into context.

## Workflow

1. Identify the smallest part of the API needed for the task.
2. Read only the matching reference file from the tables below.
3. For a method specific question, read that method namespace file before giving parameters or behavior.
4. For authenticated methods, also read [authentication.md](references/authentication.md).
5. For scrobbling or now playing, read [scrobbling.md](references/scrobbling.md) and [fm_api_track.txt](references/fm_api_track.txt).
6. For failures or retry logic, read [errors.md](references/errors.md).
7. Do not invent method names, parameters, defaults, error meanings, or authentication requirements. If the local snapshot and current official Last.fm documentation disagree, follow the official documentation.

## Core references

| Need | Read |
|---|---|
| API root, request format, encoding, JSON, usage rules | [overview.md](references/overview.md) |
| Web, desktop, mobile auth, session keys, `api_sig` | [authentication.md](references/authentication.md) |
| Scrobble rules, now playing, batching, retry behavior | [scrobbling.md](references/scrobbling.md) |
| Last.fm error codes and handling | [errors.md](references/errors.md) |

## Method namespaces

Read one namespace file unless the task crosses multiple resources.

| Namespace | Reference |
|---|---|
| `album.*` | [fm_api_album.txt](references/fm_api_album.txt) |
| `artist.*` | [fm_api_artist.txt](references/fm_api_artist.txt) |
| `auth.*` | [fm_api_auth.txt](references/fm_api_auth.txt) |
| `chart.*` | [fm_api_chart.txt](references/fm_api_chart.txt) |
| `geo.*` | [fm_api_geo.txt](references/fm_api_geo.txt) |
| `library.*` | [fm_api_library.txt](references/fm_api_library.txt) |
| `tag.*` | [fm_api_tag.txt](references/fm_api_tag.txt) |
| `track.*` | [fm_api_track.txt](references/fm_api_track.txt) |
| `user.*` | [fm_api_user.txt](references/fm_api_user.txt) |

## Rules that apply broadly

* Last.fm documents the API root as `http://ws.audioscrobbler.com/2.0/`.
* Encode arguments as UTF-8 and send an identifiable `User-Agent` header.
* XML is the default response format. Send `format=json` for JSON.
* Write services require authentication and use HTTP POST with form encoded parameters in the request body.
* Always inspect the Last.fm response body. HTTP 200 alone does not prove that the API operation succeeded.
* Parameter names are case sensitive where the method documentation says so.

## Answering implementation questions

Give the smallest correct request or code path for the user's task. State whether authentication is required, which HTTP method to use, and which parameters are required. Do not dump unrelated namespaces into the answer.