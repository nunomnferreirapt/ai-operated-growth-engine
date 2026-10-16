# Docs as code, three sites

*From a legacy archive nobody used to self-service docs for new users and deep reference for power users, built from help files, support portal and demo transcripts through a PR-gated pipeline and kept in sync by a drift watch.*

## Before

The legacy help, locked in a Windows help database. A public docs site full of empty stubs. A German support portal that covered what the docs did not. New customers stalled in the trial because the first ten minutes were not documented, and power users emailed support for lookups the product could have answered.

## What we built

**Docs as a software project.** Three public repositories, one per product, rendered as websites. A private companion repository with the audit, the rulebook and the migration plan. Every legacy help topic was indexed and mapped to a destination page or marked for retirement; the result was a list of work packages, not a vague ambition.

**Drafts from bounded sources.** An AI pipeline turned the sources we had (the legacy help files, anonymized demo transcripts, support articles and recorded walkthroughs) into draft pages and pull requests. Every change cites its source, and every PR carries a table of sources per change. The pipeline may not invent; if no source covers a question, it goes on a list for the people who know the product.

**Rules in three layers.** Mechanical rules in CI: typography, duplicated content, empty stubs, broken links, changed images. Judgment rules in a rulebook synced into each repo's agent instructions. Procedure in two contribution skills anyone on the team can run.

**A weekly drift watch.** Product facts the website states but the docs do not, flagged weekly and turned into proposed changes.

## What stayed human

Nothing reaches a public site without a person reading it page by page. I checked each pull request in the diff view; the product lead merged. The list of gaps no written source could fill went to the people with the product knowledge, by name.

## What it did

From a legacy archive nobody used to self-service documentation for new users and deep reference for power users, across the three product suites. A blind evaluation of the desktop docs, same tasks before and after, moved them from "you need a support ticket for daily work" to "self-serve for most tasks". In October 2026 the process was handed over as two skills, a rulebook and a reviewer checklist. Client success contributes; one reviewer merges.

## What I would do differently

Introduce the CI layer on day one. The first months relied on reviewers catching typography and duplication by eye, and the same problems came back until they became rules.
