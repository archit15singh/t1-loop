---
name: vital-few
description: >
  Compress a terse pointer into a reusable frame and a top-k you would work.
  Name the object, explain the instance, find siblings, sweep a non-dominated
  set, cut to a T1 (Tier 1) ontology, import a frame, explode, rank with
  hypotheses that disagree, commit, stop. Use when the user says vital few,
  t1-loop, 80/20 ontology, T1 taxonomy, competing hypotheses, or wants a
  field compressed not toured. Not the ZDT T1 test function, not a control
  loop t₁, not a Deep Research report.
---

# Vital Few

Run the loop in [LOOP.md](LOOP.md). That file is the spec. This file is the runbook. T1 in the spec means Tier 1 (the cut).

## Short form

```
name → instance → siblings → rank
    → ontology (T1) → frame → explode → cca
    → hypothesis-rank → top-k → extract loop
```

**Aspiration.** Stop when all four hold: framing sentence names the ontology; top-k is from the front and k is not N; item-1 witness is `yes` + one line; no further search is queued. If witness is `no`, one recut inside step 10, then stop anyway.

## When to use

- A terse pointer (“X”, “things like X”, a URL) and the user wants the field compressed, not a tour.
- The user asks for vital few, 80/20 ontology, T1 taxonomy, competing hypotheses, or top-k.
- The user says t1-loop (old name) or asks what loop they just ran.

Do not use for a single-file bugfix, a look-up of a known API, or implementing the top-k.

## Procedure

Follow LOOP.md steps 1–11 in order. At each step: T1 only (3–5 substeps). Recurse one level only if that step’s output blocks the next. Never recurse `siblings`, `rank`, or `top-k` more than once. Rank geometry lives in LOOP.md. Step 8 is Zwicky CCA then dedup. Step 10 emits the item-1 witness and the four aspiration checks.

Emit, in the final message:

1. `object` + `job`
2. Instance card (is / is not / limits) with primary URLs
3. Sibling front (non-dominated set + named tail) + sweep axes
4. Ontology entities, binding relation, first-cut question, T1 genera
5. Frame (name, source, axes, framing sentence)
6. Deduped idea list after CCA (plus dropped-cell log)
7. Competing hypotheses (claim / promotes / falsifier) and the resolution rule
8. Top-k with reasoning, taken from the front, plus item-1 witness (`yes`/`no` + one line)
9. Short form of the loop + aspiration four-check

## Invariants

- Primary sources over roundups
- Sweep axes stated; non-dominated set kept until step 10
- Step 8 runs CCA before the list is numbered
- Hypotheses disagree; votes cite published measurements
- Tier 2 named once, not expanded
- No implementation of the top-k inside this loop
- No new eval or search used as a vote
- Aspiration is the four checks, including item-1 witness

## Fail closed

If you cannot find a primary source for the instance, stop after step 2 and say so. If you cannot find a sourced frame, skip steps 6–8 and emit the sibling front only.
