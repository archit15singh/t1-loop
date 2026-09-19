# T1 Loop

An agentic research loop. Name an object, compress the field to a few entities, import a frame, explode, compete, commit. Then stop.

This repo is the spec. It is not a product, a scanner, or a 15-stage pipeline.

## Short form

```
name → instance → siblings → rank
    → ontology (T1) → frame → explode → collate
    → hypothesis-rank → top-k → extract loop
```

**Stop when** you have a framing sentence you can reuse and a top-k you would actually work. Not another search.

## Files

| File | Role |
|---|---|
| [LOOP.md](LOOP.md) | Source of truth: recursive breakdown of every step |
| [SKILL.md](SKILL.md) | Agent runbook |
| [examples/worked-example.md](examples/worked-example.md) | One pass on autonomous vuln find-and-fix harnesses |

## Recursion rule

Run each step at Tier 1 (3–5 substeps). Recurse into a step only if its output is blocking the next step. Never recurse into `siblings`, `rank`, or `top-k` beyond one extra pass. `extract loop` is terminal.

## Whole-loop contract

| | |
|---|---|
| **In** | A terse pointer (a name, a URL, a “things like X”) |
| **Out** | Named object, T1 ontology, framing sentence, top-k with competing-hypothesis votes |
| **Invariant** | Findings are public artifacts (sources, tables, votes), not vibes |
| **Do not** | Expand the long tail. Star-count rank. Hypotheses that all promote everything. |

## Install as a skill

Copy `SKILL.md` (and `LOOP.md` next to it) into your agent’s skills directory, or clone this repo and point the agent at it.
