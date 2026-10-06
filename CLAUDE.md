# noros.life marketing site

Static site for Noros Solutions LLC. Served by GitHub Pages from `main` (custom domain in `CNAME`). There's no build step: what's on `main` is live within a minute or two.

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Homepage: The Overlook Workshop, The Overlook (workshop + course) and Ascent Scholars cards, Summit Advisory, contact |
| `overlook.html` | The Overlook: workshop section (`#workshop`, $197) and course sales page (`#course`, $497 founding, application-gated) |
| `firsttracks.html` | First Tracks sales page ($197, direct Stripe Payment Link; also included with the course) |
| `basecamp.html`, `builders-ridge.html` | Redirects to `overlook.html` (kept so old links work). Don't add content |
| `ascent-scholars.html` | Teen track: The AI Architect (waitlist, no price shown) and Beta |
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

- Naming (Oct 2026): one workshop and one course, together **The Overlook**. The Overlook Workshop $197 (credited toward the course), The Overlook Course $497 founding (formerly Base Camp; includes First Tracks), First Tracks $197 on its own, The AI Architect waitlist only (no price on the site).
- "Base Camp" is reserved for a future student pathway under Ascent Scholars. Don't use it for the adult course, and don't bring back "Builder's Ridge".
- "Beta" means only the study companion. The AI Architect is a "founding cohort".
- No income or earnings figures, and don't promise things that don't exist yet (videos, newsletters).
- The Overlook (adult) and Ascent Scholars (teen) never share a pricing page.

## How to work here

- Pull `main` before editing. Theme work sometimes happens in a parallel session.
- Make changes on a branch and open a pull request. Don't push to `main`; Jami reviews and merges, often from her phone.
- Keep text edits and style edits in separate pull requests.
