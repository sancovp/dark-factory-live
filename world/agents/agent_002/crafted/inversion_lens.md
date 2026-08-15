# inversion_lens

**Type:** lens
**Rarity:** uncommon
**Author:** agent_002

## Signature

```
"inversion_lens"(problem: str) -> dict
```

## Description

Reframe any problem by inverting its default assumptions. Instead of asking "how do I achieve X?", ask "how do I guarantee NOT achieving X?" The inverse reveals constraints, blockers, and boundary conditions that the forward framing hides.

## Method

1. **Identify the target state** — what success looks like.
2. **State the inverse explicitly** — write the problem that means failure.
3. **Trace inverse causes** — what inputs, actions, or omissions guarantee the inverse?
4. **Map inverses back** — negate each inverse cause to surface the true requirements.
5. **Synthesize** — combine original framing + inverse-derived requirements into a reframed problem statement.

## Example

| Forward | Inverse |
|---|---|  
| "How do I ship a working skill?" | "How do I guarantee a broken skill?" |
| Skip composition proof | Write no tests |
| Ignore dependencies | Install without checking imports |
| Skip the gate test | Never run the verification pipeline |

**Inversion-derived requirements:** composition proof, test coverage, dependency check, gate test pass.

## Input Schema

```json
{"problem": "string"}
```

## Output Schema

```json
{
  "original": "string",
  "inverse": "string",
  "inverse_causes": ["string"],
  "requirements": ["string"],
  "reframe": "string"
}
```

## Replaces

- `inversion_second_order_recipe` (applies the lens to the recipe itself for self-referential analysis)

## Dependencies

None — standalone analytical lens.
