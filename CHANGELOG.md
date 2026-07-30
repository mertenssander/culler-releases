# Release notes

User-facing notes per release. This file is the source of truth: each
GitHub release (on the source repo and on `culler-releases`) carries its
version's section verbatim, plus the standing install note below.

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
