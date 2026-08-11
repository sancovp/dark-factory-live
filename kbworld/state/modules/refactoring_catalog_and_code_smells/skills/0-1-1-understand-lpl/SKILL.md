---
name: 0.1.1-understand-lpl
description: "[0.1.1] long_parameter_list: a method or function whose parameter signature exceeds a comfortable cognitive threshold,"
---

# understand-lpl

**CALL NUMBER:** `deep_bloaters.lpl`
**DEFINITION:** long_parameter_list: a method or function whose parameter signature exceeds a comfortable cognitive threshold, typically citing more than three or four distinct arguments, making the interface awkward to call and maintain

Invoke this skill to understand `lpl` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_bloaters`
- **lpl_caller_clone** (d1): caller_signature_clone: a pattern where multiple call sites pass the same subset of parameters to a method, signaling that those parameters form a logical unit awaiting formalization as an object
- **lpl_change_ripple** (d1): signature_change_ripple: the cascade of modifications required across all call sites when a long parameter list is altered, representing the brittleness cost of the current design
- **lpl_cognitive_load** (d1): parameter_cognitive_load: the mental effort required to recall the order, type, and purpose of each argument at every call site, which degrades rapidly as parameter count increases
- **lpl_data_clump_rel** (d1): data_clump_association: the kinship between long_parameter_list and data_clump, where the same fields appear together repeatedly across methods and constructors, both pointing toward a missing abstraction
- **lpl_extract_helper** (d1): extract_parameter_grouping_method: splitting a long-parameter method into smaller methods that each receive a coherent subset of parameters, addressing the long method smell alongside the long parameter list
- **lpl_introduce_param_obj** (d1): introduce_parameter_object_refactoring: a transformation that replaces a long parameter list with a single parameter object class, grouping related data and enabling method reuse and invariant enforcement
- **lpl_invariant_leak** (d1): cross_parameter_invariant: a constraint or business rule that logically spans two or more separate parameters but cannot be enforced because the parameters lack a shared container object
- **lpl_long_method_rel** (d1): long_method_cooccurrence: the empirical pattern that methods with long parameter lists frequently also suffer from excessive length and complexity, as both stem from insufficient decomposition
- **lpl_preserve_whole** (d1): preserve_whole_object_refactoring: a technique that passes the source object itself rather than extracting and passing individual attributes, reducing parameter count by restoring object cohesion
- **lpl_primitive_bundle** (d1): primitive_parameter_bundle: a set of primitive values that travel together through multiple method signatures, frequently indicating a missing abstraction that could be encapsulated into a coherent parameter object
- **lpl_primitive_obsession_rel** (d1): primitive_obsession_association: the tendency to pass multiple primitives instead of a richer object, feeding the long_parameter_list problem and suggesting that introducing a parameter object also addresses primitive obsession
- **lpl_replace_param_method** (d1): replace_parameter_with_method_call: a refactoring that eliminates a parameter by having the method obtain the value itself, applicable when the callee can compute the argument from existing parameters or object state
- **lpl_test_constructor** (d1): test_fixture_burden: the difficulty of constructing meaningful test cases when a method requires many parameters, often leading to tests that omit or default critical arguments
- **lpl_threshold** (d1): parameter_count_threshold: the line of demarcation beyond which a parameter list is deemed excessive, commonly cited as three to four parameters in literature, though context and team conventions may shift this boundary

---
*Projected from the `refactoring catalog and code smells` KB (183 concepts / 128 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
