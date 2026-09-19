---
name: research-efficiency
description: Reduce unnecessary Claude Web research and context tokens while preserving accuracy, source quality, coverage, and reasoning depth. Use for research, web search, analysis, and long-context tasks.
---

# Research Efficiency

## Goal

Minimize total task tokens by removing low-value search, fetch, repetition, and context growth — **not** by making the answer shallow.

Preserve:
- factual accuracy and important caveats
- source quality and citation support
- necessary verification
- reasoning depth needed by the task
- the user's requested level of detail

Do **not** reduce effort level merely to save tokens.

## 1. Plan before researching

For research or analysis:
1. Define the exact question and the minimum subquestions needed to answer it.
2. Prefer a small set of targeted searches over many broad searches.
3. Avoid searching for facts that are already established in the conversation or a trusted source already retrieved.
4. Set a stopping rule: stop when the key claims are supported, major contradictions are checked, and additional searching is unlikely to change the answer materially.

Do not announce the whole research plan unless useful to the user.

## 2. Search efficiently

- Use precise, high-signal queries.
- Combine closely related facts into one search when one query can retrieve them.
- Search the authoritative or primary source first when practical.
- Use secondary sources mainly to cross-check, add context, or cover gaps.
- Do not open every result. Open only sources that can answer an unresolved subquestion or verify an important claim.
- Deduplicate near-identical sources. One strong source is better than several copies of the same reporting.
- When a result snippet already establishes a low-risk fact, do not fetch a long page solely to repeat it.

## 3. Fetch selectively

When a page, document, or file is large:
- retrieve only the relevant section when the tool supports targeted retrieval
- avoid re-reading content already extracted
- do not paste or carry large raw passages forward when a compact evidence note is sufficient
- never sacrifice evidence needed to resolve an ambiguity, contradiction, or important claim

For direct web links, be especially careful with long pages: fetching an entire article/document can consume substantial context. Prefer targeted search or focused retrieval when that is enough.

## 4. Maintain a compact evidence ledger

During multi-source research, internally track each useful source as:

**Claim → Source → Date → Evidence → Confidence/uncertainty**

Keep only what is needed for synthesis. Do not retain duplicate explanations of the same fact.

For conflicting sources:
- keep both until the conflict is resolved or clearly stated
- prefer the more authoritative, direct, recent, and relevant evidence
- never hide a material disagreement just to save tokens

## 5. Prevent context bloat

Do not:
- restate the user's prompt
- repeat the same conclusion in multiple forms
- copy full search results into later reasoning
- re-read unchanged sources without a new reason
- keep obsolete intermediate notes after their useful facts have been extracted

Do:
- compress old findings into short, loss-aware summaries when the session becomes large
- retain exact numbers, dates, names, quotations, URLs/citations, and other details that may be needed later
- keep raw source material available conceptually only when it may be needed to verify a disputed point

## 6. Quality gates

Never save tokens by skipping:
- verification of important or current facts
- source citations required by the task
- security, safety, legal, medical, financial, or other high-stakes caveats
- testing or validation that materially affects correctness
- information necessary for a first-pass correct answer

If uncertainty is genuine, state it briefly and specifically.

## 7. Final answer behavior

The final response should be **normally clear and appropriately detailed**, not forced into Caveman-style language.

Use concise structure:
- answer first
- only the reasoning needed to understand the result
- include supporting evidence/citations where required
- include caveats only when decision-relevant
- avoid repeating information already visible in the conversation

A request for a detailed or exhaustive answer overrides default brevity.

## 8. Adaptive intensity

Use the lightest efficient workflow that still reaches a reliable answer:

- **Simple factual question:** minimal search and verification.
- **Moderate research:** targeted search + a few authoritative sources + contradiction check where needed.
- **Deep research:** broader source coverage, explicit subquestions, cross-checking, and synthesis.
- **High-stakes or contested topic:** prioritize verification and source quality over token savings.

Never optimize for a fixed percentage reduction. Optimize for the **lowest-cost path that preserves answer quality**.

## 9. Important limitation

This skill can reduce unnecessary **input/context/tool-use tokens** and verbose output. It cannot directly control Claude's hidden reasoning tokens or guarantee a fixed percentage of savings.

The objective is:
**same-quality answer, less wasted context and research work.**
