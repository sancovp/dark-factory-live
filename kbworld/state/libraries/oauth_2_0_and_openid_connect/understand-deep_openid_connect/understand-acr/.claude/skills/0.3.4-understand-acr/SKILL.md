---
name: 0.3.4-understand-acr
description: [0.3.4] Authentication Context Class: a statement about the authentication method used, the assurance level of the aut
---

# understand-acr

**CALL NUMBER:** `deep_openid_connect.acr : oauth_2_0_and_openid_connect(1)`
**DEFINITION:** Authentication Context Class: a statement about the authentication method used, the assurance level of the authentication event, and potentially the identity binding

Invoke this skill to understand `acr` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_openid_connect`
- **acr_claim** (d1): Claim in the id_token containing the ACR actually used by the OP to authenticate the user, returned to the RP

### from `oauth_2_0_and_openid_connect`
- **id_token** (d2): OIDC JWT containing subject identifier (sub), issuer, audience, expiration, authentication event metadata, and optionally user claims; always signed.

## CONSUMERS (what needs this)
`acr_processing`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
