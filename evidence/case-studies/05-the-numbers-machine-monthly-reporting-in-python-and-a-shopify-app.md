# The numbers machine: monthly reporting in Python and a Shopify app

*A rules-based reporting engine on git that turned subscription chains, Shopify orders and cohorts into the monthly reporting done with Fugro corporate finance and a five-year projection; the rules themselves, and why a spreadsheet could not hold them.*

## Before

Monthly top-line reporting to corporate finance ran on a manually maintained Excel fed by Shopify's CSV export. The export has two flaws that nobody had noticed. An edited order keeps its removed lines in the CSV, so a single edit could more than double that order's total. And a canceled, unpaid order keeps its full value unless someone filters it out. Every month the numbers were a little wrong in ways that could not be traced.

## What we built

```mermaid
%%{init: {"flowchart": {"wrappingWidth": 600, "nodeSpacing": 30, "rankSpacing": 32}}}%%
flowchart TB
    subgraph SRC["Sources, pulled every month"]
        direction LR
        SH["Shopify app, read-only: every order in its current state"]:::sys
        HS["HubSpot deal, joined by order number: status, market"]:::sys
        LG["Legacy orders, parsed from spreadsheets"]:::sys
    end
    RU(["The rules, decided with finance, written before the code"]):::human --> RE
    SRC --> RE["Rules engine in Python: classifies every line"]:::sys
    RE --> CT["Clean tables: subscriptions, services, revenue, churn, chains"]:::out
    RE --> FL(["Lines a person must look at, every month"]):::human
    CT --> WB["Excel workbook: data tabs, monthly metrics, subscription base"]:::out
    WB --> FIN["Monthly reporting with corporate finance"]:::out
    CT --> PRJ["Five-year projection and strategic snapshot, chapter 6"]:::out
    subgraph HO["The handover, at exit"]
        direction LR
        PS["PowerShell twin, validated line by line against Python"]:::sys --> CC["`**Claude Code** runs it for the finance user, read-only app`"]:::sys
    end
    RE -.-> PS
    classDef sys fill:#1f3a5f,stroke:#7aa2d8,color:#ffffff
    classDef human fill:#6b4514,stroke:#e0a95a,color:#ffffff
    classDef out fill:#1e4d3a,stroke:#6fcf97,color:#ffffff
    style SRC fill:transparent,stroke:#7f8c9a,stroke-dasharray:4 3
    style HO fill:transparent,stroke:#7f8c9a,stroke-dasharray:4 3
```

**A Shopify app for the data.** Built with Claude Code: a read-only app, owned by the organization, that exports every order in its current state, after edits and refunds, in the shape the pipeline needs. The CSV export was never used again.

**A pipeline, in Python, in a repository.** Three layers:

- Pull: orders and transactions from the Shopify app, into raw files.
- Clean: a rules engine classifies every line into the clean tables: subscriptions, services, trials, monthly revenue, credit notes, cancellations, defaults, churn events, subscription chains. Plus a file of lines a person must look at.
- Report: an Excel workbook with the data tabs, the monthly metrics, the renewal chains and the subscription base.

![The pipeline, three layers, script by script](../../assets/chapter-5/pipeline-three-layers.png)

*The three layers as the repo's README draws them: pull, clean, the legacy layer that anchors year zero, and the workbook.*

**The rules, written down before the code.**

- Gross sales net of VAT, at order date.
- Revenue on an accrual basis: subscriptions spread over the service period, which can start later than the order; services recognized at each payment.
- Adjustments prospective: a refund or cancellation is a reversal in the month it happens. Past reports are never restated.
- Unpaid past a threshold: written off as a loss.
- VAT: five scenarios across countries, all handled by trusting the API's net amounts rather than rebuilding tax logic.
- Every rule has its case in an edge-case log, and the pipeline was validated against each one.

![The repository layout](../../assets/chapter-5/repository-layout.png)

*The repository: rules and data model written as documents, scripts per layer, the lookups a person maintains, the board layer, and real data kept out of git.*

**HubSpot as the categorization source.** Each order joins to exactly one CRM deal by order number; customer status and market come from there. Shopify is the money, HubSpot the categories, as set up in [chapter 1](01-a-crm-built-from-zero-and-what-stayed-manual.md). Pre-Shopify legacy orders were parsed from spreadsheets so the renewal chains reach back to year zero.

**The five-year projection on top.** The clean base feeds the forecast model with scenarios and dials, the one in [chapter 6](06-a-financial-model-the-leadership-team-could-click.md), and a strategic snapshot regenerated from the same pipeline for the investment committee.

**The handover.** At exit, finance needed to keep cross-checking their report every month, on a Windows machine with no Python, no git and no admin rights. So: the pipeline scoped down to what Shopify alone can prove, ported to PowerShell, validated line by line against the Python version, and set up so that Claude Code runs it for the finance user from the read-only Shopify app. One handover session on the last day. It ran.

## What stayed human

The rules. Every one of them is a decision in the rules file, made with finance, not a default the code picked: how a refund, a cancellation or an order edit is booked; when an unmatched or ambiguous line counts as a missing sale rather than noise; what a customer's status and region are when the two systems disagree; how a multi-year prepaid order or a backdated period is recognized; when an unpaid order becomes a loss. The file also says what to do when a rule needs to change. The lines flagged for manual review are a person's job, every month.

## What it did

Monthly reporting with Fugro's corporate finance team that reconciles to the euro. The quarterly report to the technology committee, updated from the snapshot in half an hour.

![Every report cut falls out of the clean tables as a pivot](../../assets/chapter-5/data-model-every-cut-a-pivot.png)

*From the data-model note: every report cut, the monthly report, per-product splits, seats, churn, trial conversion, the renewal forecast, falls out of the clean tables as a pivot. No additional tables, one truth.*

![The strategic snapshot, section by section](../../assets/chapter-5/strategic-snapshot-sections.png)

*The strategic snapshot, regenerated from the pipeline: the single source of truth for actuals, one section per question the board asks.*

![The board dashboard, every number traced to the snapshot](../../assets/chapter-5/board-dashboard-quadrants.png)

*The quarterly board slide, every number traced to the snapshot. The technology committee report took half an hour to update.* The same base produced the subscription growth figures on the front page, the renewal chains behind the retention numbers, and the snapshot the five-year plan is anchored to: EBITDA from -67% in 2023 to break-even in the 2027 plan.

## What I would do differently

Write the monthly operating procedure while I was still the only operator. It was a known open item for months and became the hardest part of a one-session handover.
