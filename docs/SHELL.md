# The Origna8 app shell · reproduce this exactly

Every variant sits inside this chrome. It is not yours to redesign. Build it once at the
top of your file, then do your work in the content column to its right.

## Left sidebar · 246px wide, `--surface-1` ground, hairline right border

**Logo block** at top: a small rounded-square mark filled with `--rainbow-logo`, then the
wordmark "Origna" in white 600 with the "8" filled by the same rainbow sweep via
`background-clip: text`. 20px, tight tracking.

Then three labelled groups. Group labels are 10.5px, uppercase, `letter-spacing:.12em`,
`--text-3`. Items are 14px, `--text-2`, 34px tall, 10px radius, with a small stroked icon
at 16px on the left. The active item takes `--surface-3` and `--text-1`.

```
ORIGNA8 HQ        Command Center · Domina8 Standings · My Day
GENERA8 MARKET    Live Leads · Lead Packs · Alloca8
CULTIVA8          Relationships · Dialer · Activa8 Agents · Activa8 Voice ·
                  Activa8 Text [badge 2] · Activa8 Insights
```

The `Activa8 Text` badge is a small violet pill with a white `2`.

**Bottom of sidebar,** pinned: an org switcher row (square avatar, "Origna8 Corpor…" over
"Admin", a swap glyph on the right, `--surface-2` fill, hairline border, 12px radius);
below it a "Collapse" row with a left chevron; below that a user row, circular `AS`
avatar, "Aidan Sogorka" over "Admin", and a sign-out glyph on the right.

Icons: draw simple 1.5px-stroke SVGs. Do not use an icon font and do not use emoji.

## Top bar · 56px, spans the content column only, `--background` ground

Left: a search field, 246px wide, `--surface-2`, hairline border, pill-ish 10px radius,
magnifier glyph, placeholder "Search staff, loans, contacts", and a `⌘K` chip on the
right in Geist Mono 11px.

Then two 32px square ghost icon buttons (bug, feedback).

Right cluster, in order:
- a pill: a small `--brand-violet` dot, "Leads to contact", a middot, then `8` in Geist Mono
- a bell with a magenta count badge `9`
- a sun / moon theme pair inside a hairline pill
- **`+ New loan`**, solid white fill, `#0b0b0c` text, 600, pill radius
- **`$ Pricing`**, transparent fill, 1px `--brand-violet` border, white text, pill radius

## Content column

Everything right of the sidebar. Page padding 24px. The page currently opens with an
`Educa8` H1 at 26px/700 beside a small graduation-cap mark in a rounded violet-tinted
square.

**You may redesign the page header.** You may not redesign the sidebar or the top bar.

## Fidelity note

This is a static mock. The shell only has to *read* correctly at a glance and at
1440 × 900. Spend your effort on the content column, but do not leave the shell sloppy,
because a sloppy shell makes the whole variant read as a mockup rather than as the
product.
