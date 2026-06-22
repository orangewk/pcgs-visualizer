# TASKS — PCGS / Complex Gaussian Splat Cloud

## Phase 0 — Repository hygiene

- [ ] Rename project if needed: `pcgs-visualizer` or `complex-gaussian-splat-lab`.
- [ ] Keep source notes under `/docs/source-notes/`.
- [ ] Put public-facing docs under `/docs/`.
- [ ] Keep simulator code outside monolithic HTML when refactoring.

## Phase 1 — Static simulator refactor

Goal: turn `pcgs_toy_simulator.html` into a maintainable static site.

- [ ] Create `/index.html`.
- [ ] Create `/src/math.js` for Gaussian/complex arithmetic/probability functions.
- [ ] Create `/src/sampling.js` for event sampling and histogram accumulation.
- [ ] Create `/src/render.js` for canvas drawing.
- [ ] Create `/src/ui.js` for sliders/buttons.
- [ ] Preserve existing functionality from `pcgs_toy_simulator.html`.
- [ ] Add reset samples button.
- [ ] Add export PNG button if easy.

Acceptance:

- Opening `index.html` locally works.
- Sliders update density render interactively.
- Event samples accumulate visibly.
- Coherence knob removes interference smoothly.

## Phase 2 — Simulation grammar page

Goal: make the concept readable without the original conversation.

- [ ] Add a short section explaining `density render`:

```math
P(x)=|\Psi(x)|^2
```

- [ ] Add a short section explaining `event render`:

```math
x_{obs}\sim P(x)
```

- [ ] Add accumulation:

```math
\hat P_N\to P,\quad noise\sim 1/\sqrt N
```

- [ ] Add decoherence knob:

```math
P_\lambda=|\psi_1|^2+|\psi_2|^2+2\lambda\mathrm{Re}(\psi_1^*\psi_2)
```

Acceptance:

- A reader can understand what the simulator is showing without reading the full note.

## Phase 3 — Hidden spaces page

Goal: prevent conceptual confusion around “hidden space.”

- [ ] Add table distinguishing:
  - hidden physical dimensions
  - internal gauge fiber
  - spin/local-frame fiber
  - configuration/Hilbert space
  - renderer/cognitive latent space
- [ ] State clearly that Planck-length compactification applies mainly to hidden physical dimensions.
- [ ] State that internal gauge fiber is not automatically an extra physical space direction.
- [ ] State that spin is not simply a small hidden spatial loop.

Acceptance:

- The document no longer uses “hidden dimension” ambiguously.

## Phase 4 — Hidden coordinate projection toy model

Goal: visualize marginalization.

Implement a toy 2D amplitude \(\Psi(r,y)\), where `r` is visible and `y` is hidden.

- [ ] Draw 2D heatmap of \(|\Psi(r,y)|^2\).
- [ ] Draw projected 1D distribution:

```math
P_{vis}(r)=\int dy\,|\Psi(r,y)|^2
```

- [ ] Add hidden width / hidden mode controls.
- [ ] Add note: this is a toy model, not evidence for physical extra dimensions.

Acceptance:

- Changing hidden structure changes visible projection in a legible way.

## Phase 5 — Documentation polish

- [ ] Add `docs/limits.md` with explicit non-claims.
- [ ] Add `docs/glossary.md`.
- [ ] Add `docs/claim-levels.md`.
- [ ] Ensure the project can be read as a translation framework, not a physics proof.

## Non-claims to preserve

Do not write that:

- The project proves the world is literally made of Gaussian splats.
- The project derives the standard model.
- Electric charge, spin, and color are proven to be extra-dimensional windings.
- Born rule is derived.
- Measurement problem is solved.

Acceptable wording:

- “This frame reads X as Y.”
- “This is a toy visualization.”
- “This is analogous to…”
- “This should not be read as a physical derivation.”

