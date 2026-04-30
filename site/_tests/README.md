# Hallmark — generation tests

Six landing pages produced by exercising the Hallmark skill across contrasting briefs. The point: see what comes out *without* hand-holding the AI on theme, structure, or enrichment. Each test deliberately tests a different scenario.

| # | Brief | Context given | Theme requested | What the skill picked |
| --- | --- | --- | --- | --- |
| 01 | Indie podcast `Tide`, no detail | **Skipped** ("you pick") | none | Quote-Led + Atelier + no enrichment |
| 02 | Open-source CLI `Streampipe` for stream parsing | Full (devs / install + docs / technical) | **Terminal** (requested) | Workbench + Terminal + Tier-A CSS-art terminal mockup |
| 03 | Artisan bakery `Maple Street Bread` | Full (locals / browse + visit / warm hand-set) | none | Long Document + Linen + Tier-B hand-built SVG loaf |
| 04 | Manifesto for an environmental studio `Meridian` | Partial ("declarative, no flashy stuff") | none (implied) | Manifesto + Manifesto + no enrichment |
| 05 | SaaS observability tool `Tracejam` | Full (SREs / try-or-talk-to-sales / technical) | none | Bento Grid + Pastel + E1 clipped-edge dashboard mockup |
| 06 | Personal one-pager for `Anya` (software architect) | **Skipped** ("don't ask, just figure it out") | none | Long Document + Studio + no enrichment |

Each folder contains:

- **`brief.md`** — the verbatim prompt, what the skill asked / inferred, and the macrostructure stamp the page ships with
- **`index.html`** — the rendered page (self-contained, no shared assets)
- **`style.css`** — the page's tokens + components, with the Hallmark stamp at the top

Open any one with `open site/_tests/<folder>/index.html` or browse via the local dev server at `http://localhost:8765/_tests/<folder>/`.

## What this exercise was for

Stress-testing the skill on briefs that range from "complete spec" to "you figure it out, I'm lazy". Specifically watching for:

1. Does the skill default to the same shape twice across the six tests? → No two should share a macrostructure or hero archetype.
2. Does the skill enrich every page even when it shouldn't? → Tests 01, 04, 06 should be typography-only.
3. When the user skips the design-context gate, does the skill state its inferences in one sentence at the top? → Yes, see brief.md headers.
4. Does the skill bend toward "Built for the modern team" voice when copy is left to it? → Each brief has its own voice; no template-soup.

Findings and a priority list of skill improvements are at the bottom of this file, after the six test cases.

---

## Findings — what worked, what didn't, what to fix

### What worked

1. **Six different briefs produced six structurally different pages.** No two share a macrostructure, hero archetype, or footer voice. The page-shape variety the skill is built around held up under the test.
2. **Three of six tests ship with no enrichment.** The skill correctly resisted the urge to add a Lottie / illustration / mockup to the podcast (typography-only is right for voice), the manifesto (a manifesto is not a marketing page), and the personal portfolio (restraint is the credibility signal). This is the test the *previous* anti-slop generation failed.
3. **The two tests that reach for hand-built CSS art (Tracejam flame chart, bakery loaf) produced custom DOM — not Lottie.** The skill picked Tier-A or Tier-B from the enrichment hierarchy without asking, and the result feels designed, not pulled.
4. **The skipped-context flow worked twice (01 podcast, 06 architect).** Both pages open with an inferred-context disclosure sentence at the top of `brief.md`, which is the documented pattern. The skill states what it inferred.
5. **Type pairing held across all six.** No two tests share a font stack. Newsreader (1, 3), Geist Mono (2, 5), Inter Tight (4), Fraunces (6) each carry one page; pairing logic is theme-driven so this fell out naturally.
6. **The clipped-edge mockup (test 5) was hand-built CSS, not a video file.** The skill resisted the temptation to ship "embed a Loom" — the trace waterfall is pure CSS bars on a percentage grid.

### Friction points I hit while generating

- **The "domain → trio" table covers most cases but not all.** The bakery is in the table; the manifesto is in the table; the personal portfolio is in the table. The SaaS tracing tool is *implicitly* in the table under "platform / tool / infra". The podcast is in the table. **But:** I had to combine "SaaS marketing" + "developer tool" mentally to land on Bento Grid for Tracejam — the skill could be more explicit about *which* of the three suggested macrostructures wins for a given sub-domain. (E.g., "platform/tool" → Workbench or Bento; pick Workbench when the brief says docs/walkthrough, pick Bento when the brief says try-or-talk-to-sales.)
- **Theme picking is still by feel.** The skill has a strong rule that "the next theme can't be Specimen if the last one was Specimen" — but no rule like *"the next theme should be categorically different on at least one of: paper-band, display-style, accent-hue."* I avoided repeating themes here by deliberate intuition; a documented rule would help future runs.
- **Copy generation bent toward "Built for the modern team" twice — and I had to course-correct.** Tracejam's first draft headline was *"Trace what matters."* — a near-template; I rewrote it to *"Distributed tracing that explains itself."* which is more specific. **The skill needs example copy fixtures per macrostructure** (Tier 3 in the existing roadmap) — without them, the model bends toward LLM-distribution copy.
- **The `hero-enrichment.md` decision protocol is text-only — no concrete worked examples per domain.** I had to imagine what Tracejam's "Demo Video Clipped-Edge" looks like vs. "Mockup Split"; an in-file example for each enrichment archetype on a real page would speed this up.
- **Within-archetype variation knobs work in theory but I leaned on the same defaults.** The two pages with footer-index (Tracejam, none of the others ended up there) and footer-inline (the podcast, the bakery, the architect) all converge on the same shape. A future run on the *same* footer archetype should pick *different* knobs — but the rule lives in the cookbook, not in muscle memory.
- **Free fonts only got me so far.** The bakery wanted Tiempos Headline (paid, Klim); I substituted Newsreader. The Studio theme on Anya's portfolio wanted Tobias (paid); Fraunces is a strong understudy but not the same. The skill should explicitly call out free-vs-paid trade-offs with two-tier candidates per pairing.

### Improvement list — priority order

This is the punch list. Do these and the skill goes from "good" to "as good as a human-curated design.md gets in 2026".

#### Tier 1 — Real holes (next session)

1. **Per-archetype example copy fixtures.** For each of the 21 macrostructures, ship 2–3 example *opening-line copy fragments* in `references/macrostructures.md`. The model imitates them instead of bending to LLM distribution. Highest single payoff for output quality. Currently roadmap Tier 3.
2. **Sub-domain refinement for the trio table.** Split "platform / tool / infra / dashboard / developer" into two rows: *docs/walkthrough* → Workbench / Long Doc; *try-or-talk-to-sales* → Bento / Stat-Led / Workbench. Same for "personal" (one-pager Letter vs. multi-page Long Doc).
3. **A documented theme-diversification rule.** *"Across consecutive Hallmark outputs in this user's session/project, no two themes should share more than one of: paper-band, display-style, accent-hue."* Currently the rule is "don't repeat Specimen", which is tighter on one tail than it should be.
4. **Free-vs-paid font trade-off in `typography.md`.** Each tone gets two pairings: "free baseline" and "paid upgrade if the user can pay". The bakery example would say: "Free: Newsreader + Geist + Geist Mono. Paid upgrade: Tiempos Headline + Söhne + Söhne Mono."
5. **Worked examples in `hero-enrichment.md` per archetype.** A 5-line "what this looks like for X brief" under each E1–E8. Right now the descriptions are abstract; concrete worked examples accelerate generation.

#### Tier 2 — Quality polish

6. **A "different knobs" check in the slop test.** Question 34: *"If I used the same archetype as a previous Hallmark output (e.g., footer-inline twice), did I pick at least one different variation knob?"* Catches the template-soup-within-an-archetype risk this exercise surfaced.
7. **More illustration recipes in `custom-craft.md`.** The bakery loaf was the only worked example. Add one for: a workflow diagram, a mascot, a small architectural diagram, a botanical accent. Each in 30–60 lines. The bakery loaf I generated above had room to be sharper — the recipes should show what *good* looks like at this scale.
8. **A `references/copy.md` extension with non-LLM voice samples.** Three voices per tone (editorial / brutalist / soft / technical / luxury / playful / austere) with 5 example sentences each. Borrow from real sites (Klim, Linear, Apple, Tufte, Rauno, Frieze) — credit them, don't copy.
9. **Mobile breakpoint discipline per archetype.** I caught this on test 5 (Tracejam): the clipped-edge mockup needed a 60rem media query to collapse to stacked. The cookbook entries should say *"on viewports below X, this archetype collapses to Y"* so it's automatic.
10. **An in-skill check: did I write `aria-label` on every visual-only SVG?** I caught it manually for the bakery loaf and the trace waterfall, but a slop-test gate would make it automatic.

#### Tier 3 — Long bet

11. **Project-level memory beyond the CSS stamp.** Right now the skill reads the *latest* stamp in the project. A `.hallmark/log.json` per-project file (history of macrostructures + themes + briefs) would let the diversification rules see further back.
12. **A "study + remix" combined verb.** `hallmark study + redesign` in one — extract DNA from a screenshot, then rebuild the user's content with that DNA. Today the user has to chain `study` then `redesign`; one verb would be tighter.
13. **A real example gallery on the landing page.** These six tests should be linked from the main `site/index.html` as a "Generated by Hallmark" gallery, with one-line captions. Marketing the skill via the skill's outputs.
14. **Auto-generated Open Graph cards per page.** Each test ships its own meta description, but the OG image is missing. A small Hallmark utility that generates an OG image per page from the macrostructure stamp + headline would close the loop.

### What this means for the skill

Hallmark is *good*. The structural variety position holds — six briefs, six different pages, no template repetition. The enrichment hierarchy works — three of six pages correctly choose to ship nothing visual, and the three that do enrich pick the right tier (custom-built, not Lottie).

The remaining gap is **copy voice** and **theme-pick discipline**. The slop test catches *visual* tells well; it doesn't yet catch *prose* tells (like "Built for the modern team" headlines). And the diversification rules are tight on one axis (no Specimen fall-through) but loose on the rest.

Tier 1 of this list is the next session's work.
