# Authentication

Use this file when a task needs a Last.fm user session, request signing, or an authenticated write method.

## What you need

A Last.fm API account provides an API key and a shared secret. The secret is used to create `api_sig` values and should not be exposed to clients that cannot keep it private.

All write services require authentication.

## Web application flow

1. Send the user to Last.fm's authorization page with your API key.
2. Last.fm redirects to the configured callback URL with a `token` after the user grants access.
3. Call `auth.getSession` with `api_key`, `token`, and `api_sig`.
4. Store the returned session key `sk` securely.
5. Include `api_key`, `sk`, and `api_sig` on authenticated calls.

Authorization URL pattern:

```text
http://www.last.fm/api/auth/?api_key=YOUR_API_KEY
```

A different callback may be supplied with the `cb` query parameter when needed.

## Desktop application flow

1. Call `auth.getToken` with `api_key` and `api_sig`.
2. Open the Last.fm authorization URL with both the API key and token.
3. Wait for the user to approve access in the browser.
4. Call `auth.getSession` with the authorized token.
5. Store the returned session key and use it for authenticated calls.

Authorization URL pattern:

```text
http://www.last.fm/api/auth/?api_key=YOUR_API_KEY&token=TOKEN
```

## Mobile authentication flow

`auth.getMobileSession` accepts the user's Last.fm username and password directly.

This method must use HTTPS and HTTP POST.

Required parameters:

* `username`
* `password`
* `api_key`
* `api_sig`

The response contains a session key that can be used for authenticated calls.

Prefer a browser based flow when the application can support it. The mobile flow handles the user's plaintext password and therefore requires more care.

## Tokens and sessions

Authentication tokens are specific to the API account. They are valid for 60 minutes and can only be consumed once when creating a session.

Session keys have an infinite lifetime by default. A user can revoke access later from Last.fm settings, which invalidates the session.

## Signing requests

To create `api_sig`:

1. Take all parameters that are part of the API call.
2. Exclude `format` and `callback`.
3. Sort the remaining parameters alphabetically by parameter name.
4. Concatenate them as `<name><value>` with no separators.
5. Append the shared secret.
6. MD5 hash the resulting UTF-8 string.

Example input for `auth.getSession`:

```text
api_keyYOUR_API_KEYmethodauth.getSessiontokenTOKENYOUR_SHARED_SECRET
```

The result is a 32 character hexadecimal MD5 digest.

Authenticated calls normally include:

* `api_key`
* `sk`
* `api_sig`

Read [fm_api_auth.txt](fm_api_auth.txt) for the exact parameters and response fields of `auth.getToken`, `auth.getSession`, and `auth.getMobileSession`.

## Sources

* https://www.last.fm/api/authentication
* https://www.last.fm/api/authspec
* https://www.last.fm/api/webauth
* https://www.last.fm/api/mobileauth
