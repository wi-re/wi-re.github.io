---
layout: page
title: WCSPH Dataset
description: Dataset of free-slip flows in 2D
img: assets/img/datasets/final-free-slip-obstacle.png
importance: 1
category: dataset
related_publications: true
---

## Description

This dataset contains a set of example simulations using WCSPH simulated with [diffSPH](https://github.com/wi-re/diffSPH). A matching dataloader is contained in the [SFBC](https://github.com/tum-pbs/SFBC) package

## Simulation Setup

The general simulation setup:
- Domain Size: $1[m]\times 1[m]$ ($[-0.5, 0.5]^2$)
- Particle Count: $128 \times 128 = 16384$
- Particle size: $1/ (128\times 128) = 0.000061035[m^2]$
- Neighborhood Size: $45.228$ neighbors per particle
- Rest Density: $1000 [kg/m^2]$
- Timestepping: Fixed $\Delta t = 1 [ms]$
- Integration Scheme: Symplectic Euler
- SPH Formulation: $\delta^+$-SPH
- Shifting Scheme: $\delta^+$-SPH
- Boundary Handling Scheme: MDBC
- Viscosity: $\delta^+$-SPH, $\operatorname{Re}=2000$

Generated Simulations:
- Two cases, either with or without a central obstacle (if there is boundary handling)
- We generate 16 simulations for training for each case
- Each case uses a random divergence free velocity field with increasing spatial frequencies in the velocity field (Note that higher frequency fields have different initial kinetic energies, the flows are normalized for maximum initial velocity NOT identical initial energy)
- We also generate 4 simulations for each case using regular vortices, i.e., similar to Taylor Green Vortex Setups

## Data Layout:

Each simulation is stored as a single hdf5 file
- initial
    - fluid
        - UID, Contains a unique identifier for each fluid particle to track them over time
        - positions, initial particle position
        - velocities, initial particle velocity
        - areas, fixed particle area
        - masses, fixed particle mass
        - densities, initial particle density, identical to the rest density of the fluid
        - potential, potential field used to create the divergence free initial velocity field
    - boundary
        - UID, contains a unique identifier for each boundary particle
        - bodyIDs, contains the boundary object ID this particle belongs to
        - positions, initial particle position
        - velocities, initial particle velocity
        - areas, fixed particle area
        - masses, fixed particle mass 
        - densities, initial particle density, identical to the rest density of the fluid
        - distances, distance of the boundary particle to the corresponding bodies surface
        - normals, direction towards the surface of the corresponding body
- simulationExport
    - '%05d', e.g., '00001'
        - UID
        - boundaryDensity
        - boundaryVelocity
        - fluidDensity
        - fluidVelocity
        - fluidPosition
        - fluidShiftAmount, $\delta^+$-SPH shifting update from the previous step
    - ...
- config (Contains a full copy of the diffSPH simulation config)

For examples on loading and visualizing the data refer to the two contained notebooks (datasetVisualizer.ipynb to visualize individual frames and datasetOverview.ipynb to visualize the entire dataset)

## Dataset Overview

The initial conditions show the velocity field color coded (and mapped to a grid) at $t=0$ with streamlines to visualize the flow field. The final state shows the particles color coded by their initial position/UID as particles. The UID is initialized from left to right, from bottom to top, in linear fashion.

<div class="row">
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/initial-free-slip.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/final-free-slip.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/initial-free-slip-obstacle.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/final-free-slip-obstacle.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Initial conditions on the left, final state on the right
</div>


## Dataset example trajectory



<div class="row">
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/output_free-slip_128x2x1.0x3x0_2024_11_03-13_37_00.gif" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/output_free-slip_wObstacle_128x2x1.0x3x0_2024_11_03-19_43_24.gif" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Example training case for base Frequency = 1, octaves = 3
</div>


<div class="row">
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/output_free-slip_TGV_128x2x2.0_2024_11_04-14_48_45.gif" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/datasets/output_free-slip_wObstacle_TGV_128x2x2.0_2024_11_04-14_58_32.gif" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Example test case for k=2
</div>
