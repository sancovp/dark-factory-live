---
name: 0.3.2-understand-mode_bit_format
description: [0.3.2] Base-8 positional numeral system used to encode file mode; Git stores exactly 6 octal digits representing 18 b
---

# understand-mode_bit_format

**CALL NUMBER:** `deep_tree_object.mode_bit_format`
**DEFINITION:** Base-8 positional numeral system used to encode file mode; Git stores exactly 6 octal digits representing 18 bits of mode information.

Invoke this skill to understand `mode_bit_format` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tree_object`
- **mode_zero_padding** (d1): The leading zero in modes like 100644 and 040000 ensures consistent 6-digit width; the zero fills the third octal digit reserved for special file type flags.

## CONSUMERS (what needs this)
`tree_entry_mode`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
