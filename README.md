# Personal Genomics & Data Science

A 16-slide presentation on personal genomics and data science, built as a single self-contained HTML file. Each slide is a "room" with a generative canvas background, a scrambling headline and a different transition between rooms.

No build step, no dependencies, no network requests.

<!-- Add a screenshot or a short screen recording here:
![Preview](docs/preview.gif) -->

## Features

- Five generative canvas scenes: flow field, nested lattice, ribbons, warp tunnel and plasma
- Five transitions that rotate between slides: iris wipe, sliced shift, pixel dissolve, warp zoom and radial sweep
- A glitch tear layered over every transition, and headlines that scramble into place
- Responsive layout, readable on phones
- Respects `prefers-reduced-motion`: the glitch and scramble effects switch off
- Elastic net formula written in MathML, so it stays sharp at any size

## Controls

| Action | Input |
|---|---|
| Next slide | Click, tap, `Space`, `Enter`, `→` or scroll down |
| Previous slide | `←` or scroll up |
| Toggle autoplay (off by default) | `P` |

## Run it

Open `index.html` in any modern browser. If your browser blocks anything when opening from disk, serve the folder instead:

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

1. Rename the file to `index.html` and put it in the repo root.
2. In the repository, go to **Settings → Pages**.
3. Set the source to your main branch and the `/ (root)` folder, then save.
4. The site goes live at `https://<your-username>.github.io/<repo-name>/`.

## Slide outline

1. Title
2. Precision Analytics
3. P4 Medicine Substrates
4. 5 Million sites of variation
5. From Reads to Variants (FASTQ, BAM/CRAM, VCF)
6. Bioinformatic Pipeline
7. Calling & Annotation Stack
8. WGS vs WES Targeting
9. Elastic Net Regularization
10. Why Regularize Genomic Models
11. Polygenic Risk Scores
12. Judging a Risk Score
13. Promise and Risk
14. What Comes Next
15. Questions & Discussion
16. Image Sources

## Editing the content

All slide text lives in one array named `SL` near the top of the script. Each entry is a plain object:

| Field | Meaning |
|---|---|
| `k` | Small kicker line above the title |
| `t` | Slide title |
| `s` | Subtitle or lead paragraph |
| `c` | Cards, as `[heading, text]` pairs |
| `l` | Two bullet columns, as `[heading, [bullets]]` pairs |
| `m` | Label and value pairs (title slide details) |
| `f` | Raw HTML or MathML for a formula panel |
| `n` | Footnote line |
| `big` | Oversized hero number |
| `hero` | Larger title style |
| `nn` | Number the cards 1, 2, 3... |

Add, remove or reorder entries and the slide count, counter and navigation update on their own.

## How it works

- Every scene draws to its own offscreen canvas. During a transition, the current and next canvases are composited onto the visible one using a clip, slice, block or zoom effect.
- Slide `i` uses scene `i % 5`, so neighbouring slides never share a scene.
- Slide text is swapped at the midpoint of each transition, so the old content fades out and the new content fades in underneath the effect.
- The canvas resolution is capped at 1.5x device pixel ratio to keep it smooth on high-density screens.

## Browser support

Current Chrome, Edge, Firefox and Safari. MathML rendering for the formula needs a recent version (Chrome and Edge 109 or later).

## Credits

Author: G.Nitesh ([@darksoulxb](https://github.com/darksoulxb)), School of Engineering & Technology, Om Sterling Global University.

