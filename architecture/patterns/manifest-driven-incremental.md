# Manifest-driven incremental runs

A hash per source decides whether anything runs at all. Most weeks, for most skills, nothing changed, and nothing ran.

## What it does

Every source file an agent reads has a hash in a manifest. Before an agent starts, a script compares the current hash with the stored one. Unchanged means skip. Changed means the agent runs on that item only. The manifest is committed with the output, so the diff shows exactly what moved.

## Why this shape

Agents cost money and attention. A check that costs nothing in front of each one keeps both spent only on real change. It also makes a weekly chain affordable to leave running: a quiet week costs a few hash comparisons.

## Where it ran

The docs source pipeline, the transcript extractor, the chatbot drift check and the docs drift watch. The crawlers rebuilt their indexes in full; the generic rebuild in [platform-profile](https://github.com/nunomnferreirapt/platform-profile) extends the manifest to crawled pages, with the date each was fetched.
