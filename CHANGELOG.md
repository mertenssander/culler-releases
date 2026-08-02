# Release notes

User-facing notes per release. This file is the source of truth: each
GitHub release (on the source repo and on `culler-releases`) carries its
version's section verbatim, plus the standing install note below.

## 0.3.0 — 2026-08-02

**Buttons that teach their keys.** A commissioned design exploration
became culler's new edge chrome — every mouse control now shows the
keyboard shortcut it stands for, then gets out of your way.

- **The rail** (left edge): the current mode's verbs as keycap buttons —
  Pick, Reject, Clear, Rate, Grid, Compare, Filter while culling.
  Hovering teaches; the **Filter** and **Rate** buttons open real
  palettes (click a filter to jump straight to it; click a star chip).
  Buttons you've used about five times politely dim — the rail retires
  itself as you learn. `‹‹` collapses it to a thin line; rest the
  pointer on the line to bring it back.
- **The spine tabs** (right edge): CULL · DEVELOP · CROP · BATCH name
  the workflow. Click to switch; rest on a tab and a palette fires that
  mode's one-shot actions (auto tone, reset…) — from anywhere.
- **The develop panel** grew up: Auto / Reset / Match JPEG as a
  full-width row under the title, Copy / Paste / Before-After at the
  foot, keycap chips on everything, and the sliders scroll on small
  windows instead of clipping.
- **Overviews got stronger**: Survey gained the Grid's peek (`Space` —
  a real loupe with zoom, winnowing keeps working), both overviews now
  accept filter changes in place (the grid re-points live, Survey
  re-deals), every mode hop works uniformly from both (`E C V M S`,
  plus `K`⇄`N` between them), and `A` reaches the batch panel from
  each. Persistent styled key-hint strips replace the old status-line
  text that any action would overwrite.
- **New filter: Picks + unrated** — everything except your rejects, in
  the `F` cycle right after Picks and in the Filter menu.
- The old bottom action dock is retired — everything it did lives on
  in the rail, the spines, and the `⋯` menu (now beside the rail,
  styled like the palettes).
- Fixed: the develop pane could slowly widen until it covered the
  window.

## 0.2.1 — 2026-07-30

- **Server-side ratings now show up.** Stars set in Immich's own web app
  (or by any other tool) were silently invisible when browsing a server:
  real servers report the rating in a different place than culler read.
- **Archive now works against a real server.** The batch Archive action
  used a legacy API field that current Immich accepts and then ignores —
  archived photos now actually leave the timeline.
- **The Immich form teaches the API key**: where to create one (Account
  Settings → API Keys) is written right under the field, and the manual
  gained a permission table for locked-down keys.
- Under the hood: every release is now built by a pipeline that must
  first pass a live integration suite against a real Immich server —
  the two fixes above are what its first run caught.

## 0.2.0 — 2026-07-30

- **Batch from the grid**: press `A` inside the Grid view (`K`) to open
  the Batch panel without leaving the grid — decide what happens to your
  picks and rejects while the whole set is in view. Marking keys keep
  working beside the open panel; `A` closes it again.
- **Menu bar knows the grid**: while the grid is open, menu items that
  don't apply are greyed out (previously a menu click could stack
  Compare or a filter change on top of the grid). Batch… and
  Auto-advance stay enabled — their keys work in the grid.
- **Clearer scan progress**: the top-right pill now says "Scanning
  photos" while a server timeline streams in. That count is culler
  reading the server's catalog — image bytes are only ever fetched
  around where you're looking, never the whole library.
- **Lower memory in long grid scrolls** (thumbnail cache tuned down).
- **Manual**: installation now leads with the DMG; the Immich chapter
  explains what the scan does and doesn't download.

## 0.1.0 — 2026-07-29

First packaged release — a native macOS app for extremely fast,
keyboard-driven culling of RAW+JPEG photo pairs, with Lightroom-style
develop baked in.

- **JPEG-first culling**: flags, stars, color labels, filters —
  everything writes to Lightroom-compatible XMP sidecars, originals
  untouched.
- **Develop on the RAW**: opening the develop panel demosaics the RAW
  (Sony in-camera lens correction included); white balance in real
  Kelvin, tone/curve/vignette, Match JPEG one-click fit.
- **Multi-photo tools**: Compare (V), Survey (N), **Match Look** (M —
  grade one photo, the whole burst follows), and the **Grid view** (K —
  live overview with a progress tally, Space peeks any photo full-size).
- **Sources**: local folders, SD cards, network shares, and Immich
  servers (browse, cull with live sync, upload/download with stacking).
- **Mouse path for new users**: action dock, ▾ menu, clickable stars,
  edge navigation — all invisible until the mouse moves.
- Native menu bar, JPEG export with full EXIF carry-over, batch
  copy/move/trash/upload.

## Install (unsigned builds)

Open the DMG, drag `culler.app` into Applications. On first launch
macOS may refuse it — approve once via System Settings → Privacy &
Security → **Open Anyway**. A notarized build (paid Apple Developer ID)
would remove this step.
