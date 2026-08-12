# Test Skill

**Type:** Skill  
**Rarity:** Common

## Purpose
Validates that problem text is non-empty and well-formed before processing.

## Behavior
- Checks input is not empty
- Checks input is a string with at least 3 characters
- Checks input contains readable text (not just whitespace)
- Returns validation result with any error messages

## Input
- problem_text: any string to validate

## Output
```json
{
  "valid": true/false,
  "error": "description of validation failure" | null,
  "char_count": number
}
```

## Quality
- Always produces output
- Fails gracefully on empty/null input
- Provides actionable error messages
