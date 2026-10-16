# Fan-out and merge

Several agents work on independent slices in parallel; one step merges the results. Used wherever the work splits cleanly: one research angle per agent, one documentation product per agent, one loop per auditor.

## What it does

A task is cut into slices that do not depend on each other. Each slice goes to its own agent with the same instructions and a different scope. A single merge step dedupes and orders what came back. The merge is deterministic where it can be (a script), and a short agent step only where judgment is needed.

## Why this shape

Parallel slices are faster. More important, each agent sees a small, bounded input. Mistakes stay inside a slice and are visible in the merge. The merge step is also where the human gate attaches: what comes out of it is a proposal, never a publication.

## Where it ran

The article pipeline (three research agents, one merge into a claims list), the docs pipeline (one agent per product), and the estate audit (one auditor per loop). The generic rebuild is in [article-pipeline](https://github.com/nunomnferreirapt/article-pipeline).
