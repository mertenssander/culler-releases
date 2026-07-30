# Reference

## Keys — normal view

| Key | Action |
| --- | --- |
| `←` `→` / `↑` `↓` | previous / next photo (±10) |
| `Home` / `End` | first / last |
| `P` / `X` / `U` | pick / reject / clear flag |
| `1`–`5`, `0` | star rating / clear (same number again clears) |
| `6`–`9` | color label red / yellow / green / blue (again clears) |
| `Z` / `Space` / double-click | zoom 100% ⇄ fit (drag to pan) |
| Scroll / pinch | continuous zoom around the pointer (to 8×; snaps back to fit) |
| `F` / `Shift+F` | cycle filter (All → Picks → Rejects → Unrated → Edited → Labeled) / show all |
| `Cmd/Ctrl+1`–`5`, `0` | filter to at least N stars / show all |
| `K` | Grid view — overview of the working set (see [Viewing](03-viewing.md#grid-view-k)) |
| `V` | Compare view |
| `N` | Survey view |
| `M` | Match Look — fit a burst's tone to the current photo; `M` commits, `Esc` cancels (see [Develop](04-develop.md#match-look-m)) |
| `R` / `L` (match) | re-anchor the reference / unlink-link the focused photo |
| `E` | develop panel — RAW-paired photos develop the RAW (see [Develop](04-develop.md#raw-paired-photos-develop-the-raw)) |
| `Shift+A` | auto tone |
| `Shift+C` / `Shift+V` | copy / paste develop + crop settings |
| `C` | crop mode |
| `R` / `Shift+R` | rotate 90° clockwise / counter-clockwise |
| `\` | before / after (untouched original) |
| `W` | clipping warnings on the photo (red = blown, blue = crushed; RAW mode adds gold = recoverable, red = clipped in the file) |
| `S` | sources pane |
| `G` | step into / out of a stack (Immich) |
| `A` | apply panel |
| `J` / `Shift+J` | export JPEG / overwrite the paired JPEG (press twice) |
| `T` | toggle auto-advance |
| `O` | open another folder (ad-hoc, not saved) |
| `D` | debug HUD |
| `H` | help overlay |
| `Esc` | step out of a stack |

## Keys — crop mode (`C`)

| Key | Action |
| --- | --- |
| `Enter` / `C` | apply and exit |
| `Esc` | cancel (with the Level tool armed: disarm it first; press again to cancel the crop) |
| `←` / `→` | nudge the straighten angle by 0.1° (`Shift` = 1°) |
| `R` / `Shift+R` | quarter turn |
| `L` | arm / disarm the Level tool |
| `H` | help overlay |

## Keys — Grid view (`K`)

| Key | Action |
| --- | --- |
| arrows | move the cursor a cell / a row |
| `Home` / `End`, `PgUp` / `PgDn` | first / last photo, page up / down |
| `P` `X` `U`, `0`–`5`, `6`–`9` | mark the cursored photo |
| `Space` | peek the cursored photo full-size (real zoom; `Space`/`Esc` pops back, arrows flip neighbors) |
| `T` | toggle auto-advance |
| `Z` | cycle cell size (while peeking: zoom, as in the loupe) |
| `A` | batch panel, in place (the grid stays up) |
| `E` `C` `V` `N` `M` `S` | exit, then act on the cursored photo |
| `H` | help overlay |
| `Esc` / `Enter` / `K` | exit onto the cursored photo |

## Keys — Compare view (`V`)

| Key | Action |
| --- | --- |
| `←` / `→` | advance the Candidate |
| `↑` | promote the Candidate to Select |
| `↓` | swap Select ⇄ Candidate |
| `Tab` (or click) | focus the other pane — marking keys hit the focused pane |
| `P` `X` `U`, `0`–`5`, `6`–`9` | mark the focused pane |
| `Z` / `Space` / double-click | synced zoom |
| `\` | before / after (both panes) |
| `H` | help overlay |
| `Esc` / `V` | exit onto the Select |

## Keys — Survey view (`N`)

| Key | Action |
| --- | --- |
| arrows | move the focus through the grid |
| `X` | reject + remove from the grid |
| `⌫` / `Delete` | remove without judging |
| `P` `U`, `0`–`5`, `6`–`9` | mark the focused photo |
| `H` | help overlay |
| `Esc` / `N` | exit onto the focused survivor |

## Keys — sources pane (`S`)

| Key | Action |
| --- | --- |
| `↑` / `↓` | select a row |
| `Enter` | open the selected source or album |
| `→` / `←` | expand an Immich row into its albums / collapse |
| `N` | add a source |
| `⌫` / `Delete` | remove the selected source (press twice; albums: no-op) |
| `H` | help overlay |
| `Esc` / `S` | close the pane (Esc closes the add-row first) |

## Configuration files

Everything lives in `~/.culler/`:

| Path | Contents |
| --- | --- |
| `sources.conf` | the saved sources (tab-separated; Immich API keys are **not** here — they live in the OS keychain) |
| `export.conf` | the JPEG export preset |
| `state/` | per-server culling state for Immich sources (the write-through queue's source of truth) |
| `cache/` | disk cache of remote previews and embedded RAW previews (4 GB, least-recently-used eviction) |

Environment overrides: `CULLER_CONFIG_DIR` and `CULLER_CACHE_DIR` relocate
the above; `CULLER_IMMICH_URL` + `CULLER_IMMICH_KEY` inject a temporary
Immich source for one session without persisting anything.

## XMP fields

Sidecars are edited in place — fields written by other tools survive.

| Field | Meaning |
| --- | --- |
| `xmp:Rating` | stars 0–5; −1 marks a reject (per the XMP spec) |
| `xmp:Label` | color label name |
| `culler:Flag` | pick / reject / none |
| `crs:Exposure2012`, `crs:Contrast2012`, `crs:Highlights2012`, `crs:Shadows2012` | basic tone |
| `crs:IncrementalTemperature`, `crs:IncrementalTint` | white balance while developing a JPEG (the non-raw form) |
| `crs:Temperature`, `crs:Tint` | white balance while developing a RAW (real Kelvin; absent = As Shot) |
| `culler:DevelopMode` | "Raw" when the photo carries RAW-mode WB edits |
| `crs:LensProfileEnable` | "0" when in-camera lens correction is turned off (absent = on) |
| `crs:Vibrance`, `crs:Saturation` | presence |
| `crs:ParametricHighlights/Lights/Darks/Shadows` | tone curve regions |
| `crs:PostCropVignetteAmount` (+ `Style`) | vignette |
| `crs:HasCrop`, `crs:CropLeft/Top/Right/Bottom`, `crs:CropAngle` | crop + straighten |
| `culler:OrientationQuarter` | 90° turns (Lightroom handles these separately) |

## Known limitations

- Old Sony ARW files embed only a 1616×1080 preview — that's the best a
  RAW-only ARW can display *while culling* (the develop panel demosaics
  the RAW itself, at full quality).
- Lens correction reads the camera's own embedded parameters (Sony
  ARW). RAWs from other makes develop uncorrected for now, so their
  framing can drift slightly from the corrected camera JPEG's.
- Develop and crop on an Immich source stay local until you export or
  upload; only ratings, flags and labels sync live.
- Upload to Immich copies — there is no "move" yet, deliberately (see
  [batch operations](07-batch-and-export.md#the-apply-panel-a)).
- The app is exercised primarily on macOS so far; a Windows validation
  pass is on the roadmap.
