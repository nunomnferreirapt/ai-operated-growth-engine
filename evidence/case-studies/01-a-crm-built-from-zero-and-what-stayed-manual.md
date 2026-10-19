# A CRM built from zero, and what stayed manual

*The data model, the triggers that make a marketing-qualified lead, the criteria that make a sales-qualified one, the Shopify link, and the freelancer who handled what did not make sense to automate.*

## Before

There was no CRM. Customer history lived in inboxes, spreadsheets and people's heads. Orders went through a Shopify store that nobody treated as a source of truth. If you asked where a customer had come from, or how many leads a campaign had produced, there was no answer.

## What we built

```mermaid
%%{init: {"flowchart": {"wrappingWidth": 600, "nodeSpacing": 30, "rankSpacing": 40}}}%%
flowchart TB
    subgraph IN["Triggers, source stamped at first touch"]
        direction LR
        T1["Trial request or plug-in download"]:::sys
        T2["LinkedIn lead form, contact form, email"]:::sys
    end
    IN --> MQL["MQL, by trigger"]:::sys
    MQL --> SQ{"A person decides"}:::human
    SQ --> SQL["SQL: real company, geotechnical use, our market"]:::sys
    SQ --> OUT["Campaign target, partner, or disqualified"]:::sys
    SQL --> SEQ["Sequence by segment, Teams tag for who follows up"]:::sys
    SEQ --> DEAL["Deal in HubSpot: demo, talks, draft order, closed, dormant"]:::sys
    SHOP["Draft order on Shopify, the offer"]:::sys -- "creates the deal automatically: one offer, one deal" --> DEAL
    DEAL --> CLS["Classified in HubSpot: subscription type, market, customer type"]:::sys
    CLS --> REP["Financial reporting: Shopify the money, HubSpot the categories"]:::out
    classDef sys fill:#1f3a5f,stroke:#7aa2d8,color:#ffffff
    classDef human fill:#6b4514,stroke:#e0a95a,color:#ffffff
    classDef out fill:#1e4d3a,stroke:#6fcf97,color:#ffffff
    style IN fill:transparent,stroke:#7f8c9a,stroke-dasharray:4 3
```

**HubSpot, from an empty account.** Contacts, companies and deals, with one sales pipeline whose stages matched how deals actually moved: a technical demo, talks, a draft order, closed, or dormant. Three fields on every deal drive everything downstream, including the financial reporting: the subscription type (new, renewal, expansion), the market (German-speaking or not), and the customer type (new, reactivated, migrated).

**One offer, one deal.** Shopify and HubSpot are integrated: every draft order created on Shopify creates a HubSpot deal automatically. For sales operations that meant every offer with a real chance of closing landed with the right sales rep, nothing fell between the two systems, and every order got classified in HubSpot (subscription type, market, customer type) for the financial reporting. Shopify is the financial source of truth; HubSpot is the source of truth for the categories. That pair is what later let the reporting pipeline classify sales by customer status and region without anyone re-keying anything.

**Marketing-qualified by trigger.** A contact becomes an MQL on an action, not on a judgment: a trial request, a download of the free plug-in, a LinkedIn lead form, a contact form or an email submit, a known company identified on the website. The source is stamped at that moment, so attribution exists from the first touch.

**Sales-qualified by a person.** An MQL becomes an SQL when someone looks at it and says so: a real company, a geotechnical or civil engineering use, a market we sell in. The alternatives are explicit too: campaign target, partner or reseller, disqualified. In the end, 2,900 contacts made it. This is the step I never automated, because the judgment is the point.

**Routing and follow-up.** A LinkedIn ad feeds a HubSpot sequence and posts a Teams notification that tags the colleague who follows up. Dormant SQLs get a short two-email sequence after a month of silence, written in a consultative tone and signed by a person.

**What stayed manual, on purpose.** The Surfe plug-in made data enrichment and the LinkedIn side much faster. What was left, mapping orders to deals when the join failed and qualifying edge cases, went to a part-time freelancer hired through Upwork. Cheaper and more reliable than automating the last edge cases.

![The open deals list in HubSpot](../../assets/chapter-1/hubspot-open-deals.png)

*The deals list: every draft order on Shopify is a deal, with its category, priority, stage, contacts and owner. Names and totals blurred.*

![The sales pipeline as a board](../../assets/chapter-1/hubspot-pipeline-board.png)

*The same pipeline as a board: in talks, demo scheduled, demo done, draft order created, draft order sent, pilot, closed won, dormant, closed lost. Cards blurred.*

![The funnel as presented to the investment committee](../../assets/chapter-1/funnel-investment-committee.png)

*The funnel as presented to the investment committee: MQLs ramping up, outreach following, SQLs by country, segment and lead reason, and the Autodesk plug-in as a channel.*

![A HubSpot dashboard on one trigger](../../assets/chapter-1/hubspot-dashboard-plugin-downloads.png)

*One trigger, one dashboard: plug-in downloads per week, how they qualified, by country and by segment.*

![Lifecycle stages in HubSpot and the same stages as Google Ads conversion goals](../../assets/chapter-1/lifecycle-stages-and-google-ads-goals.png)

*The lifecycle stages in HubSpot (open, MQL, SQL, hard lead, opportunity, paying customer) and the same stages wired into Google Ads as conversion goals, so the ads optimize on what sales cares about.*

## What stayed human

The SQL decision. The sequences, written by people. And the reading of the numbers: the LinkedIn-to-HubSpot attribution join showed that paid social was the top of the funnel, not the last touch before a deal, which changed how the budget was judged.

## What it did

A funnel of 6,300 contacts across 60+ countries, 2,900 of them sales-qualified, with paid social as the #2 lead source. The CRM ecosystem, Shopify and HubSpot integrated, became the base for the financial reporting, the funnel analysis and, later, the AI loops.
