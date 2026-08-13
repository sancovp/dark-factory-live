---
name: 0.4.6-understand-resource_server
description: "[0.4.6] Server hosting protected resources; validates incoming access tokens and returns resources only when tokens ar"
---

# understand-resource_server

**CALL NUMBER:** `oauth_2_0_and_openid_connect.resource_server`
**DEFINITION:** Server hosting protected resources; validates incoming access tokens and returns resources only when tokens are valid and authorized.

Invoke this skill to understand `resource_server` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `oauth_2_0_and_openid_connect`
- **introspection_endpoint** (d1): RFC 7662 endpoint allowing resource servers to validate access tokens; returns active status, scope, expiry, and other token metadata.

## CONSUMERS (what needs this)
`access_token`, `bearer_token`, `oauth_2_0`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
