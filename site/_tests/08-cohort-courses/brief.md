# Test 08 — Cohort (cohort-based courses platform)

## The prompt

> "Build a landing page for Cohort — the platform for cohort-based courses. Run live courses with 30 to 500 students. Built for educators, not LMS sales teams. Audience: course operators + indie creators. Tone: warm, salon-room, editorial."

## Context gate — fully answered

Audience, use, tone all explicit.

## Domain inference

Education-tech / creator-tool / B2B-light SaaS. The brief is *operator-facing* (educators run courses), not student-facing. From the macrostructure catalogue: **Marquee Hero · Long Document · Workbench** are reasonable picks for "creator tool with showcase work."

The skill picks **Marquee Hero** because the brief implicitly says "show me the courses already running." A continuous-scroll band of course titles + instructors is the proof — and it does the social-proof job without a separate logo wall section.

## Theme

Last test was Foundry on **Newsprint** (light · roman-serif · warm-deep-red). Tracejam before was **Pastel** (light · geometric-sans · cool-indigo). Diversification axes for the next theme:

| Theme | Paper band | Display style | Accent hue |
| --- | --- | --- | --- |
| Pastel (Tracejam) | light | geometric-sans | cool-indigo |
| Newsprint (Foundry) | light | roman-serif | warm-deep-red |
| **Salon (Cohort)** | **light** | **mono** | **warm-amber** |

vs Foundry: paper-band same · display style differs · accent same family but different hue (deep-red vs amber).
vs Pastel: paper-band same · display style differs · accent differs.

Two of three differ from Foundry. Three of three differ from Pastel (counting hue tint). **Passes.**

Salon as a theme: light warm paper, mono display (IBM Plex Mono), warm amber accent, generous spacing, centered emphasis. The unusual choice — mono display on a course-platform marketing page — gives Cohort the "letterpress-y, instructor-room" feel the brief asked for ("salon-room, editorial").

## Enrichment

The marquee IS the enrichment. **No additional mockup, no illustration.** The continuous scroll of course titles is what makes the page feel inhabited. Per `hero-enrichment.md`, this is enrichment archetype **Animated Loop (E6)** delivered via continuous CSS marquee — Tier A custom-craft, no Lottie.

## Microinteractions

Cohort is a Marquee Hero — **default-on archetype** per the new microinteractions rule. Three primitives, max:

1. **Marquee scroll** — continuous CSS `@keyframes marquee` translateX(-100%) over 50 s, infinite. Pauses on hover. Reduced-motion: scroll stops, first three items shown.
2. **Stagger reveal on testimonials** — IntersectionObserver fires on each card; 100 ms stagger; opacity 0 → 1 + translateY(8px → 0); ease-out 400 ms. One-shot.
3. **Pricing card hover lift** — same recipe as Foundry: `translateY(-3px)` + shadow upgrade, 180 ms ease-out.

CTA hover-lift is the existing `microinteractions.md` recipe and counts as 0 primitives — it's button polish, not page-level motion.

## Macrostructure stamp

```
/* Hallmark · macrostructure: Marquee Hero · H6 hero knobs: speed=slow, content=titles+authors, fade=both-edges
 * theme: Salon · accent: warm-amber ~3% · enrichment: E6 animated loop (continuous marquee, Tier-A)
 * studied: no · context: explicit
 * motion: marquee, stagger-reveal, pricing-lift — three primitives, default-on per archetype
 */
```

## What the page does

1. **Hero (Marquee).** Continuous-scroll band of course titles + instructor names above. Headline below: "Cohort runs live courses with 30 to 500 students." Two CTAs.
2. **Three-step process.** Set a date · Invite students · Teach live. Numbered, conversational.
3. **Features (split, alternating).** Live cohorts · Office hours · Async chat · Cohort analytics. Each row alternates the screenshot side.
4. **Testimonials (4 in 2×2).** Instructor + course name. Specific, voice-distinct.
5. **Pricing (2 tiers).** Indie ($59/mo) · Team ($199/mo). Salon-style: italic-mono display, italic prices, centered.
6. **FAQ (6 questions).** Two-column conversational FAQ.
7. **Final CTA strip.** "Run your first cohort by next month."
8. **Footer.** Centered Salon footer, single-line nav + colophon.

The page is intentionally long — second demonstration of the SaaS page sequence rule, this time in a Marquee Hero shape rather than Stat-Led.
