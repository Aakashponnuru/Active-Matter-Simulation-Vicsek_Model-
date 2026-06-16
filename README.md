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

Unlike traditional passive systems governed by thermal equilibrium (where energy is conserved and detailed balance holds), **active matter** consists of agents that continuously consume energy from their environment to generate self-propelled motion. This breaks detailed balance at the microscopic level, leading to striking macroscopic phenomena such as giant number fluctuations, spontaneous symmetry breaking, and non-equilibrium phase transitions. 

### The Vicsek Model Formulation
To study this, the simulation implements the classic **Vicsek Model** (1995), a minimal, over-damped model of active matter. It treats particles as self-propelled point particles moving at a constant speed $v_0$ in a 2D space with periodic boundary conditions.

The system evolves through discrete time steps ($\Delta t = 1$). The state of each particle $i$ is defined by its position $\vec{r}_i$ and its direction of motion $\theta_i$. 

**1. Velocity and Position Update:**
The velocity of particle $i$ is strictly constrained to a constant magnitude $v_0$:
$$\vec{v}_i(t) = v_0 (\cos \theta_i(t), \sin \theta_i(t))$$

Positions are updated ballistically:
$$\vec{r}_i(t + \Delta t) = \vec{r}_i(t) + \vec{v}_i(t) \Delta t$$

**2. Alignment Rule (The Interaction):**
The core physics of the model lies in its ferromagnetic-like alignment rule. At each time step, particle $i$ attempts to align its direction of motion with the average direction of all neighboring particles $j$ (including itself) within a local interaction radius $r_c$. 

$$\theta_i(t + \Delta t) = \langle \theta(t) \rangle_{r_c} + \Delta \theta_i$$

Here, $\langle \theta(t) \rangle_{r_c}$ is the average angle of velocities within the circle $|\vec{r}_i - \vec{r}_j| < r_c$. 

**3. Stochastic Noise:**
The term $\Delta \theta_i$ represents angular noise, drawn uniformly from the interval $[-\eta/2, \eta/2]$. This acts as an effective "temperature," disrupting the local alignment.

### Quantifying the Phase Transition
To analyze the emergent macroscopic behavior, we calculate the **normalized average velocity**, which serves as the macroscopic order parameter ($\varphi$ or $v_a$) for the system:

$$\varphi = \frac{1}{N v_0} \left| \sum_{i=1}^N \vec{v}_i \right|$$

* **Disordered State (Gas-like):** $\varphi \approx 0$. Particle directions are uncorrelated.
* **Ordered State (Flocking/Liquid-like):** $\varphi \approx 1$. Particles spontaneously break rotational symmetry and move in a uniform, collective direction.

### Non-Equilibrium Phase Transitions
By simulating multiple ensembles and scaling the system size, the project successfully captures two distinct phase transitions:

1.  **Noise-Driven Transition:** At a constant density, decreasing the noise parameter $\eta$ below a critical threshold $\eta_c$ causes the system to undergo a continuous kinetic phase transition from a disordered state to an ordered flocking state. As system size $N$ increases, the transition sharpens, approaching the thermodynamic limit.
2.  **Density-Driven Transition:** At a constant noise level, increasing the number density $\rho$ triggers a transition. Below a critical density $\rho_c$, interactions are too sparse to propagate order. Above $\rho_c$, local clusters form, grow, and eventually merge into a globally ordered state.
