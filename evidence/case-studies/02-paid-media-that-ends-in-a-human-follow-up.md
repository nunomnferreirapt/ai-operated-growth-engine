# Paid media that ends in a human follow-up

*Campaigns customized across 20+ segments, each wired from LinkedIn ad to HubSpot sequence to a Teams notification that tags who follows up; and the monthly budget review that decided where the money went next.*

## Before

No paid acquisition. The customer base was German-speaking and had arrived by word of mouth over thirty years. Engineers outside that circle had never heard of the product.

## What we built

```mermaid
%%{init: {"flowchart": {"wrappingWidth": 600, "nodeSpacing": 30, "rankSpacing": 40}}}%%
flowchart TB
    SEG["A segment: market, role, the engineer's problem"]:::sys --> CR["Its own creative and lead magnet, in the local language"]:::sys
    CR --> AD["LinkedIn ad with a native lead form"]:::sys
    AD --> HS["Lead in HubSpot, campaign stamped"]:::sys
    HS --> SQ["Sequence matched to the segment, on a schedule"]:::sys
    HS --> TT["Teams notification tagging who follows up"]:::sys
    SQ --> P{"A person replies and follows up"}:::human
    TT --> P
    P --> SC
    subgraph M["Every month"]
        direction LR
        SC["Scorecard: spend, leads, qualified share per campaign"]:::sys --> FA["Fatigue flagged by rule, dead lines flagged"]:::sys
        AJ["Attribution join: LinkedIn numbers to HubSpot deals"]:::sys
    end
    FA --> B{"A person decides: kill, scale or hold, per segment"}:::human
    AJ --> B
    classDef sys fill:#1f3a5f,stroke:#7aa2d8,color:#ffffff
    classDef human fill:#6b4514,stroke:#e0a95a,color:#ffffff
    classDef out fill:#1e4d3a,stroke:#6fcf97,color:#ffffff
    style M fill:transparent,stroke:#7f8c9a,stroke-dasharray:4 3
```

**Segments, not one campaign.** More than 20 segments, cut by market, by role and by the problem the engineer has: migrating off an end-of-life incumbent, logging boreholes in the field, getting ground data into Civil 3D. Each segment got its own creative, its own lead magnet and its own landing. Campaigns ran in the local language, including Brazil and Turkey, where the regulatory context does part of the selling.

![LinkedIn Campaign Manager, the segment campaigns side by side](../../assets/chapter-2/linkedin-campaigns-by-segment.png)

*LinkedIn Campaign Manager, one line per segment: Brazil, Turkey, US and Canada, Fugro alumni, Italy, the migration off the incumbent, Europe, DACH, Benelux, and a website-visit line for the Civil 3D download. Figures blurred.*

**Native lead forms into the CRM.** Most leads were captured in LinkedIn's native forms rather than on a landing page, and landed in HubSpot with their campaign stamped. From there: a sequence matched to the segment, and a Teams notification tagging the colleague who follows up. The sequences were semi-automated by design. The emails went out on a schedule; the reply was always a person. Enrolment ran in bulk: the freelancer loaded the leads into a sequence and picked the email signature to match the sequence and the segment, so each segment heard from the right colleague.

![HubSpot sequences, one per segment and trigger](../../assets/chapter-2/hubspot-sequences-by-segment.png)

*The sequence list in HubSpot: one per segment and trigger, the owner in brackets. The ones marked dynamic switch from automated emails to manual steps as soon as the lead engages.*

![One sequence: automated email, delay, then a rep-led task](../../assets/chapter-2/hubspot-sequence-automated-then-rep-led.png)

*Inside one sequence: an automated email, a delay of five business days, and the switch to a rep-led task after two opens or one click. The task pauses the automation and lands with the contact owner.*

![A sequence email with the signature chosen for the segment](../../assets/chapter-2/sequence-email-signature-per-segment.png)

*A Fugro alumni email as sent, written as one alum to another and signed by the head of product. The signature was chosen per sequence and segment at enrolment. Recipient blurred.*

**A monthly scorecard.** Spend, leads and the share that qualified, per campaign, in one table. Creative fatigue was flagged by rule when click-through fell or cost per impression rose past a threshold. Lines that had produced nothing for a quarter were cut and the money moved. The scorecard was built once and regenerated every month.

**The attribution join.** LinkedIn's numbers and HubSpot's deals joined on the contact, which showed that paid social was feeding the top of the funnel rather than closing deals on its own. That changed how campaigns were judged: by qualified leads, not by last-touch revenue.

## What stayed human

Where the budget went each month, and which campaigns to kill, scale or hold. The scorecard proposed; a person decided, usually me. The copy of every sequence was written and signed by a person.

## What it did

Paid social became the #2 lead source. The campaign markets show up in the funnel as new countries, Brazil and Turkey among them.
