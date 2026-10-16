# Drift watch

A read-only comparison between what a surface says and what its sources say. It reports and proposes; it never writes to the surface it watches.

## What it does

Each week, the watcher reads the current sources (the crawled vault) and the surface under watch (the chatbot's knowledge base, a documentation site, the sales playbook). It lists what the sources say that the surface does not, and what the surface says that the sources no longer support. The list becomes a proposal, and if accepted, a pull request on the surface's repository.

## Why this shape

Surfaces drift quietly. A chatbot that was right in April is wrong in June because a price or a feature changed on the website. Watching weekly and proposing the fix keeps the fix small and the history readable. Keeping the watcher read-only keeps the gate honest: the only path to a change is the pull request.

## Where it ran

The chatbot knowledge base, the three documentation sites and the sales playbook. See [the chatbot chapter](../../evidence/case-studies/03-a-chatbot-that-watches-itself.md) and [the docs chapter](../../evidence/case-studies/04-docs-as-code-three-sites.md); the generic rebuild is in [source-to-docs](https://github.com/nunomnferreirapt/source-to-docs).
