# counter_rotating_rollers_centering_response_reversal

Counter-rotating rollers: the rod drifts away from the centre

## Paired descriptions
True: A horizontal rigid rod rests off-centre on two powered rollers. The roller surfaces move toward the gap between them. After the rollers start, the rod slides back through the centre and begins an ordinary restoring oscillation.

Counterfactual: A horizontal rigid rod rests off-centre on two powered rollers. The roller surfaces move toward the gap between them. After the rollers start, the rod instead slides farther away from the centre without any other drive touching it.

## Mechanics
The rigid rod has one free horizontal coordinate x. The two support normals obey N_L+N_R=g per unit mass. Pitch equilibrium includes the friction couple from the finite rod thickness h. With k_L=mu*tanh((u-v)/epsilon), k_R=mu*tanh((-u-v)/epsilon), N_L=g*(a-x+h*k_R/2)/(2*a-h*(k_L-k_R)/2); acceleration=k_L*N_L+k_R*N_R. Both contacts remain loaded and the rod spans both supports. The drive ramps smoothly and is identical in both branches. The only changed law is mu_CF=-0.15*mu. This is negative kinetic friction, not a hidden lateral motor. Ordinary assumptions are horizontal-planar motion, rigid contacts and low-speed regularized friction. Surface rotation marks show the actual drive direction. A fixed painted mark on the base supplies a spatial reference. Numerics use RK4, 20 internal steps per video frame; no time rescaling.

Operator: `negative_kinetic_friction_after_drive_start`. Mask targets: rigid rod and attached painted centre mark. Only the visible depth-tested surfaces of these objects are white, from the first changed frame to clip end. Other moving driven parts remain black.

See `DESIGN.md` for model boundaries and review evidence requirements.

## Runtime and output
Python 3.11 on Linux, official pinned requirements. Blender 4.5.3 Workbench renders saved 3D states; it is not the physics solver. Install with `python -m pip install -r requirements.txt`.

Native output is 2048×2048, 24 fps, 120 frames / five seconds. The --smoke profile is 512 and never formal acceptance. Four lossless RGB H.264 streams: True, Counterfactual, strict binary object-only mask and exact pure-red overlay. Shadows are disabled. Compatible 1024 browser derivatives are clearly labelled. Physical/source time equals video time; internal solver steps are documented in metadata.

```sh
python -m pytest -q tests
python examples/generate.py --seeds 42,98 --num-cases 2 --output /absolute/new-output
python examples/audit.py --case /absolute/case
python examples/reproduce.py --case /absolute/case --output /absolute/rebuilt
python examples/compare.py /absolute/case /absolute/rebuilt-case
python examples/audit_scaling.py . --samples 100000 --output /absolute/scale.json
python examples/probe_axes.py --output /absolute/new-axis-probes
```

## Scaling and safety
CGC-v1 target: 100000 accepted cases in a one-million-profile bijective domain. Six independent axes cover geometry length, physical response, release/event timing, secondary geometry, appearance and viewpoint. Nuisance variables are shared within pairs. --shard-id/--num-shards gives disjoint streams; --resume validates the exact code/dependency/header identity and all accepted hashes. Rejections and interrupted writes are retained. Static 100k is not 100k rendered videos.

Recorded-state reproduction replays both saved full trajectories and does not rerun the solver. Each copied directory is independent and carries procedural assets, requirements, CLI and tests. No generated data is committed. Back up every retained artifact and SHA256 manifest before stopping compute.

## Review status
Implementation candidate. No source-only or smoke result is a formal PASS. Prepare two materially different native representative cases with exact-head runtime witnesses, decoded audits, independent mechanics/object-identity checks, rendered axis evidence and browser playback before declaring self-check complete. No Sara application is submitted by generation.
