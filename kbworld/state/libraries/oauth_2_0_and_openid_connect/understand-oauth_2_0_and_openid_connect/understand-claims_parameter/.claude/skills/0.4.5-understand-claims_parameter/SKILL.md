---
name: 0.4.5-understand-claims_parameter
description: [0.4.5] OIDC parameter requesting specific claims in id_token or userinfo response; server may return subset based on 
---

# understand-claims_parameter

**CALL NUMBER:** `oauth_2_0_and_openid_connect.claims_parameter : deep_openid_connect(5)`
**DEFINITION:** OIDC parameter requesting specific claims in id_token or userinfo response; server may return subset based on policy and user consent.

Invoke this skill to understand `claims_parameter` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_openid_connect`
- **claims_request_object** (d1): Structured JSON object within the claims parameter containing claim preferences for id_token and userinfo endpoints; root container for granular claim directives.
- **essential_claim_directive** (d2): Claim marked as required by the relying party; identity provider must return this claim or return an error satisfying the acr_values if unable to fulfill.
- **id_token_claim_target** (d2): Claims section of claims_request specifying which claims the relying party wants embedded directly in the signed id_token JWT.
- **userinfo_claim_target** (d2): Claims section of claims_request specifying which claims the relying party wants returned from the userinfo_endpoint after token exchange.
- **voluntary_claim_directive** (d2): Claim requested by the relying party but not mandated; identity provider may omit based on policy, user consent, or availability without error.

### from `oauth_2_0_and_openid_connect`
- **id_token** (d1): OIDC JWT containing subject identifier (sub), issuer, audience, expiration, authentication event metadata, and optionally user claims; always signed.
- **userinfo_endpoint** (d1): OIDC protected endpoint returning user claims as a JSON object; called with access_token after successful authentication; claims may overlap with id_token.

## CONSUMERS (what needs this)
`openid_connect`, `relying_party`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
