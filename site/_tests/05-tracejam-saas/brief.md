# Test 05 — Tracejam (SaaS observability tool)

## The prompt

> "Build a landing page for Tracejam — a tracing/observability tool for distributed systems. Audience: SREs and platform engineers. Use case: try it / contact sales. Tone: technical."

## Context gate — fully answered

Audience, use, tone all explicit. No inference needed.

## Domain inference

`platform / tool / infra / dashboard / developer` → from the domain table: **Workbench / Bento Grid / Stat-Led** are reasonable picks.

The skill picks **Bento Grid** because Tracejam has many surfaces (traces, metrics, alerts, logs) and Bento communicates "many entry points" the way Workbench would communicate "one thing, walked through". Workbench was the runner-up.

## Theme

The tempting default for a SaaS observability tool is **Midnight** (dark technical). But the skill resists: Midnight has been used elsewhere, and the brief says "technical" not "dark". Picking **Pastel** instead — post-Linear soft tech, low-chroma indigo accent, soft surfaces. The test is whether a Pastel page can still feel rigorous to an SRE; the answer is yes if the typography is exact.

## Enrichment

**E1 Demo Video — Clipped-Edge** archetype, but with a Tier-A pure-CSS dashboard mockup instead of real video. The mockup is a hand-built CSS-art trace waterfall (a flame chart) — it says "this is real software" without needing to ship a 4 MB video.

The decision is *not* "embed a Loom". *Not* "use a stock video". *Not* "build a Lottie loop of moving bars". Pure CSS art is the right tier — the dashboard is geometric, the data are coloured rectangles, and CSS does that beautifully.

## Macrostructure stamp

```
/* Hallmark · macrostructure: Bento Grid · F1 bento knobs: tiles=6, spans=irregular, accent=corner-only
 * H7 hero: Demo Video Clipped-Edge · clip=right, aspect=16/10, frame=hairline
 * theme: Pastel · accent: indigo ~3% · enrichment: tier-A CSS art mockup (flame chart trace waterfall)
 * studied: no · context: explicit
 */
```

## What the page does

- Hero: clipped-edge browser-frame mockup containing a CSS-art trace waterfall (a flame chart of an HTTP request fanning out into ~20 spans across four services). Headline left, mockup right, mockup extends ~12 vw past the viewport edge.
- Bento grid below: six asymmetric tiles, each one a feature with its own visual treatment (a numerical stat, a small CSS chart, a code snippet, a quote from a user, a tabular table of integrations, a single sentence)
- Two CTAs: "Try it" (outlined chip) and "Talk to sales" (typographic link)
- Footer: index columns
- Soft 12 px radius on every card. Indigo accent at ~3 % footprint.
