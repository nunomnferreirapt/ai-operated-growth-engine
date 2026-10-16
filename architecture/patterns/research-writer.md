# Parallel research, one writer

Research in parallel, writing in sequence. Three agents gather claims with quotes from allowed sources; one writer turns the merged claims into a draft; a deterministic check refuses any sentence that is not backed by a citation.

## What it does

1. A brief names the topic, the audience and the allowed sources.
2. Three research agents, each with a different angle, list claims with a verbatim quote and a source id.
3. The claims are merged and deduped.
4. One writer drafts from the claims list only, citing a source after every factual sentence.
5. A script checks that every citation exists, every quoted passage is really in the source, and every sentence with a number or a name carries a citation. Fail means rewrite, not publish.

## Why this shape

Research benefits from several views; prose does not. One writer keeps one voice. The check at the end is what let independent industry platforms publish the pieces: every claim could be traced.

## Where it ran

Long-form articles that independent platforms chose to publish. See [the content chapter](../../evidence/case-studies/02-paid-media-that-ends-in-a-human-follow-up.md) for the surrounding motion and [article-pipeline](https://github.com/nunomnferreirapt/article-pipeline) for the rebuild.
