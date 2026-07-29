# The culler manual

**culler** is an extremely fast, keyboard-driven tool for going through a
shoot and deciding what survives: rate, pick, reject and label thousands of
RAW(+JPEG) photos, fix tone and crop on the keepers, and move the results
where they belong — a folder, the trash, or an Immich server.

Two ideas shape everything:

- **JPEG-first speed.** Culling never decodes RAW data. The camera JPEG
  next to each RAW (or the full-size preview embedded inside the RAW) is
  what you see, decoded in the background around your position, so
  flipping through photos is instant.
- **Nothing is destructive.** Every rating, flag, label, develop setting
  and crop is written to an XMP sidecar next to the photo, in the same
  schema Lightroom uses. Your originals are never modified — the one
  deliberate exception (`Shift+J`) asks twice and keeps a backup.

Every action has a key, and the keys are always one press away: `H` shows
the in-app cheat sheet.

## Contents

1. [Getting started](01-getting-started.md) — building, launching, and a
   tour of the screen.
2. [Culling](02-culling.md) — ratings, picks and rejects, labels, filters,
   and the one-pass workflow.
3. [Viewing and comparing](03-viewing.md) — zoom, Compare view, Survey
   view, before/after.
4. [Develop](04-develop.md) — white balance, tone, presence, tone curve,
   vignette, auto tone, and copying settings across photos.
5. [Crop, rotate and straighten](05-crop.md) — the crop mode, rotation,
   the straighten slider and the Level tool.
6. [Sources](06-sources.md) — folders, SD cards, shares, Immich servers
   and their albums, and how state syncs.
7. [Batch operations and export](07-batch-and-export.md) — the apply
   panel, JPEG export, uploads, and the pending-work indicator.
8. [Reference](08-reference.md) — every key in every mode, configuration
   files, XMP fields, and known limitations.
