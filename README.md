# Study of Molecular Dynamics & Non-Equilibrium Phase Transitions in Active Matter using the Vicsek Model

## Overview
This repository contains computational simulations exploring classical many-body systems through Molecular Dynamics (MD) and the emergent, non-equilibrium collective behavior of active matter using the Vicsek Model[cite: 2]. Unlike passive systems where energy is conserved and motion is driven by thermal equilibrium, this project models self-driven particles (like bird flocks or fish shoals) that continuously consume energy[cite: 2]. 

## Molecular Dynamics (MD) Implementation
The baseline MD simulation mirrors physical laboratory experiments through a strict procedural pipeline of sample preparation, equilibration, and measurement[cite: 2]. 
*   **System Parameters:** Simulates a 3D system with a box size of $L=24.0$, number density of $\rho=0.8$, and 11,059 particles dynamically derived via $N=\rho(L^3)$[cite: 2].
*   **Force Calculation:** Pairwise interactions are computed using the Lennard-Jones (LJ) potential with a cut-off radius of $r_c=2.5$[cite: 2].
*   **Boundary Conditions:** Employs Periodic Boundary Conditions (PBC) and the Minimum Image Convention to eliminate surface effects and simulate an infinite bulk fluid[cite: 2].
*   **Time Evolution:** Utilizes Velocity Verlet Integration over 3000 total time steps ($\Delta t=0.005$) to evolve the system[cite: 2].
*   **Analysis:** Computes the Radial Distribution Function (RDF), $g(r)$, to confirm thermal equilibrium and verify the formation of a stable first coordination shell characteristic of a liquid[cite: 2].

## Vicsek Model & Active Matter
The Vicsek simulation introduces a minimal model for active matter where self-propelled particles align with their neighbors under the influence of random noise[cite: 2].
*   **Dynamics:** Particles are initialized with random positions and directions in a 2D rectangular box ($L_x=25$, $L_y=16$), moving at a constant speed of $v=0.03$[cite: 2].
*   **Alignment & Noise:** At each time step, particles calculate the average direction of neighbors within an interaction radius of $r_c=1.0$ and add a random noise factor ($\eta$)[cite: 2].
*   **Order Parameter:** The system's macroscopic alignment is quantified by an order parameter ($v_a$), computed by taking the magnitude of the normalized sum of all particle velocity components[cite: 2].
