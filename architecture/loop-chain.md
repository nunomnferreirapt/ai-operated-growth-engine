# The weekly loop chain

The skills that had to run every week ran in one chain, in dependency order: index, chatbot drift, playbook, docs drift, fact-check, reviews watch, register re-verify. Seven stages in one chain replaced six jobs that ran at fixed times.

```mermaid
%%{init: {"flowchart": {"wrappingWidth": 600, "nodeSpacing": 30, "rankSpacing": 32}}}%%
flowchart TB
    S1["`**Claude skill** 1 · Index: crawl website, docs, support, marketplace into the vault`"]:::sys
    S2["`**Claude skill** 2 · Chatbot drift: brain against the fresh vault`"]:::sys
    S3["`**Claude skill** 3 · Playbook: checked against the same vault`"]:::sys
    S4["`**Claude skill** 4 · Docs drift: sites against their sources`"]:::sys
    S5["`**Claude skill** 5 · Fact-check: the two master sales documents`"]:::sys
    S6["`**Claude skill** 6 · Reviews watch: new marketplace reviews, draft replies`"]:::sys
    S7["`**Claude skill** 7 · Register re-verify: gaps only a person can close`"]:::sys
    S1 --> S2 --> S3 --> S4 --> S5 --> S6 --> S7
    S1 -. "a failed crawl fails everything after it" .-> S7
    S7 --> OUT["Proposals, drift reports, draft replies, pull requests"]:::out
    OUT --> P(["A person reads what ran, what failed, what to do"]):::human
    classDef sys fill:#1f3a5f,stroke:#7aa2d8,color:#ffffff
    classDef human fill:#6b4514,stroke:#e0a95a,color:#ffffff
    classDef out fill:#1e4d3a,stroke:#6fcf97,color:#ffffff
```

## What it does

1. **Index.** Crawlers refresh the knowledge vault from the website, the documentation, the support articles and the marketplace listing. The vault is under git, so every refresh is a diff.
2. **Chatbot drift.** The chatbot's knowledge base is compared with the fresh vault; differences become a drift report.
3. **Playbook.** The sales playbook is checked against the same vault.
4. **Docs drift.** The documentation sites are compared with their sources; gaps become proposed pull requests.
5. **Fact-check.** The two master sales documents, written by people, are checked against the sources; differences become paste-ready edits for a named approver.
6. **Reviews watch.** New marketplace reviews are collected, with draft replies.
7. **Register re-verify.** The list of gaps only a person can close is checked against what was merged that week.

Nothing in the chain publishes. Every stage that touches the outside world ends in a proposal or a pull request; see [the human gate](human-gate.md).

## Why this shape

The first version ran the jobs at fixed times, a few hours apart. When one ran long, the next started on top of it. When a crawl failed quietly, the stages after it worked from last week's sources. In one chain, a failed crawl marks everything after it as failed too. A guard restores the knowledge base when a crawl shrinks it sharply, added after a bad crawl did exactly that. The results waited for a person to read them: what had run, what had failed, and what to do about it.

## What would change next time

Start with the chain, not the clock.
