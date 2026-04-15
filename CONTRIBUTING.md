# Contributing to Awesome Sim-Ready 3D Asset Generation

Thanks for helping make this list useful. The goal is not to collect every 3D paper; the goal is to help engineers find work that moves assets closer to real simulation use.

## Inclusion Criteria

A resource should contribute to at least one sim-ready dimension:

- `[G]` **Geometry** — mesh, part mesh, Gaussian/implicit geometry, collision geometry.
- `[A]` **Articulation** — part hierarchy, joint type, axis, limits, kinematic graph.
- `[P]` **Physical properties** — scale, mass, inertia, friction, materials, damping, stiffness, stability.
- `[F]` **Simulator format** — URDF, MJCF/XML, SDF, USD, or simulator-specific packaging.
- `[V]` **Validation** — import, stability, joint motion, contact behavior, or policy/planner usability.

Good additions include:

- papers/projects that output simulator-facing files,
- datasets with articulated or physical annotations,
- tools that convert, validate, or repair assets,
- evaluation methods for physical plausibility or simulator usability,
- engineering guides around URDF/MJCF/SDF/USD/collision geometry.

Usually out of scope:

- pure visual 3D generation with no simulation relevance,
- rendering-only NeRF/3DGS work without physical asset output,
- generic robot-policy papers that do not introduce reusable assets, datasets, simulators, or validation methods,
- links with no project/paper/code context.

## Entry Format

Use this compact format in `README.md`:

```markdown
- **[YEAR] Resource Name** `[G][A][P][F][V]` 🌐🛠️📦
  One-line summary.
  Links: [paper](...) · [project](...) · [code](...) · [data](...)
  *Why engineers care:* concrete utility for sim-ready asset pipelines.
  *Caveat:* known limitation, missing validation, license concern, or scope boundary.
```

Availability labels:

- 🧪 paper-only
- 🌐 project page / demo
- 🛠️ code available
- 📦 data / checkpoints / assets
- 🤖 simulator-validated or simulator-facing evidence
- 🧾 license/provenance worth checking
- ⭐ representative / must-read

Keep capability tags as bracket tokens (`[G][A][P][F][V]`) rather than emojis. They are easier to grep, sort, lint, and migrate into structured metadata later. Emojis are reserved for availability/importance signals.

## Quality Bar

Before opening a PR, check:

- Does the entry explain the input and output?
- Does it identify the simulator-facing format, if any?
- Does it avoid overstating sim-readiness?
- Are caveats included when validation is weak?
- Are links stable and official when possible?
- Is the item placed in the most useful section, not just the newest section?

## Suggested PR Types

- Add a new resource.
- Correct metadata or caveats for an existing resource.
- Add a simulator/tooling guide.
- Improve the validation checklist.
- Add license/provenance notes.

## Style

- Prefer concise, engineer-facing summaries.
- Avoid hype words unless backed by evidence.
- Use official project/code/paper links when available.
- Do not copy abstracts wholesale.
- Keep the README navigable; move long explanations into `docs/`.
