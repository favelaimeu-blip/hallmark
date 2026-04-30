# Test 06 — Anya (software architect personal site)

## The prompt

> "I'm Anya, a software architect. Build me a one-pager. Don't ask me questions, just figure it out."

## Context gate — skipped (explicit)

The user explicitly opted out. Skill must state inferences in one sentence at the top of the reply.

**Going with:** *audience = engineering leaders considering Anya for hire / consult · use = read about Anya, then contact · tone = technical-but-warm, restrained, prose-led.* If any of those is wrong, redirect.

## Domain inference

`personal / resume / one-pager / individual` → from the domain table: **Long Document / Letter / Index-First**.

The skill picks **Long Document**. Letter was the runner-up and would have produced a warmer page; Long Document is the more credible shape for a senior IC at this career stage.

## Theme

The default attractor for "personal portfolio" is Specimen, and that's exactly the trap. The skill picks **Studio** — italic Fraunces display, forest-green accent, Geist body. Studio is the modern editorial agency aesthetic, and a senior software architect's one-pager benefits from looking like a small design studio's about page rather than a CV.

## Enrichment

**None.** Typography only. The decision is deliberate — a personal site that hand-builds a Lottie or commissions a Midjourney portrait of itself reads as overcompensating. Restraint is the credibility signal here.

The slop test catches: no abstract gradient background ("decoration without purpose"), no Three.js spinning name ("3D for a still object"), no demo video ("there's nothing to demo"), no aurora-blob ("never").

## Macrostructure stamp

```
/* Hallmark · macrostructure: Long Document · H5 hero knobs: salutation=greeting, body=2 paragraphs, signoff=initials
 * theme: Studio · accent: forest-green ~2% (a single mark)
 * enrichment: none (typography only — restraint is the credibility signal)
 * studied: no · context: skipped, inferred (personal / portfolio domain)
 */
```

## What the page does

- Italic display salutation: "Hello, I'm Anya."
- Two short paragraphs, italic display + roman body, on what Anya does and how she works
- A tabular "selected work" sheet: four projects, each one a single line — year · client · what changed
- A "currently" line in italic noting present focus
- A small "elsewhere" line: GitHub · LinkedIn · email
- Footer: a single dense colophon line

The page is one fold tall on a 1440 px display. That's the point.
