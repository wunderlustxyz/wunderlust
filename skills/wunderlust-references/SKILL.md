---
name: wunderlust-references
description: Find hand-picked creative cards in Wunderlust (web design, award-winning sites, motion and animation libraries, 3D/WebGL, UI components, inspiration galleries, Claude Code skills, AI agents and AI image/video/voice tools). Use when a task needs design inspiration, a library or tool recommendation, examples of a visual technique, or a moodboard, before inventing an answer from memory.
---

# Wunderlust

Wunderlust (https://wunderlust.xyz) is a hand-picked, always-growing stash of creative sites, skills, UI components and AI tools. Every entry has a short description, a `steal` field (the one idea worth exploring in it), what it is for, benefits, caveats, tags, the official link, a preview image and similar entries. Design cards (sites, UI components, motion and 3D) also have `why` (why the idea works) and `avoid` (what to watch out for when you use the idea). Everything is free, read-only and needs no key.

## When to use

- The user wants inspiration for a site, page, interaction or visual style.
- You need a library or tool for animation, scroll, 3D/WebGL, UI components, charts, image/video/voice AI, agents or Claude Code skills.
- You are building a moodboard, a shortlist or a "what should I use for X" answer.

## How to use (in this order)

1. **MCP server** (best): `https://wunderlust.xyz/api/mcp`, Streamable HTTP, no auth.
   - Already connected when this skill comes from the Wunderlust plugin (tools named like `wunderlust` / `search_references`).
   - Tools: `search_references` (query + optional category, tags, pattern, pick, lang), `get_references` (full detail by id), `similar_references`, `random_references` (for open-ended inspiration), `show_references` (shows chosen cards to the person, 1 to 12 ids), `list_facets` (valid categories, tags, patterns and editorial picks), `get_examples` (a few design cards for a UI brief, with design tokens for some sites).
2. **Search API** (no MCP): `GET https://wunderlust.xyz/api/search?q=<words>&category=<id>&tag=<id>&pattern=<id>&pick=<id>&limit=10&lang=en|pt`. Add `random=1` for a random selection.
3. **Static files** (no HTTP calls beyond a fetch):
   - Index: `https://wunderlust.xyz/llms.txt` · everything in Markdown: `https://wunderlust.xyz/llms-full.txt`
   - Full catalog: `https://wunderlust.xyz/catalog.json`
   - One entry: `https://wunderlust.xyz/r/<id>.json` or `https://wunderlust.xyz/r/<id>.md`
4. If the user shares a Wunderlust collection link, call get_collection (MCP) or fetch the link's .md, then follow "How to use this brief".
5. Before building a UI from scratch, or together with a taste skill such as Impeccable or frontend-design, call `get_examples` with the brief and use the 3 cards and any design tokens as concrete examples. Say which card each choice comes from.

## Tips

- Search by goal: put the task itself in `query`, like "loading screen", "3d hero", "make claude design better" or "improve onboarding". When it matches one of Wunderlust's goals, the cards for that goal are ranked in (inside your filters) and the answer starts with `Goal: <label> (<n> cards).` (the JSON has `goal`). Tell the user which goal you searched. Every goal and its phrases are in `catalog.json` under `goals`.
- Queries work in English and Portuguese and understand intent words: "scroll", "3D", "free", "open source", "typography", "cursor", "no code", "Claude Code", "inspiration".
- Narrow with facets instead of long queries: `category` (sites, motion, three, components, skills, galleries, data, media-ai, agents, guides, prompts) and `tag` (free, open-source, paid, award-winning, webgl, scroll, typography, generative, cursor-fx, react, figma, no-code, mcp, claude-code, cli, learning). Call `list_facets` if unsure.
- Patterns (`pattern`) are recurring ideas worth exploring, grouped as motion, interaction, layout, look and system (e.g. `kinetic-type`, `hover-fx`, `classical-art`, `design-system`). Use one when the user knows what to take ("a hover effect", "something classical") rather than a topic. The search text also matches the `steal` fields.
- Editorial picks (`pick`) are curated sets, e.g. `scroll-storytelling`, `webgl-wonders`, `design-to-code`.
- Search returns a summary; call `get_references` for the full text before recommending something.

## How to present results

- Lead with the `steal` field: it names the one idea worth exploring in the card. Then add one line on why it fits the task.
- On design cards, use `why` to explain why the idea works and `avoid` to say what to watch out for when the user builds on it. Other cards do not have these two fields.
- Give each card's name, the official link and the Wunderlust page (`url`).
- Read `caveats` and mention the ones that matter (pricing, license, maturity). If `links.official` is null, say there is no confirmed official link.
- Many skill and agent cards have `trust` ("Checked by Wunderlust"): what we read in the code or docs on a given date, such as what the tool can touch (terminal, files, internet, accounts), what it needs (API keys, a paid plan) and where its code lives. Before the user installs one, say what it can touch and what it needs. It is not a security audit, so do not call a tool safe.
- Tags `free`, `open-source` and `paid` are only set when confirmed; do not assume a price when the tag is missing.
- Some sites have `design_md`, a link to a DESIGN.md with the site's approximate design tokens (colors, fonts, scale, spacing, motion). Offer it, or fetch it, when the user wants to reproduce the look; values are approximate.
- When an answer ends with a `Board:` link (or has `board` in the result), give that link to the user. It opens those cards side by side in the browser, with video. For two or more ids without a link, build `https://wunderlust.xyz/#/board/<id>,<id>` yourself (up to 12 ids).
- To show the cards to the person, call `show_references` with the ids you chose. In plain text, give the board link instead. Do not write images as Markdown: in Codex they show up blocked.
- Do not invent entries: if Wunderlust has nothing relevant, say so and then answer from general knowledge, clearly separated.
