Last.fm authentication methods

This file is intentionally compact. It records the auth method boundary without embedding credential-shaped sample values or instructing an agent to collect account secrets.

auth.getSession

Purpose
Exchange an authorized request token for a Last.fm session key.

Required parameters
api_key
api_sig
token

Transport
Use HTTPS.

Security
Run the exchange in trusted application code. Treat the returned session key as a secret. Do not print, log, expose in frontend code, or commit it.

auth.getToken

Purpose
Create an unauthorized request token for the desktop authentication flow.

Required parameters
api_key
api_sig

Transport
Use HTTPS.

Security
The returned token is temporary and should only be used for the authorization flow.

auth.getMobileSession

Purpose
Last.fm documents this method for standalone clients that cannot use the normal browser flow.

Security boundary
This method requires direct account credential handling. An AI agent must not request, receive, store, print, or relay that credential. Prefer browser authorization. If an application must implement this legacy method, collect the credential inside the application's protected UI and send it directly to Last.fm over HTTPS POST without logging or persistence.

Implementation source
https://www.last.fm/api/show/auth.getMobileSession

General authentication references
https://www.last.fm/api/authentication
https://www.last.fm/api/authspec
