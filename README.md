# ASTR 3900/8090 — Interactive Demos

A growing set of self-contained, browser-based demos built to accompany
**ASTR 3900/8090: General Relativity & Cosmology** at Vanderbilt University.
Everything is static HTML — no install, no server, no build step.

**Live site:** https://stevertaylor.github.io/astr3900-demos/

## The demos

| Demo | Lecture | Topic |
|------|---------|-------|
| **Gravity as Geometry** | 1 | From universal free fall to an invariant spacetime interval. |
| **Special Relativity: Spacetime Geometry** | 2 | Worldlines, simultaneity, Lorentz boosts, and the twin trip. |
| **Four-Vector Explorer** | 3 | Four-vectors, Lorentz transformations, relativistic Doppler shift, aberration, and beaming. |
| **Gravitational Time Dilation & Redshift** | 4 | Photon redshift and clock slowing in a gravitational well; weak-field vs. exact GR. |
| **Two Effects, One Clock** | 5 | Special-relativistic time dilation vs. gravitational redshift — GPS and the Hafele–Keating experiment. |
| **The Alcubierre Warp Drive** | 6 | Tip the light cones yourself: coordinate speed past c without outrunning the local light cone. |

More lectures and demos are added as the semester progresses (up to ~24 lectures).

## Structure

```
index.html                                  ← the hub (landing page + iframe launcher)
lecture-01-geometry/index.html
lecture-02-spacetime/index.html
lecture-03-four-vectors/index.html
lecture-04-gravitational-redshift/index.html
lecture-05-gps-hafele-keating/index.html
lecture-06-light-cones-warp-drive/index.html
```

The hub hosts exactly one demo in an `<iframe>` at a time and tears it down on
exit, so only one live rendering context / animation loop is ever running —
memory and CPU stay flat.

## Adding a new lecture's demo

1. Drop a self-contained `lecture-NN-slug/index.html` into the repo.
2. Add **one** entry to the `DEMOS` array in the root `index.html`:

   ```js
   {
     id:'l07-slug',
     title:'My New Demo',
     tag:'Lecture 7',
     accent:'#5ec8e6',
     path:'lecture-07-slug/index.html',
     blurb:'One or two sentences describing it.'
   },
   ```

3. Commit and push. It's live in ~30 s.

Keep each demo a single `index.html`. These demos have no external
dependencies (no CDN, no build step) — if a future one needs a library,
prefer vendoring it locally so the site stays usable offline.

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000/
```

(Opening `index.html` directly via `file://` can break the iframes in some
browsers — use the local server.)
