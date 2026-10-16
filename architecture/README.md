# Architecture

One note per mechanism, short, written from the chapters. Each: what it does, why this shape, where it ran.

| Document | What it covers |
|---|---|
| [`loop-chain.md`](loop-chain.md) | The weekly dependency-ordered chain that replaced clock-scheduled jobs |
| [`human-gate.md`](human-gate.md) | Proposal, pull request, a person merges; what stayed with people |
| [`patterns/fan-out-merge.md`](patterns/fan-out-merge.md) | Parallel agents on independent slices, one merge step |
| [`patterns/research-writer.md`](patterns/research-writer.md) | Parallel research, one writer, a citation check |
| [`patterns/manifest-driven-incremental.md`](patterns/manifest-driven-incremental.md) | A hash per source decides whether anything runs |
| [`patterns/drift-watch.md`](patterns/drift-watch.md) | Read-only comparison of a surface with its sources |

Coming: sanitized excerpts of a skill definition, the orchestrator config shape and the PR-gate workflow.
