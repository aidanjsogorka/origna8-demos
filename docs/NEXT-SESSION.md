# Next session: make it more dynamic and more digestible

Paste the block at the bottom into a fresh Claude Code session. Everything above it is
context you may want to skim first.

---

## Where this stands

Live at `https://aidanjsogorka.github.io/origna8-demos/educa8/`, deploying from `main` at
root, roughly a minute per push. Local clone at `~/code/origna8-demos`. Nine screens, each a
single self-contained HTML file, all CSS and JS inline, built for 1440 × 900, dark only, no
storage APIs, no external assets.

The aesthetic is settled and is not up for debate. The open question is a product one: **A,
points and rankings, or B, driven by your open loans.** Both arguments are built. `docs/AB-DECISION.md`
carries the reasoning and a recommendation.

## The problem this session is for

Aidan's read, after looking at both screens whole:

> "The previous UIs were full of half dotted lines, etc, it was a lot."

He is right, and the diagnosis is specific. Earlier work fixed the *panel* rhythm on both
screens. It never touched the *marks*. Screen one of B currently carries:

| | count |
|---|---|
| Recall nodes | 19 |
| Capability marks, 9 rows × 3 columns | 27 |
| Lesson boxes in the course table | ~30 |
| **Small squares on one screen** | **~76** |

Three separate square-mark vocabularies that look nearly identical and mean completely
different things. Plus the recall band alone carries three textures inside one 452px panel:
solid grey fill, amber diagonal hatch, dashed orange outline. That is the noise.

A is in better shape: 1966px, four panels, nothing repeating. B is 2858px.

## Three cuts already proposed and not yet run

1. **Drop the lesson boxes in the course table.** Six rows × five outlined boxes to say
   "2 of 5 read", which the text beside it already says. Removes ~30 glyphs and one entire
   vocabulary for free.
2. **Kill the amber hatch on lapsed recall nodes**, use a solid amber fill. Keep the dashed
   outline for never-read, because "not started" as an outline is conventional and one
   non-colour cue has to survive for accessibility. Two textures become one.
3. **Reassess the capability marks** after 1 and 2. 27 is a lot, but that panel is the thesis
   and a matrix does need marks.

Roughly 76 marks to 46, three vocabularies to two, three textures to one. Do these first,
before adding anything, so the new work lands on a clean surface.

## The actual goal

**More dynamic and more digestible, at the same time.** Those pull against each other and
that tension is the brief. Adding motion to a page already carrying 76 small marks makes it
worse. The likely shape of the answer is *replacing* static marks with one thing that moves
and means something, not adding motion on top.

### Anthony's encyclopedia animation

Anthony messaged about an encyclopedia animation. **His actual message is not in the repo and
was not available when this was written, so paste it into the prompt below before starting.**
Do not build a brief around the phrase alone.

Speculation, clearly marked as such and worth exactly nothing until his message is read: the
strongest version for this product would replace the abstract squares with one object that
assembles. A loan file builds up from its parts as an officer learns the concepts behind them,
so the thing on screen is the thing they actually handle. That would serve both goals at once,
because it is motion that carries meaning rather than decoration, and it collapses three mark
vocabularies into one object. It may be nothing like what Anthony meant.

### Tooling available for the exploration

Both are connected as MCP servers in Cowork sessions. Check they are live before relying on
them; interactively-authenticated servers can be absent in headless runs.

| Tool | Use for |
|---|---|
| Higgsfield: `models_explore` then `generate_image` / `generate_video` | Look development, motion reference. `explainer_video`, `animation_actions` and `motion_control` are the relevant ones for an encyclopedia-style piece. Call `models_explore(action:'recommend')` first. |
| Hugging Face: `gr1_z_image_turbo_generate` | Free fast drafts while exploring directions |

**Hard constraint that shapes all of this.** `docs/BRIEF.md` requires placeholder graphics only:
CSS shapes, SVG, drawn diagrams, no external images. So generated imagery is for **exploration
and reference**, never shipped into the demos. Find the direction with AI, then hand-build it
in CSS and SVG. Anything generated that gets kept has to be inlined as SVG or a data URI, and
even then, prefer drawing it.

## Standing rules, unchanged

- Never blue-to-purple gradients, glassmorphism, gradient-mesh thumbnails, Inter, centred body
  copy, equal-height card walls, emoji as icons.
- **Never em dashes in any copy.** Commas, colons or full stops. A hook checks this on write.
- One accent, `#FF7A2F`, meaning "live, next, yours". The full logo sweep fills the logo mark
  and hairline edges only, never a background or a button.
- Reproduce the existing app shell exactly. The sidebar and top bar are not yours to redesign.
- Plain English everywhere a person reads. Andrew is not technical and Dan asked for this
  explicitly. No "argued as", no "lit node", no internal family names like `swiss-grid`. The
  technical vocabulary lives behind the plumbing switch and nowhere else.
- Ship a tweak bar on the dev-server build per the `design-taste` protocol. Already present on
  A and B behind `?tweaks=1`.

## Known issues, deliberately left

- **The pipeline panel has no empty state.** B rests entirely on "your open loans decide what
  to read", so an officer with zero loans gets a blank argument. That is the new hire who most
  needs the training. Real hole, needs a decision.
- **"Running blind: 5" is B's own thesis and it is the third stat in the header**, same size as
  the other two, and restated in a footnote. The most important number on the screen is never
  the most prominent thing on it. (It read 3 until 2026-07-31, against five tinted rows and the
  page's own formula, `count(capability) where run_on_live_file and not read`. Now 5 everywhere.)
- **`--text-3` (`#6c6c74`) is 3.8:1 on the app background**, under the 4.5:1 AA threshold. It is
  inherited from the live app, so it was reported rather than silently changed. `#7a7a83` clears
  it. Aidan's call.
- **Six `layout-transition` and one `dark-glow` finding remain in v1, v3 and v4.** Pre-existing
  in the archived directions, `max-height` accordions and a hover shadow. Left alone on purpose,
  because those five exist as the record of how the direction was chosen and their value is in
  being unchanged.
- **Two `side-tab` findings remain in v4**, both 3px on `--sig`. That is that direction's own
  datasheet rule weight, not the shared accent motif.

## Traps this session hit, so you do not

- **The design hook resolves its config from the session cwd, not from the edited file's repo.**
  If you launch from `~/JWLs OS` and edit `~/code/origna8-demos`, it reads
  `~/JWLs OS/.impeccable/config.json`. That config exists and carries the approved Geist Mono
  ignore. Launching from the repo root instead is cleaner and the repo has its own copy.
- **Write after every successful edit, not once at the end.** Two Python passes here asserted
  on a later step, threw, and silently discarded the earlier successful edits because the
  `write_text` never ran.
- **Deleting markup leaves its JavaScript behind.** Removing a panel orphaned its data and its
  renderer twice, and the page threw on load until the dead code went too. The render check
  caught it both times; reading the diff did not.
- **Class-name collisions.** The plumbing layer is namespaced `pl-*` for a reason: unprefixed
  `.ph` and `.lb` silently overwrote direction 04's own classes and broke its masthead with no
  error at all.
- **GitHub Pages CDN serves stale copies for a few minutes.** Verify with a cache-buster query
  before concluding a push did not land.

## Verification that has been working

Playwright at 1440 × 900 on every changed file, checking four things: console errors,
horizontal overflow **in both switch states**, anything left stuck at `opacity: 0` after a full
scroll, and clipped text where `scrollWidth > clientWidth`. That last one caught a date
rendering as "went stale Jul 0". Then the banlist grep, then
`node ~/.claude/skills/impeccable/scripts/detect.mjs --json <files>`.

Scripts from this session are disposable and were not kept. Rewrite them; they are twenty lines.

---

## The prompt

```
Continue the Origna8 Educa8 work. Read first:
- ~/JWLs OS/CLAUDE.md
- docs/NEXT-SESSION.md in the repo, which is the full handoff
- docs/BRIEF.md, docs/BRAND.md, docs/SHELL.md, docs/AB-DECISION.md
- The design-taste skill, and impeccable

Repo: github.com/aidanjsogorka/origna8-demos, cloned at ~/code/origna8-demos.
Launch this session from the repo root, not from the vault, so the design hook
reads the right config. Live at aidanjsogorka.github.io/origna8-demos/educa8/.

GOAL
Make the two learner screens more dynamic and more digestible. Those pull
against each other, and that tension is the brief. The screens already carry
about 76 small square marks across three vocabularies that look alike and mean
different things, so adding motion on top makes it worse. Look for one thing
that moves and means something, replacing static marks rather than joining them.

ANTHONY'S ENCYCLOPEDIA ANIMATION
[PASTE ANTHONY'S ACTUAL MESSAGE HERE BEFORE STARTING. Do not build on the
phrase alone. If it is not pasted, ask for it rather than guessing.]

Explore the concept properly before building. Higgsfield MCP for motion and
look reference (models_explore first, then generate_image or generate_video;
explainer_video and motion_control are the relevant ones). Hugging Face
gr1_z_image_turbo_generate for fast free drafts. Generated imagery is for
exploration only and never ships: the brief requires CSS, SVG and drawn
diagrams, no external assets. Find the direction with AI, hand-build it.

DO FIRST, before adding anything
1. Drop the lesson boxes in the course table on both screens. Six rows of five
   outlined boxes to say "2 of 5 read", which the text beside it already says.
2. Replace the amber diagonal hatch on lapsed recall nodes with a solid amber
   fill. Keep the dashed outline for never-read as the one non-colour cue.
3. Then reassess the capability marks with fresh eyes.
That takes B from about 76 marks to 46 and from three textures to one. New work
should land on a clean surface.

RULES
- Plain English everywhere a person reads. Dan asked for this directly. No
  internal jargon, no design family names. Technical words live behind the
  plumbing switch only.
- Never em dashes. Never blue-to-purple gradients, glassmorphism, Inter,
  centred body copy, emoji as icons.
- One accent, #FF7A2F. The logo sweep fills the logo mark and hairline edges
  only.
- Reproduce the app shell exactly. Sidebar and top bar are not yours.
- Ship the tweak bar on dev builds.

VERIFY, then push
Playwright at 1440x900 on every changed file and LOOK at the screenshots. Check
console errors, horizontal overflow in both switch states, anything stuck at
opacity 0 after a full scroll, and clipped text where scrollWidth exceeds
clientWidth. Then the banlist grep, then detect.mjs. Then commit and push to
main; Pages redeploys in about a minute and its CDN can serve stale copies for
a few minutes after, so verify with a cache-buster.

Flag before you start if this run will be token-expensive.
```
