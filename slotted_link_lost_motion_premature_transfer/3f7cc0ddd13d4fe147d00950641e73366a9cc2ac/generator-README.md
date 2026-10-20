# slotted_link_lost_motion_premature_transfer

Lost motion: the slot frame moves before the pin touches its end

## Paired descriptions
True: A powered pin starts in the middle of a long open slot in a rail-guided frame. The pin travels through the empty slot while the frame stays at rest. Only after the pin reaches the slot end does it push the frame along its rails.

Counterfactual: A powered pin starts in the middle of a long open slot in a rail-guided frame. As the pin moves, the frame starts following it even though the pin remains in the middle of the slot without touching either end.

## Mechanics
The input pin has smooth prescribed displacement q. A nonpenetrating, one-sided end-stop constraint makes the normal output x=max(q-gap,0): a low-speed quasi-static displacement-controlled mechanism with negligible inertia. The pin begins at the open slot centre; rails hold the frame orientation. In CF only the output law changes to x=q even though the pin stays at the slot centre. This contact-free transfer is the sole impossible behavior. The real open slot, four connected feet and holed rail collars are procedural meshes; this is not a solid bar with a painted fake hole. The input pushrod stays below the frame and never supplies a hidden frame contact. No claim of native dynamics or resolved contact impulse is made.

Operator: `contact_free_slot_frame_transfer`. Mask targets: the rail-guided slot frame, feet and sliding bearing collars. Only the visible depth-tested surfaces of these objects are white, from the first changed frame to clip end. Other moving driven parts remain black.

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
