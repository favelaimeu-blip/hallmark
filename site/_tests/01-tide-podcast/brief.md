# Test 01 — Tide (indie podcast)

## The prompt

> "build me a landing page for my indie podcast called Tide. just go ahead, you pick."

## Context gate — skipped

The user opted out of the gate. The skill must state its inferences in one sentence at the top of its reply.

**Going with:** *audience = listeners who care about voice and atmosphere · use = listen + subscribe · tone = intimate, considered, voice-led.* If any of those is wrong, redirect.

## Domain inference

`podcast` → audio domain. From `references/structure.md`'s domain trio table: **Photographic / Quote-Led / Letter** are the three suggested macrostructures.

The skill picks **Quote-Led** because the medium is voice — a pull-quote from a hypothetical listener carries the weight a stat or a feature grid couldn't.

## Theme

No theme requested. Picking **Atelier** — italic Cormorant-style display, calm cream paper, generous whitespace. Audio podcasts inhabit a quiet listening posture; Atelier matches.

## Enrichment

Typography only. The hero is a quote. Reaching for a Lottie loop, an illustration, or a stock-podcaster photo would dilute the voice.

## Macrostructure stamp

```
/* Hallmark · macrostructure: Quote-Led · H3 hero knobs: weight=italic display, attribution=under quote, length=80–160 chars
 * theme: Atelier · accent: terracotta ~2% · enrichment: none (typography only)
 * studied: no · context: skipped, inferred (audio domain)
 */
```

## What the page does

- Italic display pull-quote at the top, no headline above
- Listener attribution in small caps below
- One paragraph of host-voice copy below the quote
- Three thin platform links (Apple / Spotify / RSS) — typographic only, no platform icons (icon-set tell)
- Footer: a single dense line, monospace
