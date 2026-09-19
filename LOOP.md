# T1 Loop — recursive breakdown

Source of truth for the loop. `SKILL.md` is the runbook. This file is the spec.

## Short form

```
name → instance → siblings → rank
    → ontology (T1) → frame → explode → collate
    → hypothesis-rank → top-k → extract loop
```

## Whole loop

**Job.** Turn a terse pointer into a reusable frame and a top-k you would work.

**In.** A name, a URL, or “things like X”.

**Out.**

1. Named object + one-line job
2. Primary instance (what it is / is not)
3. Sibling front (non-dominated set + named tail)
4. T1 ontology (3–7 entities) + T1 taxonomy (2–4 genera)
5. Imported frame (sourced axes)
6. Deduped idea list
7. Competing hypotheses + votes
8. Top-k with reasoning, taken from the front
9. The loop itself, named

**Stop.** A framing sentence plus a top-k. Do not start another search.

**Invariants.**

- Primary sources over secondary write-ups
- Public artifacts (URLs, tables, votes) over inner monologue
- T1 only unless a step’s output blocks the next step
- Hypotheses must disagree
- Ranking states its axes and keeps the non-dominated set until step 10
- Votes cite published measurements

**Recursion rule.** Each step below has a T1 procedure (3–5 substeps). Recurse one more level only if that step’s output is blocking. Never recurse `siblings`, `rank`, or `top-k` more than once. `extract loop` is terminal.

## Rank geometry

Sweep the front. Do not expand the tail. Rank with measurements you already have. Stop.

| Move | Lives in | What to emit |
|---|---|---|
| Pareto sweep | 4, 9 | Non-dominated set on the load-bearing columns. Dominated tail named once. |
| Recursive candidate generation | 3, 7 | Siblings (one extra pass) then ontology × axes. Recurse only if blocked. |
| Empirical rank | 9 | Hypothesis votes from published measurements. Measured bottlenecks beat aesthetics. |
| Commit | 10 | k from the front. |

Pareto here is the front over those columns. Recursion is bounded candidate generation. Empirical ranking uses numbers the field already published. Running the candidates is the work after this loop.

---

## 1. Name the object

**Job.** Resolve the pointer to a single noun phrase with a job.

**In.** Terse query.

**T1 procedure.**

1. List the plausible referents (product, instance, class, paper).
2. Pick one primary referent. Park the others as context, not as the object.
3. Write `object: <noun>. job: <one line>`.

**Out.** `object` + `job`.

**Stop this step when.** One noun, one job, no hedging list.

**Fail.** Product vs instance vs class still mixed (e.g. “Claude Security / the harness / CRS” as one object).

**Do not.** Scope the whole field yet. That is steps 3–5.

**Recurse if blocked.** If two referents are equally load-bearing, name the *class* as the object and the best instance as step 2. Do not run two loops in parallel.

---

## 2. Explain the primary instance

**Job.** Say what the named object actually is, from owners of the thing.

**In.** `object` + `job`.

**T1 procedure.**

1. Fetch the owner’s README, paper, or product page. Not a roundup.
2. Extract: loop/stages, witness of a finding, what it will not do, how you run it.
3. Write is / is not / limits.

**Out.** A short instance card: architecture, run path, non-goals.

**Stop this step when.** A newcomer could distinguish it from the nearest neighbor.

**Fail.** Feature list. Blog paraphrase. “AI-powered” with no witness.

**Do not.** Rank alternatives yet.

**Recurse if blocked.** If the owner’s page is a landing page, open the actual spec (pipeline.md, paper, skill list). One hop.

---

## 3. Recursive search for siblings

**Job.** Same job, other implementations.

**In.** Instance card.

**T1 procedure.**

1. Search the job, not the brand (`autonomous vulnerability discovery patch harness`, not only the product name).
2. Follow catalogs and citations one hop (awesome lists, competition releases, academic ports).
3. Keep a candidate only if it is OSS *or* a documented closed system you will mark as closed.
4. Record: name, URL, witness type, patch/fix gate, runnable today?

**Out.** Candidate table with primary URLs.

**Stop this step when.** New hits are aliases of rows you already have.

**Fail.** Dumping an awesome list unverified. Treating hosted products as clones of the OSS instance.

**Do not.** Recurse into every sub-tool those projects mention.

**One extra pass (max).** Re-search using the *job of the instance* plus “open source” and the competition/standard name if one exists (e.g. AIxCC CRS). Then stop.

---

## 4. Collate, then rank

**Job.** Ordering is the product. The list is not. This step emits a non-dominated set on the load-bearing columns.

**In.** Candidate table.

**T1 procedure.**

1. Collate onto the instance’s load-bearing columns (for a CRS: witness, fix gate, runnable, not stars).
2. State the sweep axes in one sentence. These are those columns.
3. Mark dominated rows: worse or equal on every axis, strictly worse on one. That is the tail.
4. Keep the non-dominated set. Order the front only so the top 3–6 are readable.
5. Closed or unrunnable systems go below runnable ones unless an axis says otherwise.

**Out.** Non-dominated set, named tail, stated axes.

**Stop this step when.** The front is stable if you drop the tail.

**Fail.** Star-count ranking. Alphabetical dump. One weighted score that hides a tradeoff the columns still show.

**Do not.** Build a 40-row taxonomy here. That is step 5. Pick k here. That is step 10.

---

## 5. 80/20 ontology + taxonomy, T1 only

**Job.** Compress the field to the entities that distinguish 80% of cases.

**In.** Sibling front + instance card.

**T1 procedure.**

1. **Entities.** Name 3–7 objects every serious instance has. Drop anything that is implementation (model brand, number of agents, SARIF).
2. **Relation.** One diagram or sentence that binds them (what produces what, what is allowed to see what).
3. **First cut.** One question that splits the field (the 20% taxonomy). Usually: what counts as a finding, and who is allowed to believe it.
4. **T1 genera.** 2–4 categories from that cut. List members. Do not expand genera that failed the cut.

**Out.** Entity table, binding relation, first-cut question, T1 genera with members.

**Stop this step when.** You can classify a new sibling without adding an entity.

**Fail.** 15-stage pipelines as ontology. Taxonomy of vendors.

**Do not.** Expand Tier 2 (“everything else”). Name it once and leave it.

### T1 recurse (only if the first cut is fuzzy)

1. For each proposed entity, ask: if I remove it, can two instances still be told apart? If yes, drop it.
2. For the first-cut question, ask: does it sort the ranked list’s top half? If not, the cut is wrong.
3. Stop. Do not invent a second cut.

---

## 6. Import a framing discipline

**Job.** Borrow official axes from a field that already studies representation, not more tools.

**In.** Ontology.

**T1 procedure.**

1. Pick a discipline with *published* axes (course requirements, a textbook’s methods, a standard). Source them.
2. Write one framing sentence: this object, under those axes.
3. List the axes. 3–6. Not a concentration catalog.

**Out.** Frame name, source URL, axes, framing sentence.

**Stop this step when.** Each ontology entity can be asked about from at least one axis.

**Fail.** A vibe frame (“think like a scientist”). Axes you made up.

**Do not.** Explode yet. That is step 7.

**Worked default in the originating session.** Stanford Symbolic Systems: Philosophical Analysis, Formal Methods, Computational Methods, Empirical Cognitive Science. Core concepts: computation, representation, communication, intelligence. Source: [symsys.stanford.edu](https://symsys.stanford.edu/undergraduates/major-policies-requirements/core-requirements).

---

## 7. Cross-product explode

**Job.** Ontology entities × frame axes → candidate ideas.

**In.** Entities × axes.

**T1 procedure.**

1. Draw the matrix. One note per cell. Empty is allowed; skip filler.
2. Mark collisions (two cells that are the same idea).
3. Do not polish. This step produces raw cells.

**Out.** Matrix.

**Stop this step when.** Every entity has at least one non-empty cell, or you can say why it does not.

**Fail.** 20 slogans. Cells that do not mention the entity.

**Do not.** Rank here.

---

## 8. Dedup into a list

**Job.** Cells collapse. Keep distinct ideas only.

**In.** Matrix.

**T1 procedure.**

1. Merge cells that are the same claim in different jargon.
2. Drop cells that are vocabulary for another idea (keep the name, not the project).
3. Number the remainder. 8–20 is the useful band. Below 5 you under-exploded; above 25 you did not merge.

**Out.** Numbered idea list.

**Stop this step when.** No two items would produce the same artifact.

**Fail.** Keeping the whole matrix as the list.

---

## 9. Rank with competing hypotheses

**Job.** Hypotheses that disagree vote on the list. Votes are measurements the field already published.

**In.** Idea list + whatever the field has already measured.

**T1 procedure.**

1. Write at least 3 hypotheses. Each must *promote different ideas*. If they all promote the same top-k, they are not competing.
2. For each: claim, what it says to work on, what would falsify it.
3. Let evidence from the instance/siblings vote (measured bottlenecks beat aesthetics). A vote without a number or a primary source does not count.
4. State the resolution rule (which votes count for ranking).
5. Mark ideas dominated under that rule. Keep the non-dominated set. Reorder only inside the front.

**Out.** Hypothesis table, votes, non-dominated set, named tail.

**Stop this step when.** The top 5 would not change if you dropped the weakest hypothesis.

**Fail.** “Hypotheses” that are all true together. Ranking by how clever the name is. A new eval or a new search used as a vote.

### T1 recurse (only if votes are a tie)

1. Prefer the hypothesis that cites a measured loss in the field.
2. Demote philosophy-only items to vocabulary unless the framing goal is a thesis.
3. Stop. Do not add hypothesis 7.

---

## 10. Top-k + reasoning

**Job.** Commit. k comes from the front that steps 4 and 9 kept.

**In.** Non-dominated set + resolution rule.

**T1 procedure.**

1. Pick k (default 5). k is not “all of them” and not the tail.
2. For each item: one paragraph of why it survives the votes. No restating the table.
3. Write the framing sentence the top-k commits you to.

**Out.** Framing sentence + top-k.

**Stop this step when.** You would start work on item 1 tomorrow, not research item 6.

**Fail.** k = N. k drawn from the dominated tail. A framing sentence that does not mention the ontology.

**Do not.** Start building the ideas in this step. This loop produces a frame and a list, not the implementation. Do not run the candidates here.

---

## 11. Extract the loop

**Job.** Name the procedure so it can be run on a different object.

**In.** The session’s actual steps (not the topic).

**T1 procedure.**

1. List what you *did*, in order, as verbs.
2. Drop topic nouns. If a step only makes sense for this object, it is not in the loop.
3. Write short form + stop condition.
4. This file is the recursive breakdown of that short form.

**Out.** Short form, stop, pointer to this spec.

**Stop this step when.** The short form runs on a different field without edits.

**Fail.** Describing the topic (“vuln harness loop”) instead of the procedure.

**Terminal.** Do not recurse.

---

## Anti-patterns

| Pattern | Why it dies |
|---|---|
| Another search after top-k | The stop condition was the point |
| Taxonomy of vendors | Ontology is entities, not brands |
| Hypotheses that agree | Then they are a manifesto, not a ranker |
| Expanding Tier 2 | The 80/20 already threw it away |
| Star-count rank | Stars are not a witness |
| One weighted score at step 4 | The columns were the sweep; the score hid the tradeoff |
| New eval or search as a vote | Votes use measurements you already have |
| Breeding candidates after ranking | Recursion is one extra pass at 3/7, then stop |
| Frame without a source | You made up axes |
| Implementing during the loop | This loop decides what to work; it is not the work |

## Agent notes

- Fetch primary sources in steps 2, 3, 6. Do not invent axes or star counts.
- If a sibling is closed-source, keep it in the table and mark it closed. Do not pretend it is a clone you can run.
- Keep the non-dominated set at 4 and 9. Commit k from it at 10.
- When the user says “recursive breakdown, T1 only”, obey step 5’s fail column even if you have more to say.
