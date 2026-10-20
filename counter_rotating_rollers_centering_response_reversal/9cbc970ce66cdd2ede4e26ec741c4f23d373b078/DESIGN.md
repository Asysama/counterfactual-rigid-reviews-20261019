# counter_rotating_rollers_centering_response_reversal: mechanics and audit contract

The rigid rod has one free horizontal coordinate x. The two support normals obey N_L+N_R=g per unit mass. Pitch equilibrium includes the friction couple from the finite rod thickness h. With k_L=mu*tanh((u-v)/epsilon), k_R=mu*tanh((-u-v)/epsilon), N_L=g*(a-x+h*k_R/2)/(2*a-h*(k_L-k_R)/2); acceleration=k_L*N_L+k_R*N_R. Both contacts remain loaded and the rod spans both supports. The drive ramps smoothly and is identical in both branches. The only changed law is mu_CF=-0.15*mu. This is negative kinetic friction, not a hidden lateral motor. Ordinary assumptions are horizontal-planar motion, rigid contacts and low-speed regularized friction. Surface rotation marks show the actual drive direction. A fixed painted mark on the base supplies a spatial reference. Numerics use RK4, 20 internal steps per video frame; no time rescaling.

## Source of motion
Finite-thickness horizontal rigid rod on two driven cylindrical supports. Normal reactions enforce vertical and angular equilibrium. Regularized kinetic friction uses the actual two slip velocities; the one operator changes its coefficient to -0.15 times its normal value. This is generator-owned reduced mechanics, not native Blender dynamics.

## Temporal/causal contract
The native output has 120 samples at t=f/24 seconds. Onset is sampled independently from geometry and response. All ordinary parameters, motor/support input trajectories and camera motions are shared. The first changed RGB frame is discovered from actual pixels; the mask begins there. The CF operator is negative_kinetic_friction_after_drive_start. Its consequences do not count as new independent operators.

## Static and rendered scale evidence
The 1,000,000 finite recipes vary four primary physical axes and two nuisance axes. 100,000 unique validated recipes is a CPU-only static target, not a claim of 100,000 rendered outputs. Rendered one-axis perturbations must show real image changes. Corner trajectories and every submitted formal seed must complete the stated outcomes. Failures must stop generation rather than be accepted by metadata alone.

## Required review evidence
Two native exact-head seed cases; all four decoded media streams per case; complete object-only mask replay; mechanics checks independent of the generator predicate; prompt and complete-motion inspection; native edge checks; runtime witness and case mapping; all artifact hashes; public playback and publication receipts. Source correctness and scale readiness are reported separately. No PASS is implied by this design document.
