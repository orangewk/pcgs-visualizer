# AGENTS.md — Instructions for Codex / Coding Agents

## Project stance

This repository is a conceptual and visualization project. It translates quantum-state ideas into 3D Gaussian Splatting vocabulary plus phase arrows. It is not a claim of completed new physics.

Use conservative language. Preserve the distinction between:

- representation / translation frame
- toy simulation
- physical derivation
- ontology

## Terminology rules

Prefer:

- “phase arrow” for complex phase.
- “density render” for \(P=|\Psi|^2\).
- “event render” for sampling one observation from \(P\).
- “accumulation” for repeated samples approaching the distribution.
- “decoherence knob” for toy suppression of interference terms.
- “hidden physical dimension” only for extra spatial dimensions.
- “internal gauge fiber” for gauge charges.
- “spin/local-frame fiber” for spin-related structure.
- “configuration/Hilbert space” for quantum state space.

Avoid:

- “hidden dimension” without specifying which kind.
- “derives the standard model.”
- “proves reality is splats.”
- “solves measurement.”

## Code style

- Keep the simulator dependency-light.
- Use vanilla JS unless a framework is explicitly requested.
- Separate math, rendering, sampling, and UI logic.
- Add comments where formulas are implemented.
- Keep canvas rendering readable over clever.
- Avoid build systems unless necessary.

## Documentation style

- Japanese is the primary language.
- Keep sections short.
- State what is being claimed and what is not.
- Include equations where they clarify the rendering pipeline.
- Add diagrams or ASCII sketches if helpful.

## Review checklist

Before finalizing changes, verify:

- [ ] Local HTML opens without a build step.
- [ ] Sliders are labeled consistently with the docs.
- [ ] Sampling does not mutate probability normalization incorrectly.
- [ ] Coherence \(\lambda\) only suppresses the interference term in the toy formula.
- [ ] Hidden-space docs distinguish physical dimensions from internal fibers.
- [ ] No overclaiming as physics.

