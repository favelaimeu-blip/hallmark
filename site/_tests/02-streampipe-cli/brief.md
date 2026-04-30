# Test 02 — Streampipe (open-source CLI)

## The prompt

> "Make a docs landing for an open-source CLI called Streampipe. It does stream parsing for log/event pipelines. Use the Terminal theme. Audience: backend developers. Use case: install the tool and read the docs. Tone: technical, terse."

## Context gate — fully answered

The user provided audience + use + tone. No inference needed.

## Theme — explicitly requested

**Terminal**: dark phosphor-on-black, monospace throughout, no animations, square edges.

## Macrostructure

`docs / CLI / open-source / developer` → from the domain table: **Workbench / Long Document / Component Playground**. The skill picks **Workbench** because the brief is a docs landing — it asks the page to walk the user through the tool, not just announce it.

## Enrichment

A small Tier-A pure-CSS terminal mockup as the hero — `$ streampipe parse access.log --filter status=5xx | jq` rendered in monospace with a phosphor caret. No real terminal capture. No image. Custom-built.

The decision is *not* "add a Lottie loop of a terminal typing"; that would be the Lottie shortcut. Pure CSS art does this cleaner.

## Macrostructure stamp

```
/* Hallmark · macrostructure: Workbench · F2 sticky-scroll knobs: pinned=right, content=code, steps=3
 * theme: Terminal · accent: phosphor-green ~6% (functional, not decorative) · enrichment: E1 hero — pure-CSS terminal mockup (Tier A)
 * studied: no · context: explicit
 */
```

## What the page does

- Hero: monospace headline `$ streampipe --help` + a CSS-art terminal output mockup
- Install row: three install commands (npm, brew, curl) as inline copy blocks
- Three numbered feature blocks (1.0 / 2.0 / 3.0) — what it does, in plain language
- Spec sheet (F3) for flags
- Footer: dense colophon

No animations. Square edges. Underlined links. Quiet phosphor accent only on prompts and link underlines.
