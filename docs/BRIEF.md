# Educa8 redesign · shared build contract

You are building ONE variant of a redesign of **Educa8**, the learning section inside
**Origna8**, a mortgage-origination platform. Every variant renders the same content and
lives inside the same app shell. Only the aesthetic family differs.

---

## INTENT

Educa8 is the in-app academy for **new and early-career loan officers**, people in their
twenties who grew up on progression systems (Duolingo streaks, Strava stats, game skill
trees) and are now being asked to learn TRID timelines and underwriting ratios.

Right now the section is inert. The single action we want: **a young LO opens Educa8 and
starts a chapter within five seconds, then comes back tomorrow.**

## THE DIAGNOSIS · what is actually wrong today

Fix these in the design. This is the substance; the aesthetic is the delivery.

1. **No reason to start.** Six identical cards, every one labelled "Not Started," in no
   order, with no prerequisites. Uniform choice is paralysis.
2. **The loudest element on the page reports that you have done nothing.** A full-width
   banner reading `0 Active · 0 Completed · 6 Not Started`. It is also a blue-to-purple
   gradient, which is banned.
3. **Thumbnails carry zero information.** Six stock gradient meshes. Pure decoration.
4. **Progress is not rewarded.** "Mark as Complete" is the entire feedback loop. Nothing
   lands anywhere, nothing accumulates, nothing is visible to anyone else.
5. **The app already has a scoreboard, Domina8 Standings, and Educa8 does not touch
   it.** Learning should feed the competitive layer that already exists.
6. **The AI Mentor is wallpaper.** A dead right rail with a canned greeting. It should be
   the thing that asks *you* questions, not a chat box waiting to be noticed.
7. **Reading is the only verb.** Fifteen minutes of markdown with no retrieval practice,
   no scenario, no check for understanding.
8. **The Guides tab is better designed than the Courses tab**, real screenshots, step
   counts, minute estimates, a numbered path. Courses should learn from Guides.

## MECHANICS YOU MAY INTRODUCE

Scope is approved for visual **and** mechanics. Express whichever serve your family:

- One dominant **Continue / Start here** object instead of six equal cards
- A **sequenced path** with prerequisites, not a flat grid
- **Streak** and **XP**, wired visibly to Domina8 Standings
- **Time-to-complete** as a first-class promise (the Guides tab already does "5 min")
- **Retrieval checks** after each chapter; the AI Mentor asks the question
- Thumbnails that **encode information** (chapters done, difficulty, category) rather
  than being gradient noise
- Rank / cohort comparison ("you are 3rd on your branch this week")

Invent freely within your family. Do not add all of them; pick what your aesthetic can
carry with conviction.

---

## HARD CONSTRAINT · it must still be Origna8

This ships inside a live app. It must not read as a microsite bolted on. Reproduce the
app shell exactly as specified in `SHELL.md` and inherit the tokens in `TOKENS.css`.
Your aesthetic operates **inside the content column**, on the page's own structure,
type treatment, rhythm, and mechanics, not by replacing the chrome.

Two exceptions where you may deviate from the app's defaults, if your family demands it:

- **Type inside the content column.** The shell stays Hanken Grotesk. Your content area
  may introduce one additional face if your family calls for it.
- **Radii and surface treatment inside the content column.** `mono-technical` may go to
  zero radius in its own content, for example. The shell keeps its own.

---

## THE CONTENT · use verbatim, do not invent course names

Six courses:

| Category | Level | Title | Chapters | Description |
|---|---|---|---|---|
| Fundamentals | Beginner | Mortgage Fundamentals | 5 | Master the basics of mortgage lending, from loan types and qualifying criteria to the full application-to-closing workflow. |
| Products | Intermediate | FHA & VA Loan Programs | 5 | Deep dive into government-backed loan programs. Understand eligibility, guidelines, and how to structure these loans for your borrowers. |
| Compliance | Intermediate | Compliance & TRID | 4 | Navigate regulatory requirements confidently. Master TRID timelines, disclosure rules, and compliance best practices. |
| Pricing | Advanced | Rate Lock Strategies | 4 | Advanced pricing tactics: when to lock, float-down options, and how to protect your borrower in volatile markets. |
| Sales | Beginner | Building Your Pipeline | 5 | Proven strategies for lead generation, referral partner development, and consistent follow-up that keeps your pipeline full. |
| Underwriting | Intermediate | Underwriting Essentials | 6 | Think like an underwriter. Learn how income, assets, and credit are analyzed so you can submit clean files that close faster. |

Chapters of **Mortgage Fundamentals** (real, use these):
`What Is a Mortgage?` 15 min · `Loan Types Overview` 20 min · `The Qualification
Process` 25 min · `Application to Closing` 30 min · `Key Documents Checklist` 15 min

Real body copy from chapter 1, for the reading view:

> A mortgage is a loan used to purchase real estate, where the property itself serves as
> collateral.
>
> **Key Concepts** · Principal: the amount borrowed. Interest: the cost of borrowing.
> Amortization: how the loan is paid off over time. Escrow: funds held for taxes and
> insurance.

Tabs that exist today: `All Courses (6)` · `Active (0)` · `Completed (0)` · `Guides`.
The Guides tab holds 28 guides in 9 groups (Start here, Nurturing playbook 6, Origna8 HQ
2, Relationships 3, Cultiva8 3, Loan Center 5, Borrower portal 2, Eleva8 1, Branch
management 6), each with a step count and a minute estimate.

**Show a realistic in-progress state, not an empty one.** Assume the user has finished
2 chapters of Mortgage Fundamentals and 1 of Building Your Pipeline. An empty state is
the current design's biggest failure and you should not reproduce it. You may show the
true-empty state as a secondary detail if your design handles it well.

---

## WHAT TO BUILD

**Two views, both in one file, on the same page, stacked vertically:**

1. **The Educa8 index**, how the six courses and the guides are presented.
2. **A course-detail / chapter-reading view**, Mortgage Fundamentals, chapter 1 open.

Separate them with a thin full-width label bar reading `VIEW 2 · COURSE DETAIL` so it is
obvious they are two screens, not one long page. The label bar is scaffolding, style it
minimally.

## TECHNICAL

- **One self-contained HTML file.** All CSS and JS inline. Google Fonts via CDN is fine.
- Designed for **1440 × 900**. Does not need to be responsive.
- **No localStorage or sessionStorage.** In-memory only.
- Placeholder graphics only, CSS shapes, SVG, dithered canvas, drawn diagrams. No
  external images, no image generation. If you need a product screenshot, draw a
  simplified abstraction of one in CSS/SVG.
- Motion is welcome where the family supports it, and should be *specific*, not
  everything fading in identically.
- Interactivity is welcome: working tabs, an expanding chapter, a quiz that responds.

## THE BANLIST · automatic fail

- Blue-to-purple gradients, anywhere, in any form
- Glassmorphism, frosted panels, translucent card stacks
- Stock gradient-mesh thumbnails (this is what we are replacing)
- More than one accent color competing
- Inter, unless your family file names it deliberately
- Only two type sizes, build a real scale
- Centered body copy
- Equal-height card walls repeated down the page
- Every section the same height and rhythm
- Rounded corners and drop shadows on everything
- A decorative accent bar under every heading
- An icon beside every bullet; emoji as iconography
- 3D blobs, floating abstract shapes, isometric illustration, Corporate Memphis
- Everything animating in at the same distance, duration, and easing
- Em dashes in any copy you write. Use commas, colons, or full stops.
- The words: delve, tapestry, leverage, robust, seamless, journey, unlock, elevate,
  game-changer, "in today's fast-paced world"

Two closing questions before you finish:

1. Would a sharp reviewer suspect a template generator made this?
2. Could this be any other company's page with the logo swapped?

If yes to either, fix it.

## OUTPUT

Write your file to the exact path given in your task. Return a **short** report: the
family, the three most important decisions you made, the mechanic you introduced, and
one thing you are unsure about. No preamble, no summary of the brief back to me.
