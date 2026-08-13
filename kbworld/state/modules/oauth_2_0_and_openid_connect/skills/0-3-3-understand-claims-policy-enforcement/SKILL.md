---
name: 0.3.3-understand-claims_policy_enforcement
description: "[0.3.3] Identity provider rule set determining which claims can be released to a given relying_party based on client r"
---

# understand-claims_policy_enforcement

**CALL NUMBER:** `deep_openid_connect.claims_policy_enforcement`
**DEFINITION:** Identity provider rule set determining which claims can be released to a given relying_party based on client registration, user consent records, and data availability.

Invoke this skill to understand `claims_policy_enforcement` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_openid_connect`
- **partial_claims_fulfillment** (d1): Server response state where only a subset of requested claims are returned; occurs when policy or consent excludes some claims from the request.
- **claims_verification** (d2): Relying party validation that returned claims match what was requested in the claims_parameter, checking essential claims are present and values satisfy policy constraints.
- **essential_claim_directive** (d3): Claim marked as required by the relying party; identity provider must return this claim or return an error satisfying the acr_values if unable to fulfill.

## CONSUMERS (what needs this)
`identity_provider`, `user_claims_consent`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
