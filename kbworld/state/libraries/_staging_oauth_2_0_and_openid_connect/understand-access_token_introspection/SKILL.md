# understand-access_token_introspection

**CALL NUMBER:** `deep_oauth_2_0.access_token_introspection : oauth_2_0_and_openid_connect(1)`
**DEFINITION:** RFC 7662 mechanism by which a resource_server POSTs the access_token to the authorization_server introspection_endpoint to determine active status, scope, expiry, and metadata before serving the protected resource.

Invoke this skill to understand `access_token_introspection` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `oauth_2_0_and_openid_connect`
- **token_introspection** (d1): RFC 7662 introspection: protected endpoint where resource servers POST access_token to get its status, scope, expiration, and active flag.

## CONSUMERS (what needs this)
`access_token_hash`

---
*Projected from the `oauth 2 0 and openid connect` KB (174 concepts / 97 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*