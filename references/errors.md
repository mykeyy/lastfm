# Error handling

Use this file when code needs to interpret Last.fm API failures or decide whether to retry a request.

Always inspect the Last.fm response body. HTTP status alone is not enough to determine whether the API operation succeeded.

## Error codes

| Code | Meaning |
|---|---|
| `1` | This error does not exist |
| `2` | Invalid service |
| `3` | Invalid method |
| `4` | Authentication failed |
| `5` | Invalid format |
| `6` | Invalid parameters or a missing required parameter |
| `7` | Invalid resource specified |
| `8` | Operation failed, usually a backend failure |
| `9` | Invalid session key. Re-authenticate |
| `10` | Invalid API key |
| `11` | Service offline. Try again later |
| `12` | Subscribers only |
| `13` | Invalid method signature |
| `14` | Unauthorized token |
| `15` | Item unavailable for streaming |
| `16` | Service temporarily unavailable. Try again later |
| `17` | User must be logged in |
| `18` | Trial expired |
| `19` | This error does not exist |
| `20` | Not enough content |
| `21` | Not enough members |
| `22` | Not enough fans |
| `23` | Not enough neighbours |
| `24` | No peak radio |
| `25` | Radio not found |
| `26` | API key suspended |
| `27` | Deprecated request type |
| `29` | Rate limit exceeded |

## Retry guidance

A retry policy should depend on the method and error code instead of retrying every failure.

For scrobbling, Last.fm explicitly documents errors `11` and `16` as retryable. Error `9` requires a new session before retrying. Other scrobble errors generally mean the request should be corrected first.

Error `8` describes an operation failure and the official error list says to try again. Apply normal backoff rather than creating a tight retry loop.

Error `29` means the client is sending too many requests from its IP. Reduce request volume before retrying.

## Development errors

These usually indicate a bug or configuration problem rather than a transient failure:

* `2`, `3`, `5`, `6`, and `7`: method, service, format, parameter, or resource problem
* `10`: invalid API key
* `13`: bad request signature
* `14`: token has not been authorized
* `26`: API key is suspended
* `27`: request type is deprecated

## Sources

* https://www.last.fm/api/errorcodes
* https://www.last.fm/api/scrobbling
