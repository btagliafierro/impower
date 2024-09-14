---
title: DSPH documentation
summary: Boundary conditions
authors: 
    - Bonaventura Tagliafierro
    - Alejandro J. C. Crespo
date: 2023-11-11
some_url: TBD
---  
# Boundary conditions

In DualSPHysics, the boundary is described by a set of particles that are considered as a
separate set to the fluid particles. The software currently provides functionality for solid
impermeable and periodic open boundaries. Methods to allow boundary particles to be
moved according to fixed forcing functions are also present.

## Dynamic Boundary Condition

The Dynamic Boundary Condition (DBC) is the default method provided by
DualSPHysics [Crespo et al., 2007]. This method sees boundary particles that satisfy the
same equations as fluid particles, however they do not move according to the forces
exerted on them. Instead, they remain either fixed in position or move according to an
imposed/assigned motion function (i.e. moving objects such as gates, wave-makers or
floating objects).

When a fluid particle approaches a boundary and the distance between its particles and
the fluid particle becomes smaller than twice the smoothing length (h), the density of
the affected boundary particles increases, resulting in a pressure increase. In turn this
results in a repulsive force being exerted on the fluid particle due to the pressure term in
the momentum equation.

Stability of this method relies on the length of time step taken being suitably short in
order to handle the highest present velocity of any fluid particles currently interacting
with boundary particles and is therefore an important point when considering how the
variable time step is calculated.

Note that different boundary conditions have been tested in DualSPHysics in the work of [Domínguez et al., 2015]. 

## Periodic open boundary condition

DualSPHysics provides support for open boundaries in the form of a periodic boundary
condition. This is achieved by allowing particles that are near an open lateral boundary
to interact with the fluid particles near the complimentary open lateral boundary on the
other side of the domain.

In effect, the compact support kernel of a particle is clipped by the nearest open
boundary and the remainder of its clipped support applied at the complimentary open
boundary [Gómez-Gesteira et al., 2012a].

### Pre-imposed boundary motion

Within DualSPHysics it is possible to define a pre-imposed movement for a set of
boundary particles. Various predefined movement functions are available as well as the
ability to assign a time-dependant input file containing kinematic detail.
These boundary particles behave as a DBC described in Section 3.8.1, however rather
than being fixed, they move independently of the forces currently acting upon them.
This provides the ability to define complex simulation scenarios (i.e. a wave-making
paddle) as the boundaries influence the fluid particles appropriately as they move.

# Fluid-driven objects

It is also possible to derive the movement of an object by considering its interaction
with fluid particles and using these forces to drive its motion. This can be achieved by
summing the force contributions for an entire body. By assuming that the body is rigid,
the net force on each boundary particle is computed according to the sum of the
contributions of all surrounding fluid particles according to the designated kernel
function and smoothing length. Each boundary particle k therefore experiences a force
per unit mass given by

<p align="center">
<img src="https://i.imgur.com/KwwcVCU.png"/> (36)
</p>

where fka is the force per unit mass exerted by the fluid particle a on the boundary
particle k, which is given by

<p align="center">
<img src="https://i.imgur.com/SPQDcgI.png"/> (37)
</p>

For the motion of the moving body, the basic equations of rigid body dynamics can then
be used

<p align="center">
<img src="https://i.imgur.com/CiL3M8k.png"/> (38.1)
</p>

<p align="center">
<img src="https://i.imgur.com/X8baOKr.png"/> (38.2)
</p>

where M is the mass of the object, I the moment of inertia, V the velocity, Ω the
rotational velocity and R0 the centre of mass. Equations 38.1 and 38.2 are integrated in
time in order to predict the values of V and Ω for the beginning of the next time step.
Each boundary particle within the body then has a velocity given by

<p align="center">
<img src="https://i.imgur.com/UiKDdyy.png"/> (39)
</p>

Finally, the boundary particles within the rigid body are moved by integrating Eq. 39 in time. The works of [Monaghan et al., 2003] and [Monaghan, 2005] show that this technique conserves both linear and angular momentum. [Bouscasse et al., 2013] presented successful validations of nonlinear water wave interaction with floating bodies in SPH comparing with experimental data from [Hadzić et al., 2005] that includes deformations in the free-surface due to the presence of floating boxes and the movement of those objects during the experiment (heave, surge and roll displacements). Several validations using DualSPHysics are performed in [Canelas et al., 2015] that analyse the buoyancy-driven motion with solid objects larger than the smallest flow scales and with various densities. They compared SPH numerical results with analytical solutions, with other numerical methods [Fekken, 2004] and with experimental measurements.

## 3.8.5 Modified Dynamic Boundary Condition 

The Dynamic Boundary Condition (DBC) presents some drawbacks such as: over dissipation; the evolution of density and pressure of the fixed boundary particles leading to unphysical values for those points, and unphysically large boundary layers. Another drawback of using DBC arises when considering the steady-state 2D channel flows such as Poiseuille and Couette flows, as the boundary layer is not accurately solved unless a high resolution is used. The approximation of no-slip by setting zero velocity at each of the boundary particles fails to capture the condition for low resolutions. This then leads to higher than expected velocities close to the boundary and throughout the flow. Despite all this, DBC can be successfully used for coastal engineering problems due the capability of discretizing complex 3D geometries without the need of implementing complex mirroring techniques or semi-analytical wall boundary conditions. 

We will describe here the approach presented in [English et al. 2019] that includes a modification of DBC (mDBC). Within this implementation, the boundary particles are arranged in the same way as the boundary particles in the original DBC, with the boundary interface located half a particle spacing from the inner most layer of boundary particles. For each boundary particle a ghost node is projected into the fluid across the boundary interface in a similar procedure to [Marrone et al. 2011]. For a flat surface the ghost node is mirrored across the boundary interface along the direction of the boundary normal pointing into the fluid (Figure 3-1a) and fluid properties are found at this ghost node through a corrected SPH sum over the surrounding fluid particles only (Figure 3-1b). For a boundary particle located in a corner using the boundary normal would not work due to the presence of more than one normal. However, the boundary interfaces of each solid boundary meet to form an interface corner, and the ghost node is mirrored through the point of this corner into the fluid region (Figure 3-1c). Again, fluid properties are found at the ghost node through a corrected SPH sum of the surrounding fluid (Figure 3-1d). 

<p align="center">
<img width="600px" src="https://i.imgur.com/tFJVZZK.png"/>   
</p>

<p align="center">
<strong>Figure 3-1.</strong> Mirroring of ghost nodes (crosses) and the kernel radius around the ghost nodes for boundary particles in a flat surface (a) and a corner (c). Fluid particles (pink) included in the kernel sum around ghost nodes for boundary particles in a flat surface (b) and a corner (d).
</p>

The boundary particles receive fluid properties using the values calculated at the ghost node and an extrapolation method similar to the one used for open boundaries in [Tafuni et al. 2018]. For the density of the boundary particle _ρ_<sub>_b_</sub> the density _ρ_<sub>_g_</sub> and its gradient [_∂_<sub>_x_</sub>_ρ_<sub>_g_</sub>;_∂_<sub>_y_</sub>_ρ_<sub>_g_</sub>;_∂_<sub>_z_</sub>_ρ_<sub>_g_</sub>] are computed at the ghost node using the first order consistent SPH interpolation proposed by [Liu and Liu, 2006], which requires solving the following linear system for each ghost node _g_: 

<p align="center">
<img src="https://i.imgur.com/U0djbpZ.png"/> (40)      
</p>

where:

<p align="center">
<img src="https://i.imgur.com/MoDleaJ.png"/> (41)  
</p>

where the volume _V_<sub>_j_</sub> is computed as _V_<sub>_j_</sub>=_m_<sub>_j_</sub> ⁄ _ρ_<sub>_j_</sub>.

To evaluate the matrix **A**<sub>_g_</sub> and the vector **b**<sub>_g_</sub> at each ghost node _g_, a new particle interaction loop needs to be calculated. The new interaction requires the inversion of the matrix **A**<sub>_g_</sub>; however, this requires limited additional computational efforts when compared to the original DBC formulation. Note also that the matrix **A**<sub>_g_</sub> is diagonally dominant so rarely becomes ill-conditioned, even for a very disordered particle distribution. Due to this property, the adopted formulation to compute _ρ_<sub>_g_</sub>  and [_∂_<sub>_x_</sub>_ρ_<sub>_g_</sub>;_∂_<sub>_y_</sub>_ρ_<sub>_g_</sub>;_∂_<sub>_z_</sub>_ρ_<sub>_g_</sub>] is still suitable for real engineering applications with fragmented free surfaces.
Once the density and density gradient are computed at the ghost node, then the density of the boundary particle _ρ_<sub>_g_</sub> is obtained by means of a Taylor series expansion with the values found using the above relations through:

<p align="center">
<img src="https://i.imgur.com/4PfXF8a.png"/> (42)   
</p>

where **r**<sub>_g_</sub> and **r**<sub>_g_</sub> are the position of the boundary particle and associated ghost node respectively. Using this method to find the density of the boundary particle, creates smoother and more physical pressure and density fields in the boundary, and reduces the gap between the boundary and the fluid observed when using only DBC. The velocity at the ghost node is found using a Shepard filter sum 

<p align="center">
<img src="https://i.imgur.com/rmuXT0p.png"/> (43)   
</p>

The boundary particle then receives this velocity with the direction reversed to create a no-slip condition at the boundary interface. The no-slip condition created using this method is more accurate than using the zero-velocity approach of the original DBC as the negative velocity is more effective at reducing the velocity of the fluid. With this method it is also possible to create a free slip boundary by giving the boundary particles the exact tangential velocity found at the ghost node.


