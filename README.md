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
