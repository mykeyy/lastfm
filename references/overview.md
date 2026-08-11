# API overview

Use this file for Last.fm API basics that apply across namespaces.

## Endpoint and request shape

Last.fm documents the API root as:

```text
http://ws.audioscrobbler.com/2.0/
```

Send a `method` parameter in `package.method` form, followed by the parameters required by that method.

Example:

```text
http://ws.audioscrobbler.com/2.0/?method=album.getInfo&api_key=YOUR_API_KEY&artist=Cher&album=Believe&format=json
```

The API returns Last.fm XML by default. Send `format=json` when JSON is needed.

## Encoding and headers

* Encode API arguments as UTF-8.
* Use an RFC 3986 compliant HTTP client and encode URL parameters correctly.
* Send an identifiable `User-Agent` header on requests.

## Authentication

All write services require authentication. Read [authentication.md](authentication.md) before implementing a write method or any request that needs a Last.fm user session.

## Usage guidance

Last.fm asks clients to keep request volume reasonable. Avoid designs that make several requests per second continuously or call the API unnecessarily on every page load.

For commercial use, Last.fm asks developers to contact `partners@last.fm`.

## Current method namespaces

The official API currently exposes these method groups:

* `album.*`
* `artist.*`
* `auth.*`
* `chart.*`
* `geo.*`
* `library.*`
* `tag.*`
* `track.*`
* `user.*`

Use the matching `fm_api_<namespace>.txt` file for method parameters, authentication requirements, and response examples.

## Sources

* https://www.last.fm/api
* https://www.last.fm/api/intro
* https://www.last.fm/api/authentication
