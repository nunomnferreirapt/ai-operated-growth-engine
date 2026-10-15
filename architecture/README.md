# Architecture

One document per pattern. Each follows the same outline: what it does, why this shape, how it fails safely, what it looked like in production, what would change next time.

| Document | What it covers |
|---|---|
| `loop-chain.md` | The weekly dependency-gated chain that replaced clock-scheduled jobs |
| `human-gate.md` | Proposal packets, PRs, priorities, and who approves what |
| `patterns/fan-out-merge.md` | Parallel agents on independent slices, one merge step |
| `patterns/research-writer.md` | Parallel research, a single sequential writer |
| `patterns/manifest-driven-incremental.md` | Hash and freshness manifests deciding what runs at all |
| `patterns/drift-watch.md` | Read-only watchers with tripwires that prove they stayed read-only |

Status: outlines, 15 Oct 2026. Content pending.
