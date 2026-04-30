# AI usage disclosure

This page was built and edited with the help of an LLM (Anthropic Claude Opus 4.7, accessed via Claude Code in a terminal). This file exists so the provenance is honest and auditable: what the model did, what the human directed, and the sequence of prompts that produced each change.

## What the human directed

- All editorial decisions: which sources to trust, what to fact-check, what to add or remove, what tone to take.
- Verification of every factual claim against the official sources (matrix.org announcement, governing-board page, members page, matrix-community.events).
- Visual judgement: flagging when contrast was bad, when edges were clipped, when mobile was broken, when a CTA was redundant.
- The decision to include the candidate-podium event description and the Openki link.
- The decision to disclose this AI usage publicly.

## What the model did

- Wrote and edited HTML/CSS/React code in `index.html` (single-file bundle with inlined fonts and gzipped JSX).
- Fact-checked claims by fetching matrix.org and matrix-community.events and comparing them against the existing copy.
- Wrote prose for the disclaimer strip, the candidate-podium description, the reconciliation note, and CTA labels.
- Diagnosed bugs (missing viewport meta, clipping issues, broken link).
- Repackaged the gzip+base64 bundler manifest after each edit.

The model did not invent any factual claims about the Matrix Foundation, the Governing Board, the election timeline, or the Community Summit — every dated fact came from the linked sources and was cross-checked. Where wording was paraphrased rather than quoted (e.g. the "~3 hrs/week" specification of "a few hours a week"), this is noted in the page itself or stays close to the source phrasing.

## Sources of truth (verified)

- <https://matrix.org/blog/2026/04/election-announcement/>
- <https://matrix.org/foundation/governing-board/>
- <https://matrix.org/foundation/governing-board-elections/2026/>
- <https://matrix.org/foundation/members/>
- <https://matrix.org/foundation/working-groups/>
- <https://matrix.org/legal/trademark-policy>
- <https://matrix-community.events/conferences/2026-summit.html>
- <https://openki.matrix-community.events/course/9ZJDAu2dbj9d4qPZ2>

## Prompt log

Prompts are reproduced verbatim where short, paraphrased where they referenced screenshots or tooling artefacts. The chronological order matches the commit history on `main`.

1. *"create a repo at github/yncyrydyl/matrix-foundation-election-2026 and deploy it to github pages. clean up the repo first"*
2. *"as a matrix foundation expert and journalist make a fact check on that website and improve."*
3. *"where is the announcement and the matrix.org page not aligned"*
4. *"only compare the election announcement and the rest of the matrix.org site for now."*
5. *"now apply this to our infographic page. and also make the point in time 'this is today' dynamic"*
6. *"check all the links"*
7. *"make a small disclaimer at the top. this is redrawing of the announcement by yan minagawa repo @ github. make it nice and link it."*
8. *"make the matrix logo white and nice."*
9. *"add some call to actions — nominate people or yourself. also announce that there will be a possibility of a podium event at the matrix community summit"*
10. *"shit to read"* — with a screenshot of the disclaimer being illegible on a dark background.
11. *"make the waves as the background of the timeline"*
12. *"check matrix-community.events/conferences/2026-summit.html for dates. also take the logo and get the event including the logo in the zeitstrahl"*
13. *"we don't need the hero with the wave at the top / it's just schedule not schedule.json / link to opavote pls"*
14. *"the edges of the zeitstrahl are cut"* — with a screenshot showing edge labels clipped.
15. *"give me a description text for the candidate podium at c-base. it will be streamed and recorded — at least partly."*
16. *"put the link https://openki.matrix-community.events/course/9ZJDAu2dbj9d4qPZ2 into the community summit announcement"*
17. *"remove the 'Summit programme' CTA"*
18. *"how does all this look on mobile?"*
19. *"no difference on my phone"* (root cause: missing viewport meta tag)
20. *"the summit logo looks cut on mobile"*
21. *"reveal the usage of llm including the used prompts to the repo"* — produced this file.
22. *"add a little disclaimer to the message at the top about the usage of llm including a link to the prompt file. and include the prompt."* — extended the on-page disclaimer strip to mention LLM assistance and link here, and appended this prompt to the log.
23. *"make a nice preview with matrix chats when the url is posted"* (with a screenshot of an Element link preview showing "Unpacking…" as the description, because no Open Graph tags were set). Generated `og-image.png` (1200×630) with PIL — cream background, [matrix] dark plate, big title with green "2026", flowing wave layer, subtitle "27 Apr — 15 Jun · Six weeks. Five phases. · Ballot via OpaVote." — and added Open Graph + Twitter Card meta tags plus a `<meta name="description">` so the preview no longer scrapes the bundler's loading message.

## How to reproduce

The original `index.html` was a self-contained React infographic with an inlined gzip+base64 bundler. Edits in this session unpacked the bundle, modified the JSX (`470758bf-9a73-4631-910e-e8ac7954c5f7`) and the HTML template, then re-gzipped, re-base64-encoded, and re-injected into the bundler manifest with `</script>`-safe JSON encoding. The full transform script lives only in commit history, but every commit message describes the change in plain English.

## Trademark and authorship

- The Matrix logo is a trademark of [The Matrix.org Foundation](https://matrix.org). Use here is descriptive, not endorsing — see <https://matrix.org/legal/trademark-policy>.
- Editorial authorship: Yan Minagawa.
- Code authorship: human-directed, model-assisted, as described above.
