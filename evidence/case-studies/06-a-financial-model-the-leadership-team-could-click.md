# A financial model the leadership team could click

*The five-year model rebuilt as a Lovable app for the investment-committee presentations to Fugro's CEO and CFO: scenarios, levers, one screen per decision, instead of a spreadsheet passed around by email.*

## Before

The five-year plan was a spreadsheet. Every investment-committee meeting re-derived the same questions from it: what happens if churn is two points higher, what if the new market lands a year late, when does this stop needing the group's money. The answers took a week to produce and were stale by the meeting.

## What we built

**The model as a file, not a sheet.** Five bets, each a small formula with named dials, in one JSON file. Every dial has a preset for three scenarios: conservative, estimated and ambitious. 2026 is pinned to actuals and never moves; the sliders only move 2027 to 2030. A reconcile script recomputes every bet from its formula and ties the headline totals to the written narrative, so the model cannot quietly drift from the document that explains it.

**A page the board can touch.** Built in Lovable from one prompt and the JSON file, in about two hours. One chart, with the headline as stacked bands per bet. Scenario chips that set every dial; the moment someone moves a slider, the chip says "Custom". Per-bet toggles that pull a bet in or out of the headline live. Live KPIs that recompute on every drag: customers, revenue per customer, growth rate. A second chart answers the only question a CFO asks in a cost year: when does this stop needing internal funding, with the cost allocation and the funding line as inputs.

**Words without numbers.** The narrative notes on the page carry no figures by design. Any number copied into prose would drift from the chart. Every number shown is rendered live from the model.

**Fixes as surgical prompts.** Lovable builds fast and breaks easily. Each correction was written as the smallest possible instruction, scoped to one section, with the constraint spelled out: change this label, touch nothing else. The prompts were kept in the repository next to the model, so the page can be regenerated.

## What stayed human

The bets themselves, the dials and their presets. The model computes; it does not decide what to believe. In the meeting, the scenario the room landed on was argued, not calculated.

## What it did

The investment-committee presentations to Fugro's CEO and CFO, and the GeoDin board meetings, ran on this page. Each bet carried a proof point, an owner, a cost and a gate date, so the board could decide on evidence. The plan it showed has EBITDA at break-even in 2027.

## What I would do differently

Set the one open price in the model earlier. A placeholder understated it for months and anchored internal conversations low.
