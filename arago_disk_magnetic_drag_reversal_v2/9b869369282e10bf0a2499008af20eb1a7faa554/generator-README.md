# arago_disk_magnetic_drag_reversal

Arago disk: the suspended magnet rotates against the copper disk

## Paired descriptions
True: A motor turns a copper disk beneath a freely rotating bar magnet mounted on a separate overhead pivot. An air gap separates the disk and magnet. The magnet gradually rotates in the same direction as the disk through electromagnetic induction.

Counterfactual: A motor turns a copper disk beneath a freely rotating bar magnet mounted on a separate overhead pivot. An air gap separates the disk and magnet. Without another drive, the magnet instead rotates continuously opposite to the disk.

## Mechanics
A motor rotates the conductive disk about a vertical shaft. A separate overhead bearing supports the freely yawing two-pole magnet with a visible air gap above the disk. The generator uses a reduced electromagnetic drag model, not a field solver: I*omega_dot=k*(Omega-omega)-d*omega, d=3*k, I=0.2*L^2/12. In Counterfactual only k in the magnetic coupling term changes sign; ordinary bearing damping d stays positive and unchanged. The motor disk trajectory is shared. Integrate the magnet and disk angles at 20 RK4 steps per frame. Magnet rotation is visible from its red/blue poles and top marks. Do not infer direction from the final angle alone. This idealization ignores vertical force/tilt because the independent bearing constrains those coordinates. No water, refraction or optical effect is used.

Operator: `reverse_eddy_current_drag_torque`. Mask targets: the rotating bar magnet and its rotating central clamp. Only the visible depth-tested surfaces of these objects are white, from the first changed frame to clip end. Other moving driven parts remain black.

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
