# sliding_supports_weighted_rod_balance_failure

Sliding supports: an unpowered drift prevents weighted-rod balancing

## Paired descriptions
True: A horizontal rod with a fixed weight near one end rests on two identical support pads. The pads slowly slide toward each other. The rod adjusts through friction and the pads finish together beneath its shifted centre of mass, keeping the rod balanced.

Counterfactual: A horizontal rod with a fixed weight near one end rests on two identical support pads. The pads slowly slide toward each other. Without an external push, the rod drifts away from its balancing position and tips down instead of remaining balanced above the closing pads.

## Mechanics
Official unmodified PyBullet 3.2.7 integrates rigid contact, gravity and friction with 20 steps per recorded frame (dt=1/480 s), after a shared 0.5 s settling interval outside the video. An unpowered serial X/Z/Y joint chain retains the planar symmetry of the experiment; all three motors are explicitly disabled. A fixed child link attaches the real ballast collision cylinder and its mass to the rod. Moving massless pads receive identical smooth positions and velocities in both branches. True is supported and converges under the shifted COM. CF adds only one bounded horizontal force pulse with no visible energy source; subsequent separation, sliding and tipping remain native contact dynamics. This force, rather than altered friction or an authored tip animation, is the declared physical error. The renderer reads saved rod-link poses and pad positions. The rendered platform has matching collision geometry; the ground is also collidable. The rod has zero prescribed pose after settling. The planar idealization is explicit and is not a claim of full unconstrained 3D dynamics.

Operator: `unpowered_horizontal_force_during_support_closure`. Mask targets: the rigid rod and its fixed end weight and markings. Only the visible depth-tested surfaces of these objects are white, from the first changed frame to clip end. Other moving driven parts remain black.

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
