# Origna8 true colorway · sampled from the live app, 30 Jul 2026

Sampled from painted computed styles on `app.origna8.com`, not from the stylesheet's
variable names, which are stale and disagree with what actually renders. **Use these.**

## The logo sweep · the real brand colours

```
linear-gradient(115deg, #FF7A2F 0%, #FF4D8D 32%, #B14DFF 64%, #4D6BFF 100%)
```

| Stop | Hex | Name |
|---|---|---|
| 0% | `#FF7A2F` | brand orange |
| 32% | `#FF4D8D` | brand pink |
| 64% | `#B14DFF` | brand purple |
| 100% | `#4D6BFF` | brand blue |

This sweep is warmer and younger than anything the app currently uses outside the logo
mark, which is the single most useful finding for this brief. The product is dressed far
more soberly than its own brand.

**Rules for the sweep.** It may fill the logo mark, the `8` in the wordmark, and hairline
signal elements one or two pixels thick. It may NOT become a page background, a banner, a
card fill, or a button. The purple-to-blue half of it is exactly the gradient the banlist
forbids, so the full sweep as a large surface is out. The 8px inset border trick the app
already uses (`linear-gradient(#16161a,#16161a), linear-gradient(115deg, …)`) is a
sanctioned way to get a sweep-edged pill, and it is fair game.

## Primary accent

**`#FF7A2F`.** One accent, and it means "live, next, yours." The app leans on violet
everywhere and orange is the warm end nobody has used. It is a real brand stop, not an
invention.

Do not introduce a second competing accent. Category colours below are coding, not accent.

## Course category colours · as the live app paints them

Keep these. They are the one place the app is already doing something right, and Andrew
will recognise his own courses by them. Use them as **solid marks, small chips, rules, and
node fills**, never as full-bleed gradient card thumbnails, which is the thing being
replaced.

| Category | Gradient as painted | Use this solid |
|---|---|---|
| Fundamentals | `#F5A623 → #F0C040 → #E8B84A` | `#F0B93A` |
| Products | `#7ECBCD → #5EEAD4 → #38BDF8` | `#5EEAD4` |
| Compliance | `#A78BFA → #8B5CF6 → #7C3AED` | `#8B5CF6` |
| Pricing | `#6D28D9 → #4C1D95 → #3B0764` | `#6D28D9` |
| Sales | `#F59E0B → #EF4444 → #EC4899` | `#EF4444` |
| Underwriting | `#059669 → #10B981 → #34D399` | `#10B981` |

## Ground, text, lines · unchanged, these were right

```
--background #08080a   --surface-1 #111114   --surface-2 #16161a   --surface-3 #1e1e23
--text-1 #f4f4f5       --text-2 #a0a0a8      --text-3 #6c6c74
--border #ffffff1a     --border-2 #ffffff0e  --ring #ffffff38
--pos #34d399  --neg #f87171  --warn #f0b649
```

Buttons: `+ New loan` is solid white on `#0b0b0c`, pill radius. `$ Pricing` is transparent
with a `#7c3aed` border.

Radii `8 / 12 / 18 / 24 / 999`. Motion `cubic-bezier(.22,.61,.36,1)` at `.14s / .22s / .32s`.

Type: **Hanken Grotesk** (300–800), **Geist Mono** (400–600) for every numeral, ID, and
identifier. Body 16px. H1 26px / 700 / -0.78px.

Google Fonts:
`https://fonts.googleapis.com/css2?family=Hanken+Grotesk:wght@300;400;500;600;700;800&family=Geist+Mono:wght@400;500;600&display=swap`

## Known gap

The app has a light theme behind the sun/moon toggle. These demos are dark only. Worth
saying out loud rather than pretending it is handled.
