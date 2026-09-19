---
name: t1-loop
description: >
  Run a Pareto research loop: name an object, explain the primary instance,
  find siblings, rank them, compress to a T1 ontology and taxonomy, import a
  framing discipline, explode ontology × axes, collate, rank with competing
  hypotheses, commit to top-k, extract the loop. Use when the user says
  t1-loop, meta-loop, 80/20 ontology, recursive breakdown, competing
  hypotheses, or wants a research procedure pulled out of a session.
---

# T1 Loop

Run the loop in [LOOP.md](LOOP.md). That file is the spec. This file is the runbook.

## Short form

```
name → instance → siblings → rank
    → ontology (T1) → frame → explode → collate
    → hypothesis-rank → top-k → extract loop
```

**Stop when** you have a framing sentence you can reuse and a top-k you would actually work. Not another search.

## When to use

- A terse pointer (“X”, “things like X”, a URL) and the user wants the field compressed, not a tour.
- The user asks for 80/20 ontology, T1 taxonomy, competing hypotheses, or top-k.
- The user asks what loop they just ran.

Do not use for a single-file bugfix, a look-up of a known API, or implementing the top-k.

## Procedure

Follow LOOP.md steps 1–11 in order. At each step: T1 only (3–5 substeps). Recurse one level only if that step’s output blocks the next. Never recurse `siblings`, `rank`, or `top-k` more than once.

Emit, in the final message:

1. `object` + `job`
2. Instance card (is / is not / limits) with primary URLs
3. Ranked siblings + rank criterion
4. Ontology entities, binding relation, first-cut question, T1 genera
5. Frame (name, source, axes, framing sentence)
6. Deduped idea list
7. Competing hypotheses (claim / promotes / falsifier) and the resolution rule
8. Top-k with reasoning
9. Short form of the loop + stop condition

## Invariants

- Primary sources over roundups
- Rank criterion stated
- Hypotheses disagree
- Tier 2 named once, not expanded
- No implementation of the top-k inside this loop

## Fail closed

If you cannot find a primary source for the instance, stop after step 2 and say so. If you cannot find a sourced frame, skip steps 6–7 and rank siblings only.
