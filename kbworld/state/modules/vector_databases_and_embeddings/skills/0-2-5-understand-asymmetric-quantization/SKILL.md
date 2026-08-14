---
name: 0.2.5-understand-asymmetric_quantization
description: "[0.2.5] A quantization scheme using both scale_factor and zero_point to map an arbitrary [min, max] float range to the"
---

# understand-asymmetric_quantization

**CALL NUMBER:** `deep_nearest_neighbor_sea.asymmetric_quantization`
**DEFINITION:** A quantization scheme using both scale_factor and zero_point to map an arbitrary [min, max] float range to the integer domain, enabling better utilization of the quantization range.

Invoke this skill to understand `asymmetric_quantization` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_nearest_neighbor_sea`
- **symmetric_quantization** (d1): A quantization scheme where the float range is centered at zero and only a scale factor is used; the zero point is implicitly zero; maps [-max_abs, max_abs] to [-127, 127].

## CONSUMERS (what needs this)
`dequantization`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
