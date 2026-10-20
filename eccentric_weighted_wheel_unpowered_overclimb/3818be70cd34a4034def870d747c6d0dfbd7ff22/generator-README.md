# eccentric_weighted_wheel_unpowered_overclimb

Eccentric wheel: uphill rolling exceeds its available gravitational energy

## Paired descriptions
True: A wheel with a visible fixed off-centre metal weight is released from rest on a gentle incline. The wheel initially rolls uphill while its combined centre of mass descends. It reaches a turning point and rolls back toward a lower-energy position.

Counterfactual: A wheel with a visible fixed off-centre metal weight is released from rest on a gentle incline. The wheel initially rolls uphill while its combined centre of mass descends. Without a drive, it continues uphill beyond its passive turning range, raising its combined centre of mass above its release height.

## Mechanics
The wheel is one rigid planar assembly with a fixed ballast and no-slip rolling coordinate theta; travel s=s0+R*theta. The ballast phase is alpha=alpha0+theta. With tangent t=(cos(beta),0,sin(beta)) and normal n=(-sin(beta),0,cos(beta)), the axle is C=origin+t*s+n*R and ballast displacement is d*(sin(alpha)*t+cos(alpha)*n). Combined eccentricity e=m_ballast*d/m. Effective inertia M(theta)=I_geo+m*R^2+2*m*R*e*cos(alpha), potential U=m*g*(R*theta*sin(beta)+e*cos(alpha-beta)). Passive equation: M*theta_ddot+0.5*M_prime*omega^2+U_prime+damping*omega=0. The normal branch has no positive input work and can initially climb while COM descends. CF starts only after the first COM-potential minimum and applies a single unpowered generalized torque that tracks a positive angular speed; rolling and rigid geometry remain intact. The evidence requires rising above release potential and beyond the entire passive turning range. This is a reduced mechanics model, not Blender dynamics. Ideal static friction supplies rolling without work; independent checks must confirm positive normal reaction and a feasible finite friction demand. The narrow ballast has steel-like density 7800 kg/m^3 and is offset in depth to clear the spokes; a bracket and axial mount make the fixed connection visible. Planar symmetry/support is assumed.

Operator: `unpowered_uphill_servo_torque`. Mask targets: the rigid wheel, fixed ballast, spokes, axle and painted marks. Only the visible depth-tested surfaces of these objects are white, from the first changed frame to clip end. Other moving driven parts remain black.

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
