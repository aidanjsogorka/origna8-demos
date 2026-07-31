# origna8-demos

Interactive UI demos and design renditions for Origna8.

Live site: https://aidanjsogorka.github.io/origna8-demos/

## Educa8 redesign, 30 Jul 2026

The Educa8 learning section, rebuilt. Nine self-contained HTML pages, no build step, no backend.

Start at `educa8/index.html`, the hub.

| Page | What it is |
|---|---|
| `educa8/andrew-authoring.html` | The course studio. Andrew writes lessons here, in plain English. |
| `educa8/learner-a-competitive.html` | The reading view, argued as competition: streak, branch leaderboard, XP, season track. |
| `educa8/learner-b-mastery.html` | The reading view, argued as relevance and mastery: no streak, no board, no points. Ordered by the officer's open pipeline, with evidence drawn from their own closed files. |
| `educa8/learner-c-mastery-edited.html` | B after a density pass. Same argument and same content, but the thesis moved up, the recall table became an instrument, and the header lost a figure. Replaces B if it reads better. |
| `educa8/v1` … `v5` | The five design directions the aesthetic was chosen from. v5, the ledger, won. |

**A and B are the open question. C is B, edited.** Same content, same app shell, opposite theory of why a loan
officer in their twenties would open the section at all. Both keep spaced retrieval. They differ
on everything else.

## The plumbing switch

Every page has one, in the header or in the demo bar at the bottom. Off, the page reads in
ordinary English. On:

- every label crossfades to its real field name with a type chip
- provenance strips appear under the numbers
- a panel opens listing, for each figure on screen, the table or event behind it, whether it is
  computed live, on write, or on a schedule, and whether it exists in Origna8 today

The hub carries a price list built from those panels, so the directions can be costed against
each other rather than argued about.

## Conventions

- One file per screen, all CSS and JS inline. No dependencies beyond two Google Fonts.
- Built for 1440 × 900. Dark only. No `localStorage` or `sessionStorage`, in-memory state only.
- The plumbing layer is namespaced `pl-*` so it can never collide with a page's own classes.
- Append `?tweaks=1` to `learner-a-competitive.html`, `learner-b-mastery.html` or any of `v1`
  through `v5` for a live tweak panel: accent, type scale, rule weight, motion.

Palette is sampled from what the live app actually paints, not from its stylesheet variable
names, which disagree. Details in `docs/BRAND.md`.

## Docs

| File | For |
|---|---|
| `docs/ANDREW-WALKTHROUGH.md` | Walking Andrew through the work. Plain English, no field names, with the two questions worth getting answers to. |
| `docs/AB-DECISION.md` | The A versus B argument, with a recommendation. |
| `docs/PLUMBING.md` | What the switch shows, and what each direction costs to build. The Jawad document. |
| `docs/BRAND.md` | The real Origna8 palette, sampled from the live app. Authoritative. |
| `docs/BRIEF.md`, `docs/SHELL.md`, `docs/AUTHORING.md` | The original build contracts. |
