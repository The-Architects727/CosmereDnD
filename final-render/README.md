# Final Render

Everything needed to publish lives here. This is also the **only folder tracked by git**,
so it can be pushed to GitHub without exposing the rest of the vault.

```
final-render/
  art/            <- put your images here, named by slot id
  art/manifest.tsv<- slot id -> hosted URL, once uploaded
  mistborn-homebrew.md   <- the finished brew, copied here by the build
  mistborn-homebrew.pdf  <- the exported PDF, put here by you
```

---

## THE ONE RULE FOR IMAGES

**Draw each image at the aspect ratio listed for its slot.** Aspect ratio is
width divided by height. If the ratio is wrong the image still works, but it will
push the page layout around, which is what caused the runaway-column problem.

| Ratio | Shape | Where it is used |
|---|---|---|
| **0.77 : 1** | Tall portrait, page shaped | Full-page covers |
| **1.00 : 1** | Perfect square | Emblems |
| **1.33 : 1** | Landscape, 4:3 | Most column art |
| **2.00 : 1** | Wide banner | The two metal charts |
| **2.50 : 1** | Very wide banner | The koloss growth diagram |

**Nothing taller than 0.77 : 1.** A portrait taller than that eats most of a
column and starts pushing content off the page.

---

## How to supply an image

1. **Name the file after its slot id**, for example `metal-tin.jpg`, and drop it in `art/`.
2. Rebuild (`python ../renders/build.py`). The placeholder is now sized to your
   image's real aspect ratio, so the layout settles immediately.
3. **When you host it**, add a line to `art/manifest.tsv`:
   ```
   metal-tin	https://i.imgur.com/XXXXXX.jpg
   ```
   (slot id, a TAB, then the URL)
4. Rebuild again. The placeholder is replaced by the real image and **nothing moves**,
   because the space was already reserved correctly.

Homebrewery loads images by URL and cannot take uploads, so hosting is unavoidable.
Imgur is the least effort. A GitHub repo is better long term, because URLs can then be
derived from filenames instead of pasted one at a time.

---

## Every slot

Filenames take any of `.png`, `.jpg`, `.jpeg`, `.webp`, `.gif`.

| Slot id (filename) | Aspect | Suggested pixels | Format | Occupies |
|---|---|---|---|---|
| `cover-front` | **0.77 : 1** | 2550 x 3300 | JPEG | full, ~56 lines |
| `cover-part1` | **0.77 : 1** | 2550 x 3300 | JPEG | full, ~56 lines |
| `bloodlines-vial` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `chart-allomancy` | **2.00 : 1** | 2400 x 1200 | PNG | wide, ~22 lines |
| `force-diagram` | **1.33 : 1** | 960 x 720 | PNG | column, ~15 lines |
| `metal-tin` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `metal-pewter` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `metal-copper` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `metal-bendalloy` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `godmetals-atium` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `savant-tin` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `ferrings-bracers` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `chart-feruchemy` | **2.00 : 1** | 2400 x 1200 | PNG | wide, ~22 lines |
| `metal-gold-feru` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `metal-aluminum-feru` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `twinborn-emblem` | **1.00 : 1** | 900 x 900 | JPEG | column, ~20 lines |
| `compounding-ring` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `cover-part2` | **0.77 : 1** | 2550 x 3300 | JPEG | full, ~56 lines |
| `koloss-growth` | **2.50 : 1** | 2400 x 960 | PNG | wide, ~17 lines |
| `kandra-forming` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `cover-part3` | **0.77 : 1** | 2550 x 3300 | JPEG | full, ~56 lines |
| `background-hazekiller` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `cover-part4` | **0.77 : 1** | 2550 x 3300 | JPEG | full, ~56 lines |
| `class-mistborn` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `class-feruchemist` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `class-hemalurgist` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `hema-bindpoints` | **0.77 : 1** | 2550 x 3300 | PNG | full, ~56 lines |
| `hema-inquisitor` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `hema-chimera` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `cover-part5` | **0.77 : 1** | 2550 x 3300 | JPEG | full, ~56 lines |
| `economy-forms` | **1.33 : 1** | 960 x 720 | JPEG | column, ~15 lines |
| `cover-appendix` | **0.77 : 1** | 2550 x 3300 | JPEG | full, ~56 lines |

---

## Notes

- **The metal symbols are no longer separate images.** All sixteen Allomantic symbols
  belong inside `chart-allomancy`, and all sixteen Feruchemical ones inside
  `chart-feruchemy`. That is 32 fewer files to make and place.
- **Keep file sizes sensible.** The PDF was already 26 MB with no art at all. JPEG at
  quality 80 for painted scenes, PNG only for charts, diagrams and anything needing
  transparency.
- **300 dpi** at the printed size is the target, which is what the suggested pixel
  dimensions above work out to.
