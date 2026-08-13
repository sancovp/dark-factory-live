---
name: 0.3.1-understand-claims_request_object
description: "[0.3.1] Structured JSON object within the claims parameter containing claim preferences for id_token and userinfo endp"
---

# understand-claims_request_object

**CALL NUMBER:** `deep_openid_connect.claims_request_object`
**DEFINITION:** Structured JSON object within the claims parameter containing claim preferences for id_token and userinfo endpoints; root container for granular claim directives.

Invoke this skill to understand `claims_request_object` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_openid_connect`
- **essential_claim_directive** (d1): Claim marked as required by the relying party; identity provider must return this claim or return an error satisfying the acr_values if unable to fulfill.
- **id_token_claim_target** (d1): Claims section of claims_request specifying which claims the relying party wants embedded directly in the signed id_token JWT.
- **userinfo_claim_target** (d1): Claims section of claims_request specifying which claims the relying party wants returned from the userinfo_endpoint after token exchange.
- **voluntary_claim_directive** (d1): Claim requested by the relying party but not mandated; identity provider may omit based on policy, user consent, or availability without error.

## CONSUMERS (what needs this)
`claims_parameter`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
