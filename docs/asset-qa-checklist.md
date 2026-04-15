# ✅ Asset QA Checklist

This checklist separates **looks good** from **simulates well**.

## Stage 0 — Visual Asset

Use this stage for meshes or generated objects that are not yet simulator-ready.

- [ ] Geometry is complete enough for the target task.
- [ ] Object scale is at least roughly known.
- [ ] Texture/material appearance is plausible, if needed.
- [ ] Thin structures, handles, hinges, and contact surfaces are not obviously broken.

Exit criterion: the asset is worth converting, but not yet trusted in simulation.

## Stage 1 — Importable Asset

- [ ] Asset file parses in the claimed simulator/toolchain.
- [ ] Mesh paths resolve from the asset description file.
- [ ] Units are documented: meters, centimeters, arbitrary scale, or unknown.
- [ ] Origins and transforms are not obviously offset or rotated.
- [ ] Visual meshes and collision meshes are both accounted for.
- [ ] Textures/material references do not break import.

Exit criterion: the simulator can load the asset without immediate errors.

## Stage 2 — Kinematically Usable Asset

For articulated objects:

- [ ] Link hierarchy matches the semantic parts.
- [ ] Joint type is plausible: revolute, prismatic, fixed, continuous, etc.
- [ ] Joint axis is in the correct frame.
- [ ] Joint limits are plausible and do not invert the motion.
- [ ] Parent/child frames are consistent.
- [ ] Moving parts do not immediately interpenetrate static parts.
- [ ] Default joint states are valid and resettable.

Exit criterion: the object moves like the intended object class.

## Stage 3 — Physically Stable Asset

- [ ] Mass is defined or derived from documented assumptions.
- [ ] Inertia is valid and not singular/absurd.
- [ ] Collision meshes are simplified enough for stable contact.
- [ ] Collision meshes align with visual geometry.
- [ ] Friction/damping/restitution assumptions are explicit.
- [ ] Asset remains stable under gravity for a basic drop/settle test.
- [ ] Articulated joints do not explode under simple actuation.
- [ ] Solver/contact parameters are documented if non-default values are required.

Exit criterion: the asset does not only load; it can survive basic physics.

## Stage 4 — Task-Useful Asset

- [ ] A planner or policy can interact with the asset repeatedly.
- [ ] Reset states are deterministic or intentionally randomized.
- [ ] Task-relevant affordances are represented: handles, lids, buttons, wheels, drawers.
- [ ] Contact-rich interaction does not fail due to collision artifacts.
- [ ] Success/failure can be measured automatically.
- [ ] Randomization ranges are documented.
- [ ] Known failure modes are recorded.

Exit criterion: the asset can support experiments, not just demos.

## Minimum Metadata to Record

For each generated asset, record:

- source input: image/text/mesh/video/scan
- generation method and version
- output format: URDF/MJCF/SDF/USD/mesh/etc.
- simulator target and version
- units and scale assumptions
- physical parameter source: predicted, default, manually set, measured
- validation commands or scripts
- known caveats

## Common Failure Modes

- Mesh loads, but scale is wrong by 10× or 100×.
- Visual mesh is used as collision mesh and causes unstable contact.
- Joint axis is correct in world frame but wrong in local link frame.
- Inertia is missing or numerically invalid.
- Generated handle is visually present but not separated as a movable part.
- URDF imports in one simulator but behaves differently in another.
- Material labels exist, but friction/stiffness values are arbitrary.
