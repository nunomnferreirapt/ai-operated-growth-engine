# A chatbot that watches itself

*Built with two freelancers for about USD 2k, live in under a month, two closed deals in four months; its knowledge base is a versioned, PR-reviewed repo, and a weekly drift watch proposes the edits.*

## Before

A contact form and an email address. Prospects with a question waited for office hours; existing customers with a licensing problem waited longer. The product's own knowledge (pricing, integrations, how to migrate an old license) sat in people's heads and in a German support portal.

## What we built

**A small expert team instead of an agency.** I wrote the spec and hired two freelancers through Upwork: one on the n8n engineering (the agent workflow, the tools it can call, the CRM hookup), one on the conversation design (intent lanes, qualification, the Miro flows). Weekly design sessions on the n8n canvas. Live on the website in under a month, for about USD 2k.

**The knowledge base as a git repository.** The bot answers from a set of markdown files, versioned in a repo, changed only through pull requests. That repo was also the contract between the two freelancers: the conversation flows reference the files by name. Built in English, the bot replies in the visitor's language.

**A weekly drift watch.** Every week a read-only job compares the knowledge base with what the website, the docs and the support articles currently say, and proposes the edits as a pull request. A person reads and merges. The bot never updates itself.

**Guardrails as files.** The rules for what the bot may and may not do are in the same repo and are only ever changed by hand. Real visitors tried the usual things: fake urgency, persona overrides, "which tools are you using". The rules held.

## What stayed human

Every change to what the bot knows or how it behaves. The handoff of anyone who wants to buy, which goes to a person in sales. And the handover itself: the engagement was set up so we could maintain what the bot knows ourselves, through pull requests, and we did; the workflow itself stayed with the freelancer on a light maintenance basis.

## What it did

Two closed deals in four months, one of them logged in the CRM under the name "Chatbot" by whoever created it. Customers started treating the bot as the front door for licensing questions, including returning ones.

## What broke

Once, a customer said they wanted to buy, the bot said it had passed the request to sales, and nothing had been sent. The customer waited and then escalated by email. The deal still closed. What made failures like that cheap to fix: the bot's brain lives in GitHub and sits in the weekly loops, so a correction went from pull request to production in days, not in a vendor ticket.
