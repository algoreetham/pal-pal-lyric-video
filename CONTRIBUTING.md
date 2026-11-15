# Contributing to Pal Pal Kinetic Lyric Video

We welcome contributions, enhancements, and new animation styles for this lyric video project!

---

## Development Workflow

1. **Fork & Clone**:
   ```bash
   git clone https://github.com/algoreetham/pal-pal-lyric-video.git
   cd pal-pal-lyric-video
   ```

2. **Run Local Dev Preview**:
   ```bash
   npx --yes hyperframes@0.8.143 preview
   ```
   Or open `preview.html` directly in your browser.

3. **Verify Changes**:
   Before committing, run the automated lint, motion, and contrast validation check:
   ```bash
   npx --yes hyperframes@0.8.143 check --json
   ```

---

## Code & Animation Guidelines

- **Subpixel GPU Transforms**:
  Always animate hardware-accelerated transforms (`x`, `y`, `scale`, `rotation`, `opacity`). Never animate layout or text reflow properties like `letter-spacing`, `line-height`, or `font-size` with GSAP, as they snap to integer pixels and stutter during frame-by-frame rendering.

- **Deterministic Mathematics**:
  Never use `Math.random()` inside animations or procedural generators. Always use a seeded PRNG or trigonometric functions (e.g. `Math.sin(t * constant)`) so every frame produces the identical pixel output on every render pass.

- **Master Timeline Scoping**:
  Always add tweens to the master GSAP timeline registered on `window.__timelines["main"]` so the Hyperframes seek engine drives all visual elements in synchronization.

- **WCAG Contrast**:
  Ensure text remains legible and maintains at least 3:1 contrast against dynamic backgrounds. Intentional inversions using `mix-blend-mode: difference` should be verified via `snapshots/contact-sheet.jpg`.

---

## Submitting Pull Requests

1. Create a feature branch (`git checkout -b feature/cool-animation`).
2. Commit your changes with Conventional Commit messages (`feat:`, `fix:`, `docs:`).
3. Push to your branch and open a Pull Request.
