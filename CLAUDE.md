# noros.life marketing site

Static site for Noros Solutions LLC. Served by GitHub Pages from `main` (custom domain in `CNAME`). There's no build step: what's on `main` is live within a minute or two.

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Homepage: workshop section, Builder's Ridge row (Overlook Workshop, Overlook Course, Summit Advisory), Ascent Scholars row (Base Camp placeholder), contact |
| `overlook.html` | The Overlook: workshop section (`#workshop`, $197) and course sales page (`#course`, $497 founding, application-gated) |
| `firsttracks.html` | First Tracks sales page ($197, direct Stripe Payment Link; also included with the course) |
| `builders-ridge.html` | Professional pathway hub: Overlook Workshop, Overlook Course, Summit Advisory, plus a First Tracks line. Room for future offerings |
| `basecamp.html` | Redirect to `overlook.html#course` (the adult course's old page). Don't add content; the student Base Camp lives on `ascent-scholars.html` |
| `ascent-scholars.html` | Student pathway: Base Camp placeholder (workshop + career-prep course, waitlist by email). Beta and The AI Architect sections are `hidden`, not deleted |
| `summit-advisory.html` | Consulting page |
| `beta.html` | Beta study companion. Separate, self-contained, doesn't use `tokens.css` |
| `tokens.css` | All colors and theme tokens, shared by the six main pages and the course portal |

## Theme rules

- Colors live only in `tokens.css`. Pages use semantic tokens (`--bg`, `--surface`, `--text-primary`, `--accent`, `--pop-fill`, …), never raw hex and never the palette layer.
- Every main page sets `<html data-theme="light">`: the oatmeal background with Periwinkle + Chartreuse.
- The course portal (repo `noros-courses`) loads `https://noros.life/tokens.css`, so a change here changes the portal too.
- Fonts: Syne (headings, labels), DM Mono, Cormorant Garamond (body). None has arrow, check or mountain glyphs. Use the inline SVG icons (`<svg class="i"><use href="#i-arrow-r"/></svg>` and similar) instead of typed symbols.

## Forms

| Form | Page | Goes to |
| --- | --- | --- |
| Overlook Course application | `overlook.html` | Noros intake app on Cloud Run, `POST /api/apply` (Sheet "Applications" tab + emails) |
| Summit Advisory lead | `summit-advisory.html` | Same intake app, `POST /api/lead` |
| Contact, workshop interest | `index.html` | Formspree `xpqnlwja` |

The intake app lives in a separate folder (`~/summit-intake-app`, deployed with `gcloud run deploy`). A new form there needs a backend route deployed before the page change is merged.

## Content rules

- Two pathways (Oct 2026). **Builder's Ridge** (professionals): The Overlook Workshop $197 (credited toward the course), The Overlook Course $497 founding (formerly Base Camp; includes First Tracks), First Tracks $197 on its own, Summit Advisory by scope. **Ascent Scholars** (students): Base Camp, a workshop and career-prep course, coming soon, waitlist only, no price.
- "Base Camp" now means only the student offering. Never use it for the adult course.
- "Beta" means only the study companion. The AI Architect is a "founding cohort". Both are hidden for now; don't link them.
- No income or earnings figures, and don't promise things that don't exist yet (videos, newsletters).
- Builder's Ridge (adult) and Ascent Scholars (students) never share a pricing page.

## How to work here

- Pull `main` before editing. Theme work sometimes happens in a parallel session.
- Make changes on a branch and open a pull request. Don't push to `main`; Jami reviews and merges, often from her phone.
- Keep text edits and style edits in separate pull requests.
