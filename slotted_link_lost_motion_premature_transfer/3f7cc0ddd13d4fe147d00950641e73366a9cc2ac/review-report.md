# PR #728 generator self-review

**Decision:** NOT VERIFIED — browser playback and final visual inspection pending

**Reviewed head:** `3f7cc0ddd13d4fe147d00950641e73366a9cc2ac`
**Generator:** `slotted_link_lost_motion_premature_transfer`
**PR:** https://github.com/hipo-dev/counterfactual-data/pull/728
**Runtime policy scope:** NEW / REPLACEMENT
**Generator correctness:** NOT VERIFIED (final visual/playback review pending)
**Runtime provenance:** PASS
**Declared scaling target:** 100,000 accepted cases
**Declared-target scale readiness:** PASS under the explicit reduced model and parameter domain; static and rendered evidence are separate.
**Production readiness:** NOT READY until browser/visual verification completes

No Sara form has been filled or submitted. This is a contributor self-check, not Sara approval or a GitHub approval review.

## Blocking findings

Browser playback, seeking, public HTTP integrity and final visual inspection are still pending. self_check_complete remains false.

## Six-gate result

| Gate | Result | Evidence |
|---|---|---|
| Output contract | PASS | Two native 2048×2048 / 24fps / 120-frame / five-second cases; all four streams decoded in full; metadata, raw and encoded hashes |
| Violating-object-only mask | PASS | Every native mask frame is binary, matched to a reviewer-selected object whitelist projection; no shadows; overlay changes only white-mask pixels to pure red |
| Real scaling | PASS | 100,000 CPU-only profile/signature audits; six independently wired axes; 13 controlled rendered recipes; two materially different formal seeds; sixteen physical corners and 100 further trajectory samples |
| Official unpatched environment | PASS | Official pinned Python wheels, exact install versions and actual runtime witnesses; installed source/native RECORD hashes; rebuilt bytecode verified compiler-equivalent |
| Decoded matched control | PASS | Exact decoded RGB prefix, identical ordinary input/camera conditions, one declared operator, exact frame-hash reproduction |
| Semantic consistency | NOT VERIFIED (final visual inspection pending) | Names, title, README, independent prompts, scoring, operator, stored state, native decoded frames and browser playback |

## Production-quality behavior and prompt alignment

The normal pin traverses the open slot before touching and pushing its end. CF makes the whole output frame follow while the pin stays in the open centre. The four feet remain connected to the frame and the bearing collars stay on their rails. The driver shaft seats inside its housing; the input pushrod stays below the output.

The True and CF descriptions are independent and contain no seed, sampled incidental color, source revision, simulator name or cross-reference shortcut. Both submitted seeds must complete the same stated outcomes under their different dimensions/response/timing/view. The only declared CF error is the registered operator; ordinary downstream effects retain the common equations/contact solver.

Full-clip visual confirmation: pending; decoded mechanics and selected-frame geometry evidence already exist.

## Timebase and playback integrity

Video samples are t=f/24 seconds. Physical/source seconds per video second is 1.0 in both branches. Internal solver steps are explicitly distinct from the one recorded outer sample: 20 for the roller, Arago and Bullet models; 40 for the wheel; the quasi-static slot evaluates its prescribed displacement once per sample. No branch-specific slow/fast mapping is used. A small shared camera drift does not alter trajectory time.

## Simulator and motion-authority claim

The front four generators use the documented reduced analytical/integrated/kinematic models. Blender Workbench only renders stored states. Sliding supports uses official PyBullet 3.2.7 for native contact/gravity/friction and one explicit CF force, with passive X/Z/Y joints. Its exact native state resimulation is checked separately when applicable. No Genesis, MuJoCo, field-solver, photorealism or fully unconstrained 3D-native claim is made.

## Semantic matrix

| Surface | Binding |
|---|---|
| Generator name / title | Actual registered phenomenon and source directory |
| README / design | Exact model, assumptions, single operator and paired descriptions |
| Prompts | Each states its own setup and completed branch outcome |
| Scoring | Current registered operator and the two same branch statements |
| Metadata / saved trajectories | Exact source head, recipe, clock, evidence and input controls |
| Video / mask / overlay | Full decoded verification plus native object-identity replay |

## Successful-render provenance and reproduction

- Every accepted case maps to exactly one successful witness; the fail-closed index contains exactly seeds 42 and 98.
- The witness binds clean source commit, command, seed set, lock, actual interpreter/packages/OS, T4 OpenGL renderer/driver, encoder executable/hash/version and all submitted artifact hashes.
- Official bpy is a module in the same Python process; no separate embedded Python is claimed.
- Source and runtime component records distinguish install instructions from the actual successful run.
- One complete native seed 42 case per generator was independently replayed from the saved states through its own witness. All four streams match every original raw/decoded frame hash exactly. This is a newly witnessed reproduction, not historical-runtime evidence.
- Compatible 1024px browser streams are labelled derivatives; the native originals remain separately published with full SHA256 bindings.

## Client-facing artifacts

Binary masks display white-on-black. All overlays use pure red. Browser RGB/overlay derivatives are lossy yuv420p copies; the nearest-scaled browser mask is decoded strict binary. Native RGB ground truth is lossless libx264rgb CRF0. Public original assets have GitHub server digest confirmation. HTTP checks bind every browser stream to its local hash; real browser tests verify loaded dimensions, full playback to five seconds and seeking through the end.

Client playback status: NOT VERIFIED.

## Scale-readiness result

- Target 100,000; audited 100,000 static samples. This is not 100,000 rendered cases.
- Profile space is 1,000,000; a bijection gives deterministic unique seed/profile mapping.
- Primary axes are geometry length, response, onset and secondary geometry; appearance and camera view are shared nuisances.
- Canonical checker is a byte-identical copy of dev `standards/cgc_v1/audit_scaling_contract.py`, SHA256 `db2d7ea12040139f9e683e08f04bf050e2e668e66270fb9a428e0d9c3cee8764`.
- Static acceptance rate is 1.0; bucket coverage and all disjoint shard details are retained in scale.json.
- Every low/high axis probe recomputes its derived parameters and changes final geometry or trajectory pixels with all other base inputs held fixed. axis-probes.json records exact recipes, image hashes and effects.
- The two formal recipes differ on multiple physical and nuisance axes; no label-dependent incidental setup or timebase is introduced.
- Atomic writes, rejection records, manifest-bound resume, incompatible-resume rejection and disjoint seed streams are checked. Interrupted outputs are preserved rather than silently accepted.

## Commands and artifacts checked

Compile, design tests, CLI help, two native seed generation through run_with_provenance, 100k canonical scaling, controlled 768px PNG probes, extra trajectory population, independent full decoded audit, all-frame native identity replay, saved-state reproduction and exact hashes, witness audit/index, safe/incompatible resume, official-wheel integrity, public assets and browser playback. See linked JSON files for exact commands, runtimes, sizes, hashes and per-case metrics.

## Limits and re-review

Only two cases per generator are formal rendered acceptance evidence. The sixteen physical corners and 100 further samples are trajectory-only checks. The 100k audit is static. The 13 controlled PNG recipes demonstrate axis attribution, not 13 additional formal videos. Model idealizations are explicit in DESIGN.md. Any source-head or delivered-media change requires affected regeneration and the applicable exact-head checks again. No merge or Sara submission is authorized by this report.
