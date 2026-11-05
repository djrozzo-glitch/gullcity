# Gull and the City 🐦

A cozy, slightly absurd, endlessly scrolling browser game. Fly above a hand-painted European city, release a falling stream, and aim for pedestrians or cars.

**Playable prototype:** v0.2 · Pure HTML5 Canvas + JavaScript · No build step or dependencies.

## Play

- **Click / tap / Space** — release a stream of falling droplets
- **P** or **Pause** — pause / resume
- **Sound** — toggle synthesized sound effects
- **Bald pedestrian** +5 · **Other pedestrian** +2 · **Car** +1

No time limit or game over.

## Run locally

Open `index.html` in a browser. For a local HTTP server (optional):

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000/ .

## Publish on GitHub Pages

1. Create a new public GitHub repository, e.g. `gull-and-the-city`.
2. Upload **the files and folders from this package directly into the repository root** (not the outer folder). `index.html` must be at the root.
3. Commit your changes to `main`.
4. In the repository, open **Settings → Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**, then `main` and `/ (root)`. Save.
6. Once deployed, visit `https://YOUR-USERNAME.github.io/gull-and-the-city/` (assuming the repository has that name). GitHub displays the final URL in **Settings → Pages**.

Relative asset paths work both at a GitHub Pages subpath and at a custom domain. The `.nojekyll` file prevents Jekyll processing.

### Or push from Terminal

```bash
git init
git add .
git commit -m "Initial playable release v0.2"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/gull-and-the-city.git
git push -u origin main
```

Create the empty repository on GitHub before pushing; do not initialize it with a separate README if using these commands. GitHub authentication uses a signed-in credential manager, SSH, or a personal access token, not your account password.

## Files

- `index.html` — game and styling
- `favicon.svg` — website tab icon
- `assets/backgrounds/` — four parallax scenery layers
- `assets/gull/` — 12 individual seagull poses
- `assets/people/` — eight pedestrians
- `assets/cars/` — eight vehicle images
- `assets/props/` — street props
- `assets/fx/` — visual feedback effects
- `assets/sheets/` — original source sprite sheets for future editing

## Known limitations

This is a first playable prototype. Pedestrians use subtle bobbing instead of walk-cycle frames, panorama seams may be visible on repeats, and falling droplets use simplified gravity rather than full fluid dynamics. AI-generated sprites may have minor cropping artifacts.

## License

No license has been selected yet. All rights reserved until the owner chooses one.

## v0.3 corrections
- Pedestrians aligned with sidewalk and animated using four procedural stride frames per character.
- Seagull uses a safe, cleaned flight sequence; stray fragments removed.
- High contrast comic-style score popups for hits.

## v0.4 corrections
- Seagull frames normalized onto a common canvas to avoid nose clipping/jumping.
- Pedestrian baseline tied to the street layer instead of the old abstract floorY.
- Street is rendered in two passes: base + front overlay so pedestrians and gull sit between scene layers.
- Gull now glides with gentle depth motion between the pedestrian plane and the cars.

## v0.5 — Lane & layering overhaul

- Distant skyline repositioned behind the roofline, eliminating the floating city strip.
- Removed the duplicated foreground street render that covered NPCs with repeated
  trees, benches, fountains and flowerbeds.
- Pedestrian baseline tied to the stone sidewalk, and pedestrian sprites reduced.
- Car sprites reduced and aligned to the road.
- Seagull moves automatically between two visibly different flight heights.
  It stays on each lane, then transitions smoothly for 1.65 seconds.
- Streams have a lane locked at release: sidewalk streams only score on people,
  road streams only score on cars. All other collisions are ignored.
- Lane readout displayed in HUD.
- No npm or server required. Commit files at repository root for GitHub Pages.

## v0.6 perspective + head-hit update
- Gull scale now changes more dramatically by lane: smaller over pedestrians, larger over cars.
- Streams inherit lane perspective too: smaller and lighter in the pedestrian lane.
- Pedestrian scoring now uses a head hitbox. When a stream reaches a pedestrian's head, the whole stream stops immediately.

## v0.7 crowd + traffic tuning
- Streams released from the pedestrian lane now terminate at sidewalk level if they miss.
- Cars are visually larger but spawn less frequently.
- Pedestrians are fewer on screen.
- Pedestrians are flipped so they face their movement direction instead of moonwalking backwards.

## v0.8 — Roof impacts and foreground occlusion
- A separate `street_front.png` layer holds lamp posts and bollards, allowing
  pedestrians to walk behind them while the rest of the street stays stationary.
- People are shifted farther down onto the sidewalk.
- Bald pedestrian spawn chance increased to 31%.
- Car-lane streams hit the top of cars, stop on impact, and splash on the roof.
- Missed car-lane drops end with a splash on the road.

## v0.9 — Precise foreground occlusion masks
- Rebuilt foreground mask in original street-image coordinates.
- Each of eight bollards and both streetlamps has its own tightly fitted silhouette.
- Front layer and base street share exact scroll, flip and size parameters.
- Reduced pedestrian vertical bob so feet stay grounded.
