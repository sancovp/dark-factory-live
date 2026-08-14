# inversion_lens

## Type
lens

## Rarity
common

## Description
A lens that reframes problems by inversion — looking at what would be true if the problem's opposite were the goal.

## Invocation
Input: { problem: string }
Output: { reframed: string, inversion_statement: string }

## Method
1. Identify the stated goal or desired outcome in the problem
2. Invert it: "What if the OPPOSITE were the true goal?"
3. Trace implications backward from the inversion
4. Return the reframed problem + the inversion statement

## Usage
PROBLEM: "Why is the economy flat?"
INVERSION: "What if flatness IS the goal?"
REFRAME: "What forces would WANT a flat economy?"

## Example
Input:  "Why can't agents cooperate?"
Inversion: "What if defection WERE the goal?"
Reframe:   "What if the reward structure DESIGNED defection?"
