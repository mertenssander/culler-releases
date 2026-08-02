# Culling

Culling is a keyboard rhythm: look, judge, move on. Every judgment is
written to the photo's XMP sidecar immediately — there is no save step.

## Moving around

| Key | Action |
| --- | --- |
| `←` `→` | previous / next photo |
| `↑` `↓` | jump 10 back / forward |
| `Home` / `End` | first / last photo |

Decoding runs ahead of you in both directions, so holding an arrow key
never waits on the disk.

## Judging

| Key | Action |
| --- | --- |
| `1`–`5` | star rating (press the same number again to clear) |
| `0` | clear the rating |
| `P` | pick (press again to un-pick) |
| `X` | reject (press again to un-reject) |
| `U` | clear the flag |
| `6`–`9` | color label: red, yellow, green, blue (again clears) |

Stars, flags and labels are three independent axes — a photo can be a
4-star, picked, red-labeled photo. Labels show as a colored bar on the
filmstrip thumbnail and persist as Lightroom's own `xmp:Label`, so they
survive a round trip through other tools.

**Auto-advance** (`T` toggles it) moves to the next photo after every
rating or flag, which is what makes a first pass fast: `P`, `X`, `3`,
`X`, `P`… and you're ten photos in. Turn it off when you want to stack
multiple judgments on one photo; the overlay shows `[manual advance]`.

## Culling with the mouse

The keyboard is the fast path, but everything above is clickable the
moment the mouse moves — and every control shows its key, so the buttons
teach the shortcuts as you go:

- **The rail** (left edge) carries the culling verbs as keycap
  buttons — Pick, Reject, Clear, Rate, Grid, Compare, Filter — each
  showing its key with the name under it; hovering flares the full
  teaching line — and the **Filter** and **Rate** buttons open real
  palettes: click a filter to jump straight to it, click a star chip
  (1–5, 0) to rate. Its **⋯** button opens the menu with the rest: the
  live filter, Survey, Match Look, Batch, Sources, Auto-advance and
  Help ([screenshot](img/16-more-popover.png)). Buttons you've used
  about five times (key or click) politely dim — the rail retires
  itself as you learn. The **‹‹** at its foot collapses it to a thin
  line; click the line (or rest the pointer on it) to bring it back.
- **The spine tabs** (right edge) name the workflow — CULL · DEVELOP ·
  CROP. Click one to switch; rest the pointer on an inactive tab and a
  small palette appears to fire that mode's one-shot actions (auto
  tone, reset…) without switching at all.
- **The stars in the top-left overlay** become five click targets while
  the pointer is moving — hover previews, clicking sets the rating, and
  clicking the same star again clears it, exactly like the number keys.
- **Hover a side edge of the photo** for previous/next arrows (at fit
  zoom; when zoomed in, the mouse pans instead).

The photo itself stays untouched: the rail is a slim gutter, never an
overlay, and collapsing it gets you within three pixels of a bare
photo. The first launch shows a one-line hint beside the rail, once,
and never again.

## Filters: working in passes

`F` cycles the view: **All → Picks → Picks+unrated → Rejects → Unrated → Edited →
Labeled** and back. `Shift+F` returns straight to All. The overlay shows
the active filter, and the position counter (`3/12`) counts within it.

For a second pass over your ratings, `Cmd/Ctrl+1`–`5` shows only photos
with *at least* that many stars, and `Cmd/Ctrl+0` (or `F`) clears it.

A photo that stops matching the filter leaves the view as you judge it —
rejecting a photo in the Picks view removes it and advances, which is
exactly the winnowing motion you want.

## The one-pass workflow

1. Open the folder, `T` on (the default), and run through everything with
   `P` / `X` / arrows. Don't deliberate — that's what the next passes are
   for. Use [Survey view](03-viewing.md#survey-view-n) on bursts.
2. `F` to Picks. Rate the keepers `1`–`5`; use
   [Compare view](03-viewing.md#compare-view-v) when two frames fight for
   the same slot.
3. `Cmd+4` to see only the best, [develop](04-develop.md) and
   [crop](05-crop.md) them.
4. `F` to Rejects, then [batch-move or trash them](07-batch-and-export.md).

Everything you set here follows the photo: Lightroom reads the same
sidecars on import, and on an Immich source the ratings sync to the
server as you press the keys ([details](06-sources.md#write-through-sync)).
