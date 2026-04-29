# Hallmark

A design skill for AI coding assistants. Makes the UIs they generate look made, not generated.

**Powered by Together AI.**

---

## What it is

A single, opinionated skill — short on purpose — that teaches Claude Code, Cursor, or Codex a firm, consensus-backed set of rules for typography, colour, layout, motion, interaction, microinteractions, copy, responsive behaviour, and structural variety. It refuses to design without a confirmed audience, use case, and tone, and refuses to emit the on-distribution defaults every LLM was trained into.

The differentiator: Hallmark insists on **structural variety**, not just visual variety. Two pages by Hallmark for two different briefs should not share the same hero → 3-feature → CTA → footer rhythm.

---

## Five verbs

| Verb | What it does |
| --- | --- |
| *(default)* | Build new UI — runs the design-context gate (askable, skippable; the skill states what it inferred either way), picks a structural fingerprint, applies the ruleset, runs the slop test before handing back. |
| `hallmark audit <target>` | Score existing code against the named anti-patterns + structural sameness. Returns a punch list. No edits. |
| `hallmark refine <target>` | Polish in place. Smallest possible diff. Preserves structure. |
| `hallmark redesign <target> [--mood <name>]` | Throw out the structure, keep copy + IA + brand, rebuild with a deliberately different structural fingerprint. |
| `hallmark study <screenshot>` | The user attached a design they admire. Extract the **DNA** — macrostructure, archetypes, type-pairing role, colour anchor — and produce a diagnosis report. Then optionally rebuild *the user's* content using the extracted DNA. **Refuses paid templates and competitor pages. Names font roles, never font IDs. Never copies pixels.** |

---

## What's inside

**Skill** — [`skill/SKILL.md`](skill/SKILL.md) plus ten reference files:

- [`typography.md`](skill/references/typography.md) — banned defaults, pairing rules, weight extremes, scale ratios
- [`color.md`](skill/references/color.md) — OKLCH palette construction, accent discipline (≤3% area), dark-mode recipe
- [`layout-and-space.md`](skill/references/layout-and-space.md) — 4pt scale, asymmetry, grid-breaks, depth via weight not shadow
- [`structure.md`](skill/references/structure.md) — six axes of structural variety (heading placement, body composition, divider, button voice, image, reveal); the per-theme structural fingerprint table
- [`motion.md`](skill/references/motion.md) — duration buckets, three named easings, no bounce on UI, reduced-motion default
- [`microinteractions.md`](skill/references/microinteractions.md) — 14 interaction recipes (button press, focus, modal, toast, optimistic update, command palette, drag, copy-to-clipboard, search-as-you-type) and the 20 named microinteraction tells
- [`interaction-and-states.md`](skill/references/interaction-and-states.md) — eight states per element, focus-visible spec, 44px hit targets, undo over confirm
- [`responsive.md`](skill/references/responsive.md) — mobile-first, content-driven breakpoints, `dvh` not `vh`, safe-area-insets
- [`copy.md`](skill/references/copy.md) — specific verbs, three-part errors, standalone link text, proper typographic punctuation
- [`anti-patterns.md`](skill/references/anti-patterns.md) — 30+ named tells with severity, why they fail, and the fix
- [`macrostructures.md`](skill/references/macrostructures.md) — the 21 named whole-page shapes; pick one before writing code, stamp it in the CSS comment
- [`component-cookbook.md`](skill/references/component-cookbook.md) — 33 component archetypes across 7 categories, each with 2–3 within-archetype variation knobs
- [`study.md`](skill/references/study.md) — vision-extraction protocol for the `hallmark study` verb: refusal heuristics, the structured-fields schema, type-role vocabulary, theme mapping table, worked example, limits

**Slop test (29 questions)** — every output must answer *no* to all twenty-nine before shipping. Visual (8), structural (2), microinteraction (10), variety (3), implementation gates (6).

**Site** — [`site/`](site/) is a self-demonstrating landing page. Hand-written HTML + CSS + ES module, no framework, no build step. Uses Together AI's "The Future" typeface plus Google Fonts.

**Twelve themes**, four categories, each with its own structural fingerprint:

- **Editorial** — Specimen, Newsprint, Atelier
- **Soft** — Garden, Salon, Linen
- **Technical** — Midnight, Terminal, Almanac
- **Bold** — Brutal, Manifesto, Sport

Each theme overrides not only colour and typography but section-heading placement, column counts, divider style, button voice, and reveal pattern. The same landing page reorganises itself per theme, demonstrating the structural-variety principle.

**Two test specimens** — [`site/_example-bakery/`](site/_example-bakery/) (an editorial bakery announcement, output of a real `hallmark` run) and [`site/_example-cmdk/`](site/_example-cmdk/) (a keyboard-first command palette demonstrating the microinteraction canon).

**Roadmap** — [`ROADMAP.md`](ROADMAP.md) lists Tier 1, 2, and 3 work, plus an explicit "things to *not* do" list and measurement criteria.

---

## Install

### Any harness, via npx

```
npx skills add hallmark
```

### Claude Code (manual)

Copy [`skill/SKILL.md`](skill/SKILL.md) and [`skill/references/`](skill/references/) into `~/.claude/skills/hallmark/`.

### Cursor

Create `.cursor/rules/hallmark.mdc` with the body of `SKILL.md` (no frontmatter).

### View the landing page locally

```
cd site && python3 -m http.server 4173
# → http://localhost:4173
```

---

## Philosophy

Five skills — [impeccable](https://github.com/pbakaus/impeccable), [kami](https://github.com/tw93/kami), [taste-skill](https://github.com/Leonxlnx/taste-skill), Anthropic's [frontend-design skill](https://github.com/anthropics/skills), and the Claude [frontend aesthetics cookbook](https://platform.claude.com/cookbook/coding-prompting-for-frontend-aesthetics) — have converged on roughly the same anti-slop ruleset. Hallmark takes that consensus, restates it in one voice, fills the gap on motion and microinteractions, and adds *structural* variety as a first-class principle.

Distinct choices:

- **One skill, five verbs.** Not eighteen commands. Use the default; reach for `audit`, `refine`, `redesign`, or `study` when you need them.
- **Design-context gate.** No audience + use case + tone → no design. The skill asks.
- **Tone as a first-class decision.** "Clean and modern" is rejected. Pick an extreme: editorial, brutalist, soft, utilitarian, luxury, playful, technical, austere.
- **Structural fingerprint.** Every page picks one option from each of six axes. Two consecutive outputs in a session should never share the same fingerprint.
- **Microinteractions are not decoration.** Silent success over celebratory toasts. Optimistic update + Undo over confirm dialogs. Hover delay 800 ms, focus delay 0 ms.
- **The slop test.** Twenty yes/no checks before handing back. One yes fails the output.

---

## Credits

Built on the open work of Paul Bakaus ([impeccable](https://github.com/pbakaus/impeccable)), tw93 ([kami](https://github.com/tw93/kami)), Leonxlnx ([taste-skill](https://github.com/Leonxlnx/taste-skill)), Anthropic's skills team ([frontend-design](https://github.com/anthropics/skills) and [canvas-design](https://github.com/anthropics/skills)), [DESIGN.md](https://getdesign.md) (Google Stitch), MC Dean's [63 design skills](https://marieclairedean.substack.com/p/i-built-63-design-skills-for-claude), [PencilPlaybook](https://github.com/stevembarclay/pencilplaybook), and the [Slopless](https://slopless.design) tactile-rebellion canon. Where rules overlapped, Hallmark adopted; where they diverged, Hallmark picked.

---

## Licence

MIT. Use it, fork it, ship it.
