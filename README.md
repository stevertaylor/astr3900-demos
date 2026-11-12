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
| **Light Cones and the Warp Drive** | 6 | Tip the light cones yourself: coordinate speed past c without outrunning the local light cone. |
| **Coordinate and Orthonormal Bases** | 7 | Coordinate basis vectors stretch and degenerate on a plane, a sphere and a Schwarzschild slice; the orthonormal frame stays unit length. |
| **Why the Ball Goes as High as It Does** | 8 | Extremal aging: the free-fall path between two events is the one with the most proper time. |
| **Can You Get Through the Wormhole?** | 9 | Geodesics on a wormhole and the critical angular momentum for passing through. |
| **Conserved Quantities and Broken Symmetries** | 10 | Metric symmetries, Killing vectors, and what is lost when the mass varies in t or φ. |
| **Falling In: Two Clocks** | 11 | A radial plunge on the faller's clock and on a distant clock. |
| **Schwarzschild Orbit Explorer** | 12 | The effective potential: circular, precessing, scattering and plunging orbits. |
| **Perihelion Precession** | 13 | Exact Schwarzschild orbits precess; test 6π(M/ℓ)² from the last stable orbit out to S2, the Hulse–Taylor pulsar and Mercury. |
| **Photon Orbits and Light Bending** | 14 | Capture vs. escape set by the impact parameter, the photon sphere, and light deflection. |
| **One Spacetime, Two Charts** | 15 | Schwarzschild vs. Eddington–Finkelstein coordinates: light cones tip over at the horizon. |
| **Watching a Star Collapse** | 16 | Exponential redshift and fading seen from far away, or ride the surface through the horizon. |
| **Kruskal Diagram Explorer** | 17 | Light signals between a falling and a static observer on the Kruskal diagram. |
| **Gyroscopes and the Ergosphere** | 18 | Geodetic precession on a circular orbit; frame dragging and the ergosphere of a Kerr hole. |
| **Flat or Curved?** | 19 | Parallel walkers on a plane, cylinder, sphere and saddle: Gaussian curvature sets the drift. |
| **Tidal Stretch and Squeeze** | 20 | Tidal deformation of a falling body, with the tidal tensor read out live. |
| **Densities and Fluxes** | 21 | The number current through spacelike and timelike surfaces; the stress-energy tensor of a boosted fluid. |
| **A Ring of Test Masses** | 22 | A plane gravitational wave on free masses: polarizations, detector strain, transversality. |
| **Kerr Orbit Explorer** | Feature | A 3D map of a spinning black hole: timelike and null geodesics, guided scenes, and a WebXR mode for VR headsets. |

More lectures and demos are added as the semester progresses (up to ~24 lectures).

## Structure

```
index.html                     ← the hub (landing page + iframe launcher)
lecture-NN-slug/index.html     ← one folder per lecture demo (01–22 so far)
kerr-orbit-explorer/index.html ← feature demo (3D, WebGL2)
```

The hub hosts exactly one demo in an `<iframe>` at a time and tears it down on
exit, so only one live rendering context / animation loop is ever running —
memory and CPU stay flat.

## Adding a new lecture's demo

1. Drop a self-contained `lecture-NN-slug/index.html` into the repo.
2. Add **one** entry to the `DEMOS` array in the root `index.html`:

   ```js
   {
     id:'l23-slug',
     title:'My New Demo',
     tag:'Lecture 23',
     accent:'#5ec8e6',
     path:'lecture-23-slug/index.html',
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
