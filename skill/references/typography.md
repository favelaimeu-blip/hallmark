# Typography

Type carries the design. If the type is wrong, nothing else matters.

## Principles

- A page is a pairing, not a single font. Display face + body face, minimum. *Single-font pages are allowed only when the single font IS the design choice* — a true terminal aesthetic is monospace-everywhere on purpose; a Manifesto poster might be one display face on purpose. The default is a pairing.
- Commit to extremes. Weight 200 next to weight 800 reads as intentional. Weight 400 next to weight 600 reads as a default setting.
- Size steps should be ratios, not increments. Major third (1.25), perfect fourth (1.333), perfect fifth (1.5), or golden (1.618). Pick one and use it.
- Line-height changes with size. Tight for display (1.05–1.2), comfortable for body (1.5–1.65).
- Measure — line length — lives between 45 and 75 characters. Use `max-width: 65ch` as the default.

## Banned defaults

These fonts are on-distribution for every LLM. Do not reach for them without a deliberate reason:

- **Sans-serif:** Inter, Roboto, Open Sans, Lato, Poppins, Source Sans, Nunito, Montserrat, Raleway, Work Sans, DM Sans, system-ui, Arial, Helvetica.
- **Serif:** Merriweather, Playfair Display (as body — banned as overused body serif; ok as display in moderation), Lora, Source Serif, Georgia-as-default.
- **Mono:** Courier New, Consolas-as-default, system mono.

If the user insists on one, do it. Otherwise pick from the allowlist below.

## Pairing patterns that work

Each tone gets two rows: a **free baseline** (everything Google-Fonts-or-similar; works out of the box) and a **paid upgrade** (foundry licences required; only when the user has confirmed the budget and the licence). The free row is the default. **Never name a paid font in code without confirming the user is licensed** — the demo will fall back to system-default and look broken to the user.

| Tone | Tier | Display | Body | Mono |
| --- | --- | --- | --- | --- |
| **Editorial** | Free | Fraunces · Newsreader · EB Garamond | IBM Plex Sans · Inter Tight | JetBrains Mono · Geist Mono |
| | *Paid* | *Tiempos Headline · Söhne Breit · Reckless Display* | *Söhne · Haffer · Untitled Sans* | *Söhne Mono · GT America Mono* |
| **Technical** | Free | JetBrains Mono · Geist Mono · Geist (700) | Geist · IBM Plex Sans | Geist Mono · JetBrains Mono |
| | *Paid* | *Berkeley Mono · Söhne Mono · GT Pressura* | *Söhne · Untitled Sans* | *Berkeley Mono · GT Pressura Mono* |
| **Brutalist** | Free | Inter Tight (heavy) · Anton · Bricolage Grotesque (800) | Inter · Geist | Geist Mono |
| | *Paid* | *Druk · Monument Extended · NaN Jaune · Migra* | *Söhne Breit · GT America* | *GT America Mono* |
| **Soft** | Free | Geist · Bricolage Grotesque (500) · Newsreader | Geist · Crimson Pro | Geist Mono |
| | *Paid* | *Söhne · GT Pressura · Pangaia* | *Söhne · Halyard Text* | *Söhne Mono* |
| **Luxury** | Free | Cormorant Garamond · Fraunces · Cardo | EB Garamond · Crimson Pro | (rare; if needed: JetBrains Mono) |
| | *Paid* | *Canela · Tiempos Headline · GT Super · Domaine Display* | *Tiempos Text · Suisse Int'l · Domaine Text* | *(rarely used at this tier)* |
| **Playful** | Free | Bricolage Grotesque · Fraunces (italic) · Newsreader (italic) | Geist · Newsreader | Geist Mono |
| | *Paid* | *Clash Display · Cabinet Grotesk · Migra · Tobias* | *Satoshi · Plus Jakarta Sans · GT Maru* | *Space Mono · GT Maru Mono* |
| **Austere** | Free | system-ui · Inter Tight (regular) · Geist (400) | system-ui · Geist | system-ui · Geist Mono |
| | *Paid* | *ABC Diatype · ABC Monument Grotesk · Söhne (regular) · ABC Pressura* | *ABC Diatype · Söhne* | *ABC Diatype Mono · Söhne Mono* |
| **Workshop** *(Hallmark's own theme)* | Free | The Future · Geist · Inter Tight | The Future · Söhne | The Future Mono · Geist Mono |
| | *Paid* | *Avenir Next · GT Walsheim* | *Söhne · GT Walsheim* | *Berkeley Mono* |

**The discipline.** Default to the free pairings. They're not consolation prizes; Fraunces, Geist, Bricolage Grotesque, and JetBrains Mono are first-rate faces in 2026. The paid upgrades exist for two cases: (a) the user has explicitly confirmed they're licensed, or (b) the user is asking for a specific named foundry voice (e.g., "make it look like Klim", "I want Söhne"). Reach for Tier 2 only then; otherwise the free row is the right answer. Treat the free row as canon, the paid row as a *cited* alternative.

## Wordmark / logo typography

The wordmark in the navbar and footer **may use a different display face than the body**. On tone-rich themes (Editorial, Salon, Atelier, Linen, Quiet) it **should** — collapsing the wordmark into the body family flattens the visual hierarchy and the page reads as un-branded.

```css
:root {
  --display:       "Geist", system-ui, sans-serif;     /* body + display */
  --font-wordmark: "Fraunces", Georgia, serif;         /* logo only */
}
.wordmark {
  font-family: var(--font-wordmark);
  font-weight: 600;
  letter-spacing: -0.015em;
}
```

Recommended pairings (free baseline first):

- **Geist body → Fraunces wordmark, IBM Plex Mono wordmark, or Bricolage Grotesque (heavy) wordmark**
- **Fraunces body → Geist Mono wordmark, Inter Tight wordmark**
- **System-ui body → JetBrains Mono wordmark, Newsreader wordmark**
- **Inter Tight body → Fraunces wordmark, EB Garamond wordmark**

When to use the same family for both:

- **Editorial · Letter · Manifesto · Long Document** can collapse to a single family because the body voice carries the brand. The wordmark in these contexts is small, grounded, and earns its weight by being typeset rather than decorated.

When to use a contrasting family:

- **Bento Grid · Stat-Led · Workbench · Marquee Hero** — these archetypes lean visually generic (geometric grids, big numbers, browser-frame mockups) and need the wordmark to do the typographic differentiation work the body can't.

**Avoid the same-family collapse on a SaaS page.** A Geist-only page where the wordmark is also Geist 600 reads as un-designed; the wordmark in Fraunces SemiBold over a Geist body costs nothing and adds the one typographic register that says *this is a brand*.

## Scale

Pick a ratio. The default for Hallmark work is **1.25** (major third). Build the scale from a 16px body, then clamp display sizes for responsive.

```css
:root {
  --text-xs:   0.64rem;   /* 10.24px */
  --text-sm:   0.8rem;    /* 12.8px  */
  --text-base: 1rem;      /* 16px    */
  --text-md:   1.25rem;   /* 20px    */
  --text-lg:   1.5625rem; /* 25px    */
  --text-xl:   1.9531rem; /* 31.25px */
  --text-2xl:  2.4414rem;
  --text-3xl:  3.0518rem;
  --text-4xl:  3.8147rem;
  --text-display: clamp(3rem, 8vw + 1rem, 8rem);
}
```

Use no more than five sizes on a single page. If you need more hierarchy, use weight and colour, not another size.

## Weights

- Body: one weight (typically 400 or 350). Bold for emphasis only.
- Headings: a weight that contrasts the body by at least 300 units. If body is 400, headings are 700 or 200 — not 500 or 600.
- Never synthesise. Load the weight you need; don't rely on `font-weight: bold` against a single-weight file.

## Required features

- `font-display: swap` on every web font.
- Match fallback metrics with `size-adjust`, `ascent-override`, `descent-override`, `line-gap-override` to prevent CLS.
- Tabular numbers on any data display: `font-variant-numeric: tabular-nums;`.
- Oldstyle figures for body copy where the face supports them: `font-variant-numeric: oldstyle-nums;`.
- Proper typographic punctuation: `" " — … ‘ ’`. Never straight quotes, never `--` or `...`.

## Body text rules

- Minimum 16px. Below 14px is accessibility-hostile.
- Line-height 1.5–1.65 on body copy, tighter (1.1–1.3) on display.
- Measure 45–75 characters (`max-width: 65ch`).
- Never all-caps body copy. Never justified text without hyphenation. Never letter-spacing above 0.05em on body.

## Headings rules

- Tight tracking on display sizes (`letter-spacing: -0.02em` to `-0.04em` depending on the face).
- Loose tracking on small caps / labels (`letter-spacing: 0.08em` to `0.14em`, `text-transform: uppercase`, use small caps if the face has them: `font-variant-caps: all-small-caps;`).
- Skip no levels. `h1` → `h2` → `h3`. Style them visually how you like, but keep semantic order.

## Bans

- No Inter, no Roboto, no Open Sans. No system stack as the *only* stack.
- No gradient text on headings (`background-clip: text` with a gradient fill).
- No single-font pages.
- No all-caps paragraphs.
- No font-size below 14px for body copy, below 10px anywhere.
- No hard-synthesised bold or italic.
