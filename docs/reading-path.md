# 📚 Reading Path

This path is for engineers and researchers who want to understand simulation-ready asset generation without drowning in generic 3D generation papers.

## 0. Start with the Definition

Understand the core distinction:

```text
visual 3D asset ≠ simulation-ready physical asset
```

A sim-ready asset needs geometry, articulation, physical properties, simulator format, and validation.

## 1. Learn the Substrate

Start with datasets and simulators because they define the output space.

- SAPIEN / PartNet-Mobility
- AKB-48
- GAPartNet
- Objaverse / Objaverse-XL

Questions to ask:

- What parts are annotated?
- Are joint axes and limits available?
- Are physical properties provided or guessed?
- Which simulator is assumed?

## 2. Study Image-to-URDF and Articulation Pipelines

Read early and representative pipelines:

- URDFormer
- Real2Code
- Articulate-Anything

Questions to ask:

- Does the method output an executable representation?
- Is articulation predicted directly, generated as code, or recovered through optimization?
- Where can self-correction happen?

## 3. Study Single-Image / Mesh-to-Articulated Asset Generation

Then move to methods that generate or decompose articulated assets:

- SINGAPO
- DreamArt
- PAct
- Particulate
- Articulate AnyMesh
- SIMART

Questions to ask:

- Is the input image, mesh, video, or multi-view observation?
- Are parts generated separately or segmented after generation?
- Can the output become URDF/MJCF/USD, or is it only a visual articulated demo?

## 4. Add Physics and Materials

After geometry/articulation, study physical grounding:

- PhysX-3D
- SOPHY
- PhysDreamer
- PhyCAGE
- DSO

Questions to ask:

- Which physical properties are estimated?
- Are values measured, predicted, defaulted, or optimized?
- Is a simulator in the loop?
- What validation proves physical soundness?

## 5. Study End-to-End Sim-Ready Systems

Now read integrated systems:

- PhysX-Anything
- SIMART
- EmbodiedGen asset generation pipelines

Questions to ask:

- What representation passes through the model?
- Where is the token bottleneck?
- What is generated vs deterministically lowered/exported?
- Which simulator actually runs the output?
- What breaks on long-tail objects?

## 6. Build an Engineer's Mental Model

Use this stack:

```text
input → perception/reasoning → part/physics representation → geometry refinement → simulator lowering → validation
```

Map every paper to the stage it strengthens. Most papers do not solve the whole pipeline.

## 7. When Adding a New Paper

Place it by the missing piece it solves:

- pretty mesh but no joints → articulation
- joints but poor part geometry → part-aware generation/refinement
- geometry but no material → physical property grounding
- format export but unstable sim → validation/alignment
- too little data → procedural/data synthesis
