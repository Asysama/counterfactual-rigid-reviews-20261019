# arago_disk_magnetic_drag_reversal: mechanics and audit contract

A motor rotates the conductive disk about a vertical shaft. A separate overhead bearing supports the freely yawing two-pole magnet with a visible air gap above the disk. The generator uses a reduced electromagnetic drag model, not a field solver: I*omega_dot=k*(Omega-omega)-d*omega, d=3*k, I=0.2*L^2/12. In Counterfactual only k in the magnetic coupling term changes sign; ordinary bearing damping d stays positive and unchanged. The motor disk trajectory is shared. Integrate the magnet and disk angles at 20 RK4 steps per frame. Magnet rotation is visible from its red/blue poles and top marks. Do not infer direction from the final angle alone. This idealization ignores vertical force/tilt because the independent bearing constrains those coordinates. No water, refraction or optical effect is used.

## Source of motion
Quasistatic eddy-current drag torque k*(disk_speed-magnet_speed) and ordinary positive viscous pivot resistance d*magnet_speed. d=3k keeps both signs bounded. Only k changes sign in CF. Ambient magnetic alignment is neglected; this is a phenomenological induction model, not a field solver or native Blender dynamics.

## Temporal/causal contract
The native output has 120 samples at t=f/24 seconds. Onset is sampled independently from geometry and response. All ordinary parameters, motor/support input trajectories and camera motions are shared. The first changed RGB frame is discovered from actual pixels; the mask begins there. The CF operator is reverse_eddy_current_drag_torque. Its consequences do not count as new independent operators.

## Static and rendered scale evidence
The 1,000,000 finite recipes vary four primary physical axes and two nuisance axes. 100,000 unique validated recipes is a CPU-only static target, not a claim of 100,000 rendered outputs. Rendered one-axis perturbations must show real image changes. Corner trajectories and every submitted formal seed must complete the stated outcomes. Failures must stop generation rather than be accepted by metadata alone.

## Required review evidence
Two native exact-head seed cases; all four decoded media streams per case; complete object-only mask replay; mechanics checks independent of the generator predicate; prompt and complete-motion inspection; native edge checks; runtime witness and case mapping; all artifact hashes; public playback and publication receipts. Source correctness and scale readiness are reported separately. No PASS is implied by this design document.
