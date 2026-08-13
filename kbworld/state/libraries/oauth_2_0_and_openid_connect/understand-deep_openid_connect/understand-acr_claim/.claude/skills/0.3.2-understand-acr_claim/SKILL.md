---
name: 0.3.2-understand-acr_claim
description: [0.3.2] Claim in the id_token containing the ACR actually used by the OP to authenticate the user, returned to the RP
---

# understand-acr_claim

**CALL NUMBER:** `deep_openid_connect.acr_claim : oauth_2_0_and_openid_connect(1)`
**DEFINITION:** Claim in the id_token containing the ACR actually used by the OP to authenticate the user, returned to the RP

Invoke this skill to understand `acr_claim` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `oauth_2_0_and_openid_connect`
- **id_token** (d1): OIDC JWT containing subject identifier (sub), issuer, audience, expiration, authentication event metadata, and optionally user claims; always signed.

## CONSUMERS (what needs this)
`acr`, `acr_claim_value`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
