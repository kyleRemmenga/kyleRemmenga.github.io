# Handoff: Kyle Remmenga — personal site (GitHub Pages)

## Overview

A five-page personal site for Kyle Remmenga, to be deployed at `kyleRemmenga.github.io`. It is a personal home page, not a portfolio pitch: a short intro, work history, projects, an about page, and contact details. Tone is plain and understated — no marketing language, no calls to action.

Target repo: **`kyleRemmenga/kyleRemmenga.github.io`**, branch `main`. That repo currently contains only the course starter (`index.html` with "Hello, world" and a minimal `style.css`). Both should be replaced.

## About the design files

`Kyle Remmenga.dc.html` (with `support.js` beside it) is a **design reference created in HTML** — a prototype showing the intended look, content, and behavior. It is not production code to copy directly. It renders through a component runtime and uses a JS-driven page switcher; neither belongs in the final site.

**The task:** recreate this design as a plain static multi-page site suitable for GitHub Pages — hand-written HTML and one CSS file, no build step, no framework, no bundler. GitHub Pages serves the repo root directly, so the output should be static files at the root.

Open the bundled `Kyle Remmenga.dc.html` in a browser to see the reference rendering, and read its source for the exact copy. **All body copy is final and should be transcribed verbatim** — it was written and revised with the site's owner. Do not rewrite, expand, or "improve" it.

## Fidelity

**High fidelity.** Colors, typography, spacing, and layout are final. Recreate them faithfully. All color values are `oklch()` — keep them as `oklch()` in the CSS rather than converting to hex; the design was tuned in that space.

## Target file structure

```
index.html      Home
work.html       Work
projects.html   Projects
about.html      About
contact.html    Contact
style.css       Shared stylesheet
```

Every page shares the same shell (left rail + content column). In the prototype the pages are `<sc-if>` branches switched by JS; in the real site each becomes its own HTML file, with the rail nav as ordinary `<a href>` links. Mark the current page's link with `aria-current="page"` and style it with the accent color.

## Layout

Two-column shell, full viewport height, `display: flex` (must **not** wrap — a `flex-wrap: wrap` here was a bug that broke the layout).

**Left rail** — `flex: 0 1 300px; min-width: 232px`, `position: sticky; top: 0; height: 100vh`, `border-right: 1px solid oklch(0.28 0.010 152)`, `padding: 56px 36px 40px`, `display: flex; flex-direction: column; gap: 40px`. Contents top to bottom:

1. Name block: "Kyle" / "Remmenga" on two lines, JetBrains Mono 700, 19px, `letter-spacing: -0.02em`, `line-height: 1.25`. Below it "AI Engineer" — JetBrains Mono 11px, `letter-spacing: 0.10em`, uppercase, accent color. The two sit in a flex column with `gap: 10px`.
2. Nav — flex column, `gap: 2px`, `margin-top: -8px`. Links are JetBrains Mono 14px, `letter-spacing: -0.01em`, `padding: 7px 0`, `transition: color .22s ease`. Inactive `oklch(0.62 0.010 152)`, hover `oklch(0.93 0.006 152)`, current page accent. Order: Home, Work, Projects, About, Contact.
3. Contact block pinned to the bottom with `margin-top: auto` — flex column `gap: 14px`. An inner flex column `gap: 6px` of three links (email, GitHub, LinkedIn) at 15px Newsreader, `line-height: 1.5`, then "Littleton, Colorado" in JetBrains Mono 10px, `letter-spacing: 0.08em`, uppercase, `oklch(0.52 0.010 152)`.

**Content column** — `flex: 1 1 360px; min-width: 0`, horizontal padding `clamp(32px, 7vw, 110px)`. Inside it a `max-width: 720px` block with padding `clamp(56px, 9vh, 120px) 0 120px`.

**Responsive** — one breakpoint at `max-width: 860px`: the shell becomes `flex-direction: column`; the rail becomes static (`height: auto`, no right border, a `1px solid oklch(0.28 0.010 152)` bottom border instead, `padding: 34px 28px 26px`, `gap: 26px`); the nav becomes a horizontal wrapping row (`gap: 4px 22px`) and the bottom contact block loses its `margin-top: auto`.

## Design tokens

**Colors** (all `oklch`, hue 152 throughout — a desaturated green)

| Role | Value |
| --- | --- |
| Page background | `oklch(0.185 0.008 152)` |
| Heading / high-emphasis text | `oklch(0.93 0.006 152)` |
| Body text | `oklch(0.86 0.006 152)` |
| Secondary body text | `oklch(0.80 0.006 152)` / `oklch(0.78 0.008 152)` |
| Tertiary / intro paragraphs | `oklch(0.72 0.008 152)` |
| Labels, dates, meta | `oklch(0.58 0.010 152)` |
| Skill-group labels | `oklch(0.62 0.010 152)` |
| Faintest meta (rail location, date ranges on Home) | `oklch(0.52–0.55 0.010 152)` |
| Rules and dividers | `oklch(0.28 0.010 152)` (secondary `oklch(0.26 0.010 152)`) |
| Bullet left rules / chip borders | `oklch(0.30 0.010 152)` / `oklch(0.31 0.012 152)` |
| **Accent** | `oklch(0.74 0.10 152)` |
| Accent hover | `oklch(0.86 0.09 152)` |

Expose the accent as `--accent` on `:root`. Selection: `background: color-mix(in oklch, var(--accent) 30%, transparent)`.

**Typography**

- Headline / UI / meta: **JetBrains Mono** 400, 500, 700
- Body: **Newsreader** 300, 400, 500 + italic
- Google Fonts link:
  `https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Newsreader:ital,opsz,wght@0,6..72,300;0,6..72,400;0,6..72,500;1,6..72,400&display=swap`
- Body default: Newsreader, `-webkit-font-smoothing: antialiased`

| Element | Spec |
| --- | --- |
| Home h1 | JetBrains Mono 500, `clamp(30px, 3.4vw, 48px)`, `line-height: 1.14`, `letter-spacing: -0.035em`, `text-wrap: balance` |
| Section h1 (Work/Projects/About/Contact) | JetBrains Mono 500, `clamp(30px, 4vw, 42px)`, `line-height: 1.15`, `letter-spacing: -0.03em` |
| Lead paragraphs | Newsreader 21px, `line-height: 1.62`, `text-wrap: pretty` |
| Section intro under h1 | Newsreader 20px, `line-height: 1.6`, `max-width: 60ch` |
| Job / project h2 | JetBrains Mono 500, 20–21px, `letter-spacing: -0.02em` |
| Employer line | Newsreader 17px italic, accent color |
| Date ranges | JetBrains Mono 12px, `letter-spacing: 0.06em`, uppercase |
| Bullet body | Newsreader 19px, `line-height: 1.58` |
| Bullet lead-in (bold label) | JetBrains Mono 500, 14px, `display: block`, `margin-bottom: 4px`, `oklch(0.93 0.006 152)` |
| Eyebrow labels ("Where I am now", "Education", "Technical Skills") | JetBrains Mono 11px, `letter-spacing: 0.14em`, uppercase, `oklch(0.58 0.010 152)` |
| Skill chips | JetBrains Mono 13px, `padding: 5px 11px`, `border: 1px solid oklch(0.31 0.012 152)`, `border-radius: 2px` |

Prose blocks cap at `60–62ch`. Border radius is effectively zero everywhere except the 2px skill chips. No shadows, no gradients, no rounded cards.

**Links** — accent color, `border-bottom: 1px solid color-mix(in oklch, var(--accent) 35%, transparent)`, no `text-decoration`; on hover both color and border become `oklch(0.86 0.09 152)`. Transition `border-color .25s ease, color .25s ease`.

## Screens

Copy for every screen is in the bundled HTML — transcribe it exactly. Structure per page:

**index.html — Home.** H1 "Kyle Remmenga", two intro paragraphs, then an eyebrow "Where I am now" and a three-row table-like list (AI Engineer Intern / Class VI Partners; AI Engineer / Mines, Petroleum Engineering; M.S. Computer Science / Colorado School of Mines, 2025 — 2026). Each row: `display: flex; flex-wrap: wrap; gap: 4px 20px; align-items: baseline; padding: 18px 0`, bottom rule; three cells — role (JetBrains Mono 15px, `flex: 1 1 240px`), organization (Newsreader 17px, `flex: 1 1 180px`, `oklch(0.70 0.008 152)`), year (JetBrains Mono 12px). The list has a top rule on the container.

**work.html — Work.** Five `<article>` entries in a flex column, `gap: 56px`. Each: a header row (h2 left, date range right, `justify-content: space-between`, 14px bottom padding, bottom rule), the italic employer/location line, then an unstyled `<ul>` (`list-style: none`) of bullets with `gap: 16px`, each bullet `padding-left: 20px; border-left: 1px solid oklch(0.30 0.010 152)` and a JetBrains Mono lead-in label above its sentence. Entries in order: AI Engineer Intern (Class VI Partners), AI Engineer (Mines, Department of Petroleum Engineering), Graduate Assistant (Mines, Department of Petroleum Engineering), Machine Learning Researcher (Colorado Mesa), Cyber Security Researcher (Colorado Mesa).

The Class VI Partners entry carries one extra line under its italic employer line: "Subcontracted through Analytical Data Systems, May — August 2026" — JetBrains Mono 12px, `letter-spacing: 0.04em`, `oklch(0.58 0.010 152)`, `margin-top: -6px`. Both Mines entries name the Department of Petroleum Engineering in their italic employer line.

**projects.html — Projects.** Four numbered rows, each `padding: 30px 0` with a top rule (last also bottom rule). Row is a flex with a 44px number cell (JetBrains Mono 12px, accent, `padding-top: 6px`) and a `flex: 1 1 380px` body. Order: 01 Stars Without Number character generator (has a repo link at JetBrains Mono 13px), 02 GPT from scratch, 03 Live parking availability, 04 Subset checksum. Below the list, 72px down, the "Technical Skills" eyebrow and four skill groups (Languages, ML / AI, Infrastructure, Tools) — each a flex row with a 130px label cell and a wrapping chip row, groups separated by `gap: 26px`.

**about.html — About.** H1, three paragraphs, then the "Education" eyebrow and two entries (M.S. Mines, B.S. Colorado Mesa) in a flex column `gap: 34px`; each has a top rule, a header row (h2 / date range), the italic school line, and one descriptive sentence. The M.S. reads AUG 2025 — DEC 2026 and its sentence opens "Expected December 2026."; the B.S. reads 2022 — 2025.

**contact.html — Contact.** H1, one line of intro, then a definition-style list of rows (`padding: 22px 0`, top rules, bottom rule on the last): Email, GitHub, LinkedIn, Located. Each row has a 120px JetBrains Mono 11px uppercase label (`letter-spacing: 0.12em`) and a 20px value.

**Phone number:** deliberately omitted. The prototype has it behind a flag that is off. Do not add it — the repo is public.

## Interactions & behavior

Minimal by design.

- Page entry animation: the content block runs `riseIn .5s cubic-bezier(.2,.7,.3,1) both` — `opacity: 0; translateY(10px)` to `opacity: 1; translateY(0)`. On a static multi-page site apply this to the content column on load.
- Nav and link hovers are the color transitions described above. No other motion.
- External links (GitHub, LinkedIn, project repo) use `target="_blank" rel="noopener"`. Email is `mailto:`.
- No JavaScript is required for the final site. If you add any, it should be a progressive enhancement only.

## State management

None. Static pages.

## Assets

No images. Fonts come from Google Fonts via `<link>` with `preconnect` to `fonts.googleapis.com` and `fonts.gstatic.com` (crossorigin). No icons, no logos.

## Content sources

- Work history, education, and projects 02–04 come from Kyle's resume (already transcribed into the prototype verbatim), reconciled against his LinkedIn profile with him directly. Where the two sources disagreed, the prototype holds the settled version — use it, not the resume PDF.
- Project 01 is summarized from `github.com/kyleRemmenga/swn_character_generator`.
- Intro and about copy was written and revised in the design process; treat it as final.

## Deployment

Commit the static files to the root of `kyleRemmenga/kyleRemmenga.github.io` on `main`. GitHub Pages serves a user site from the root of that repo automatically — no workflow file, no Jekyll config needed. A `.nojekyll` file at the root is harmless and avoids Jekyll surprises.

## Files in this bundle

- `Kyle Remmenga.dc.html` — the design reference. Open in a browser to view; read the source for exact copy.
- `support.js` — runtime the reference needs to render. Not part of the deliverable.
