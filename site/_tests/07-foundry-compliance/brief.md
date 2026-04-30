# Test 07 — Foundry (SOC2 / ISO27001 compliance automation)

## The prompt

> "Build a landing page for Foundry — SOC2 and ISO 27001 compliance automation for B2B SaaS. Show: how many companies got compliant, what it costs, who uses it. Audience: founders + CTOs. Tone: technical but trustworthy."

## Context gate — fully answered

Audience, use, tone all explicit. No inference needed.

## Domain inference

`platform / tool / infra / observability / dashboard SaaS` (try-or-talk-to-sales) → from the refined trio table: **Bento Grid / Workbench / Stat-Led** are reasonable picks.

The skill picks **Stat-Led** because the brief explicitly leads with a number ("how many companies"), and compliance is a *proof-by-numbers* sale. The hero is one giant number; every section anchors on a stat.

## Theme

The previous SaaS test (Tracejam) used **Pastel** (light · geometric-sans · cool-indigo). Diversification rule says the next theme must differ on at least one of three axes. **Newsprint** (light · roman-serif Playfair · warm-deep-red) differs on two — display style and accent hue. Plus Newsprint reads as *trade publication serious*, which is the right register for compliance. Pick: Newsprint.

## Enrichment

**None.** Stat-Led's hero is the number; adding a mockup would dilute the proof. A typographic-only hero is correct here. Per the enrichment hierarchy, this is Tier 0 (typography only) — the strongest hero a Stat-Led page can have.

## Microinteractions

The skill's new microinteractions rule says Stat-Led is **default-on**. Three primitives (max), purposeful:

1. **Number reveal** on the "847" — IntersectionObserver triggers a `requestAnimationFrame` count from 0 to target over 1.4 s, ease-out. Reduced-motion: render the final value instantly.
2. **Pricing card hover lift** — `translateY(-3px)` + shadow upgrade, 180 ms ease-out. Active state drops back at 60 ms.
3. **Recommended-tier pulse** — one-shot `@keyframes pulse-border` 2 s, runs once on viewport entry. Subtle: opacity 0.4 → 1 → 0.4 on the border. Doesn't loop.

## Macrostructure stamp

```
/* Hallmark · macrostructure: Stat-Led · S1 hero knobs: number=8xl, alignment=left-bias, supporting=enumerated
 * theme: Newsprint · accent: deep-red ~3% (band rules + recommended-tier)
 * enrichment: none (typography only — the number is the hero)
 * studied: no · context: explicit
 * motion: number-reveal (counter), pricing-lift, recommended-pulse — three primitives, default-on per archetype
 */
```

## Diversification axes (Newsprint vs prior outputs in this test set)

| Theme | Paper band | Display style | Accent hue |
| --- | --- | --- | --- |
| Pastel (Tracejam) | light | geometric-sans | cool-indigo |
| **Newsprint (Foundry)** | **light** | **roman-serif** | **warm-deep-red** |
| Differs on | (same) | DIFFERS | DIFFERS |

Two of three axes differ. Passes the theme-diversification rule.

## What the page does

1. **Hero (Stat-Led).** "847" big enough to be the room. Supporting prose: "companies passed audit using Foundry. Avg time-to-compliant: 31 days, vs industry avg of 9 months."
2. **Logo wall.** 8 customer wordmarks, monochrome, tabular, one row.
3. **Stats grid.** Three supporting numbers — pass rate, avg days, hours saved.
4. **Features (4 cards).** Continuous monitoring · Auto-evidence collection · Vendor risk · Audit-day support.
5. **Testimonials (3).** Pull-quote, name, role, company. Specific to use cases.
6. **Pricing (3 tiers).** Starter $299/mo · Team $899/mo (recommended) · Scale (custom). Feature checklist per tier. Animated pulse on Team.
7. **FAQ (8 questions).** Conversational FAQ, expanded by default.
8. **CTA strip.** "Start your audit. 14 days free." One button.
9. **Footer.** Index-style, 4 columns.

The page is intentionally long — it demonstrates the SaaS page sequence rule from `macrostructures.md`: hero → social proof → features → testimonials → pricing → FAQ → CTA → footer.
