# understand-openid_connect

**CALL NUMBER:** `oauth_2_0_and_openid_connect.openid_connect : deep_openid_connect(8)`
**DEFINITION:** Identity layer on top of OAuth 2.0 (OIDC 1.0, OIDC Core spec) adding ID tokens as JWTs, userinfo endpoint, and standardized identity claims for authentication use cases.

Invoke this skill to understand `openid_connect` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_openid_connect`
- **claims_request_object** (d2): Structured JSON object within the claims parameter containing claim preferences for id_token and userinfo endpoints; root container for granular claim directives.
- **claims_policy_enforcement** (d2): Identity provider rule set determining which claims can be released to a given relying_party based on client registration, user consent records, and data availability.
- **essential_claim_directive** (d3): Claim marked as required by the relying party; identity provider must return this claim or return an error satisfying the acr_values if unable to fulfill.
- **id_token_claim_target** (d3): Claims section of claims_request specifying which claims the relying party wants embedded directly in the signed id_token JWT.
- **userinfo_claim_target** (d3): Claims section of claims_request specifying which claims the relying party wants returned from the userinfo_endpoint after token exchange.
- **voluntary_claim_directive** (d3): Claim requested by the relying party but not mandated; identity provider may omit based on policy, user consent, or availability without error.
- **partial_claims_fulfillment** (d3): Server response state where only a subset of requested claims are returned; occurs when policy or consent excludes some claims from the request.
- **claims_verification** (d4): Relying party validation that returned claims match what was requested in the claims_parameter, checking essential claims are present and values satisfy policy constraints.

### from `oauth_2_0_and_openid_connect`
- **acr_values** (d1): OIDC authentication context class reference values requested by RP; ordered list the OP attempts to satisfy (e.g. 'urn:oasis:names:tc:SAML:2.0:ac:classes:Password').
- **claims_parameter** (d1): OIDC parameter requesting specific claims in id_token or userinfo response; server may return subset based on policy and user consent.
- **discovery_document** (d1): Well-known URL pattern (RFC 5785) at /.well-known/openid-configuration exposing OIDC provider configuration JSON.
- **id_token** (d1): OIDC JWT containing subject identifier (sub), issuer, audience, expiration, authentication event metadata, and optionally user claims; always signed.
- **id_token_hint** (d1): OIDC parameter carrying a previously issued id_token; OP uses it to infer the user and potentially skip re-authentication or pre-fill consent.
- **identity_provider** (d1): OIDC term for the authorization server that also acts as the authentication authority; issues id_token and exposes userinfo.
- **issuer** (d1): String identifier (typically URL) in id_token and access_token; relying parties validate tokens were issued by a trusted, matching issuer.
- **jwks_uri** (d1): URL in discovery document pointing to JSON Web Key Set (RFC 7517) containing public keys used to verify id_token and access_token signatures.
- **login_hint** (d1): OIDC parameter suggesting which account the user should log in with; may be email, username, or account selector hint.
- **max_age** (d1): OIDC parameter specifying maximum seconds since last authentication; if elapsed, OP must re-authenticate before issuing id_token.
- **openid_configuration** (d1): Discovery document served at /.well-known/openid-configuration; machine-readable metadata listing endpoints, supported features, and server capabilities.
- **pairwise_identifiers** (d1): OIDC subject identifier strategy where each RP receives a different sub for the same user, preventing cross-RP user correlation.
- **prompt_parameter** (d1): OIDC parameter controlling user interaction: none (no prompt, error if needed), login (force re-auth), consent (show approval screen), select_account.
- **relying_party** (d1): OIDC term for the client application that relies on the identity provider's id_token for user authentication.
- **subject_identifier** (d1): The 'sub' claim in id_token: a unique stable identifier assigned by the identity provider to the user; pairwise vs public based on RP.
- **ui_locales** (d1): OIDC parameter indicating user's preferred languages for the consent/userinfo UI; BCP 47 language tag list.
- **userinfo_endpoint** (d1): OIDC protected endpoint returning user claims as a JSON object; called with access_token after successful authentication; claims may overlap with id_token.

## CONSUMERS (what needs this)
`oauth_2_0`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*