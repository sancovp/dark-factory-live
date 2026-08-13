# understand-oauth_2_0

**CALL NUMBER:** `oauth_2_0_and_openid_connect.oauth_2_0 : deep_openid_connect(8), deep_oauth_2_0(1)`
**DEFINITION:** IETF RFC 6749 authorization framework enabling third-party application access to protected resources without sharing credentials; defines four grant types and token issuance via authorization and token endpoints.

Invoke this skill to understand `oauth_2_0` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **token_type** (d2): OAuth 2.0 parameter indicating how the access_token is to be presented to the resource server, typically Bearer, specifying the authorization scheme to use in requests.

### from `deep_oauth_2_0`
- **access_token_scope** (d2): The specific permission set granted to the access_token; a space-delimited string drawn from the scopes requested and approved during authorization; determines what resources and actions the token authorizes.

### from `deep_openid_connect`
- **claims_request_object** (d3): Structured JSON object within the claims parameter containing claim preferences for id_token and userinfo endpoints; root container for granular claim directives.
- **claims_policy_enforcement** (d3): Identity provider rule set determining which claims can be released to a given relying_party based on client registration, user consent records, and data availability.
- **essential_claim_directive** (d4): Claim marked as required by the relying party; identity provider must return this claim or return an error satisfying the acr_values if unable to fulfill.
- **id_token_claim_target** (d4): Claims section of claims_request specifying which claims the relying party wants embedded directly in the signed id_token JWT.
- **userinfo_claim_target** (d4): Claims section of claims_request specifying which claims the relying party wants returned from the userinfo_endpoint after token exchange.
- **voluntary_claim_directive** (d4): Claim requested by the relying party but not mandated; identity provider may omit based on policy, user consent, or availability without error.
- **partial_claims_fulfillment** (d4): Server response state where only a subset of requested claims are returned; occurs when policy or consent excludes some claims from the request.
- **claims_verification** (d5): Relying party validation that returned claims match what was requested in the claims_parameter, checking essential claims are present and values satisfy policy constraints.

### from `oauth_2_0_and_openid_connect`
- **access_token** (d1): OAuth 2.0 credential presented to the resource server; opaque to clients but contains or references authorization state; scoped and time-limited.
- **authorization_code** (d1): Short-lived credential exchanged for tokens at the token endpoint; exists to keep tokens out of the user-agent (browser) history and address bar.
- **authorization_code_flow** (d1): Primary OAuth 2.0 flow for web apps with a server-side component; uses authorization_endpoint then token_endpoint with the returned code.
- **authorization_endpoint** (d1): OAuth 2.0 endpoint where the resource owner authenticates and grants consent; returns authorization_code via redirect or form_post response.
- **authorization_server** (d1): OAuth 2.0 server that authenticates the resource owner, obtains consent, and issues access tokens and optionally refresh tokens and ID tokens.
- **authorization_server_metadata** (d1): RFC 8414 metadata document at /.well-known/oauth-authorization-server; lists server capabilities, endpoint URLs, grant types, and supported features.
- **bearer_token** (d1): Token type defined in RFC 6750; any party possessing the token may use it; security relies on transport TLS and token secrecy.
- **ciba** (d1): RFC 9002 Client Initiated Backchannel Authentication; user initiates auth from a device, push notification is sent to their phone, RP polls for result.
- **client** (d1): Application making protected resource requests on behalf of the resource owner; classified as confidential (can hold secrets) or public (cannot).
- **client_credentials_grant** (d1): OAuth 2.0 flow where the client authenticates with its own credentials and receives an access token representing the client itself (no user).
- **client_id** (d1): Public identifier assigned by the authorization server to a client; used to identify which application is requesting authorization.
- **client_secret** (d1): Confidential credential held by the client; used with authorization_code or client_credentials flows to authenticate the client to the token endpoint.
- **device_flow** (d1): RFC 8628 OAuth 2.0 Device Authorization Grant; user enters a code on a separate device while the client polls for authorization completion.
- **dpop_proof** (d1): RFC 9449 Demonstrated Proof-of-Possession; client signs a JWT with its private key and includes DPoP header in token requests to bind the token to the key.
- **expires_in** (d1): Integer seconds indicating access token lifetime; returned alongside access_token in token response.
- **grant_type** (d1): OAuth 2.0 parameter identifying which authorization flow is being used; values: authorization_code, client_credentials, refresh_token, password (deprecated).
- **introspection_endpoint** (d1): RFC 7662 endpoint allowing resource servers to validate access tokens; returns active status, scope, expiry, and other token metadata.
- **openid_connect** (d1): Identity layer on top of OAuth 2.0 (OIDC 1.0, OIDC Core spec) adding ID tokens as JWTs, userinfo endpoint, and standardized identity claims for authentication use cases.
- **pkce** (d1): RFC 7636 Proof Key for Code Exchange; mitigates authorization code interception by requiring code_verifier and code_challenge from the client.
- **pushed_authorization_request** (d1): RFC 9126 PAR: client POSTs authorization request parameters to par_endpoint first, receives request_uri for use at authorization_endpoint.
- **redirect_uri** (d1): Callback URL the authorization server redirects to after consent; must be pre-registered with the authorization server and must match exactly.
- **refresh_token** (d1): OAuth 2.0 credential used to obtain new access tokens without re-prompting the resource owner; long-lived and tied to the same scope as the original access token.
- **resource_indicator** (d1): RFC 8707 parameter specifying the target resource server URI; server issues access token scoped to that specific resource, not just the general API.
- **resource_owner** (d1): Entity capable of granting access to a protected resource; typically the end-user who authenticates to authorize the client's request.
- **resource_server** (d1): Server hosting protected resources; validates incoming access tokens and returns resources only when tokens are valid and authorized.

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*