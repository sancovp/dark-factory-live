# Test-Then-Verify Pipeline

**Type:** recipe
**Rarity:** uncommon
**Description:** Composes a test runner and chain verifier into a two-stage pipeline

## Composition
- test_runner: executes test suite
- chain_verifier: validates artifact chain

## Flow
Stage 1: Run tests -> if fail, halt
Stage 2: Verify chain -> both pass = verified

## Usage
pipeline(test_suite_path, artifact_path) -> {verified, test_results, chain_status}
