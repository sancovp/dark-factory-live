# understand-access_token

**CALL NUMBER:** `oauth_2_0_and_openid_connect.access_token : deep_oauth_2_0(1)`
**DEFINITION:** OAuth 2.0 credential presented to the resource server; opaque to clients but contains or references authorization state; scoped and time-limited.

Invoke this skill to understand `access_token` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **token_type** (d2): OAuth 2.0 parameter indicating how the access_token is to be presented to the resource server, typically Bearer, specifying the authorization scheme to use in requests.

### from `deep_oauth_2_0`
- **access_token_scope** (d1): The specific permission set granted to the access_token; a space-delimited string drawn from the scopes requested and approved during authorization; determines what resources and actions the token authorizes.

### from `oauth_2_0_and_openid_connect`
- **authorization_server** (d1): OAuth 2.0 server that authenticates the resource owner, obtains consent, and issues access tokens and optionally refresh tokens and ID tokens.
- **bearer_token** (d1): Token type defined in RFC 6750; any party possessing the token may use it; security relies on transport TLS and token secrecy.
- **expires_in** (d1): Integer seconds indicating access token lifetime; returned alongside access_token in token response.
- **grant_type** (d1): OAuth 2.0 parameter identifying which authorization flow is being used; values: authorization_code, client_credentials, refresh_token, password (deprecated).
- **introspection_endpoint** (d1): RFC 7662 endpoint allowing resource servers to validate access tokens; returns active status, scope, expiry, and other token metadata.
- **refresh_token** (d1): OAuth 2.0 credential used to obtain new access tokens without re-prompting the resource owner; long-lived and tied to the same scope as the original access token.
- **resource_indicator** (d1): RFC 8707 parameter specifying the target resource server URI; server issues access token scoped to that specific resource, not just the general API.
- **resource_server** (d1): Server hosting protected resources; validates incoming access tokens and returns resources only when tokens are valid and authorized.
- **token_endpoint** (d1): OAuth 2.0 endpoint accepting authorization_code or other grants and returning access_token, refresh_token, and optional id_token.

## CONSUMERS (what needs this)
`access_token_audience_restricted`, `access_token_expires_in`, `access_token_format_type`, `access_token_presented_to`, `oauth_2_0`, `token_endpoint`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*