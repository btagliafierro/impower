---
title: SPH implementation in DualSPHysics
summary: Introduction to wiki doc
authors: 
    - Bonaventura Tagliafierro
date: 2023-11-11
some_url: TBD
---  

# **SPH Formulation**

Smoothed Particle Hydrodynamics (SPH) is a Lagrangian meshless method. The
technique discretises a continuum using a set of material points or particles. When used
for the simulation of fluid dynamics, the discretised Navier-Stokes equations are locally
integrated at the location of each of these particles, according to the physical properties
of surrounding particles. The set of neighbouring particles is determined by a distance
based function, either circular (two-dimensional) or spherical (three-dimensional), with
an associated characteristic length or smoothing length often denoted as $h$. At each timestep
new physical quantities are calculated for each particle, and they then move
according to the updated values.

<div style="background-color: #e6f3ff; padding: 15px; border-left: 5px solid #3498db; margin-bottom: 15px;">
<strong>Note:</strong> The conservation laws of continuum fluid dynamics are transformed from their partial differential form to a form suitable for particle based simulation using integral equations based on an interpolation function, which gives an estimate of values at a specific point.
</div>

# **SPH Fundamentals**

Typically this interpolation or weighting function is referred to as the kernel function
$W$ and can take different forms, with the most common being cubic or quintic. In all
cases however, it is designed to represent a function $F(\mathbf{r})$  defined in $\mathbf{r}'$ by the integral approximation:

$$\begin{equation}
\tag{1}\label{sph} 
  \text{F}(\mathbf{r})=\int_{\Omega}{F(\mathbf{r}') W(\mathbf{r}-\mathbf{r}')\text{d}\mathbf{r}'},
\end{equation}$$

where $\mathbf{r}$ is the pointee and $\mathbf{r}'$ a ne

The smoothing kernel must fulfil several properties ([Monaghan 1992](#Monaghan1992 "I'm a tooltip!")), Lorem ipsum[^1] dolor sit amet, consectetur adipiscing elit.[^2] such as positivity inside a defined zone of interaction, compact support, normalization and monotonically decreasing value with distance and differentiability. For a more complete description of SPH, the reader is referred to [Monaghan, 2005; Violeau, 2013].

[Hover me](https://example.com "I'm a tooltip!")

[^1]: Lorem ipsum dolor sit amet, consectetur adipiscing elit.

The function $F$ in Equation \eqref{sph} can be approximated in a non-continuous, discrete form based
on the set of particles. In this case the function is interpolated at a particle ($a$) where a
summation is performed over all the particles that fall within its region of compact
support, as defined by the smoothing length $h$

$$$$

$$\begin{eqnarray}\tag{2}%
\frac{d\mathbf{v}_{a}}{dt}&=&-\sum_{b}m_{b}\Pi_{ab}\nabla_{a}W_{ab}
\end{eqnarray}$$


$$\begin{eqnarray}\tag{4}\label{ccc}%
\text{F}(\mathbf{r}_a) \approx \sum_{b}  \text{F}(\mathbf{r}_b) W(\mathbf{r}_a - \mathbf{r}_{b}, h) \text{F}_j &=& \sum_{j}  \frac{m_j}{\rho_j} W(\mathbf{r} - \mathbf{r}_{j}, h) \text{F}_j,\\
y &=& x^4 + 4   \nonumber   \\
&=& (x^2+2)^2 -4x^2  \\
&\le&(x^2+2)^2    \nonumber
\end{eqnarray}$$

where the subscript denotes an individual particle, _v_<sub>_b_</sub> is the volume of a neighbouring particle (_b_). If 
_v_<sub>_b_</sub>=_m_<sub>_b_</sub>/_ρ_<sub>_b_</sub>, with _m_ and _ρ_ being the mass and the density of particle _b_ respectively then Eq. (2) becomes

<p align="center">
<img src="https://i.imgur.com/rqu0cyp.png"/> (3)
</p>

## Smoothing kernel

The performance of an SPH model depends heavily on the choice of the smoothing kernel. Kernels are expressed as a function of the non-dimensional distance between particles (_q_), given by _q_=_r_/_h_ , where _r_ is the distance between any two given particles a and b and the parameter _h_ (the smoothing length) controls the size of the area around particle a in which neighbouring particles are considered. Within DualSPHysics, the user is able to choose from one of the following kernel definitions:

####  Cubic Spline [Monaghan and Lattanzio, 1985]
\begin{equation}
\Gamma_a = \sum_{b}m_b \frac{4 \sum{0}r_{ab}\cdot a W_{ab}}{(\rho_a + \rho_b)( r_{ab}^2 + 0.01h^2 )}
\end{equation}
where α<sub>D</sub> is equal to 10/7πh<sup>2</sup> in 2-D and 1/πh<sup>3</sup> in 3-D.

The tensile correction method, proposed by [Monaghan, 2000], is only actively used in
the cases of a kernel whose first derivative goes to zero with the particle distance q.

#### Quintic [Wendland, 1995]


\tag{5} \label{hhh} 
\begin{eqnarray}
&(1-r / h)^{5}-6(2 / 3-r / h)^{5}+15(1 / 3-r / h)^{5}, & 0 \leq r / h<1 / 3, \\
&(1-r / h)^{5}-6(2 / 3-r / h)^{5}, & 1 / 3 \leq r / h<2 / 3, \\
&(1-r / h)^{5}, & 2 / 3 \leq r / h<1, \\
    &0, & r / h \geq 1 .
\end{eqnarray}


where α<sub>D</sub> is equal to 7/4πh<sup>2</sup> in 2-D and 21/16πh<sup>3</sup> in 3-D.

$$\require{color}
\frac{\displaystyle
  {\overbrace{x^{n}}^{\text{the $k=0$ term}}} + 
  {\overbrace{\color{blue} \binom{n}{n-1}x^{n-1}h^{1}}^{\text{the $k=1$ term}}} +
  {\overbrace{\color{red} \sum_{k=2}^{k=n}\binom{n}{n-k}x^{n-k}h^{k}}^
    {\text{the terms from $k=2$ to $k=n$}}- x^n}}
  {h}
$$


In the text that follows, only kernels with an influence domain of 2 _h_ are
considered.

### Momentum Equation
The momentum conservation equation in a continuum is

<p align="center">
<img src="https://i.imgur.com/5tlgjt0.png"/> (6)
</p>

where **_Γ_** refers to dissipative terms and **_g_** is gravitational acceleration. DualSPHysics
offers different options for including the effects of dissipation.

### Artificial Viscosity
The artificial viscosity scheme, proposed by [Monaghan, 1992], is a common method
within fluid simulation using SPH due primarily to its simplicity. In SPH notation, Eq. 6
can be written as

<p align="center">
<img src="https://i.imgur.com/6MwDAHJ.png"/> (7)
</p>

where P<sub>k</sub> and ρ<sub>k</sub> are the pressure and density that correspond to particle k (as evaluated
at a or b). The viscosity term <img src="https://i.imgur.com/jIBQoNg.png" /> is given by

<p align="center">
<img src="https://i.imgur.com/PNAdFht.png"/> (8)
</p>

where ab **r**_ab=**r**_a-**r**_b and **v**_ab=**v**a-**v**b with **r**_k and **v**_k being the particle position and velocity respectively. <img src="https://i.imgur.com/0WtDphK.png" /> is the mean speed of sound, <img src="https://i.imgur.com/z8fQyJ8.png"/> and α is a coefficient that needs to be tuned in order to introduce the proper dissipation. The value of α=0.01 has proven to give the best results in the
validation of wave flumes to study wave propagation and wave loadings exerted onto
coastal structures [Altomare et al. (2015a)].

###  Laminar viscosity and Sub-Particle Scale (SPS) Turbulence
Laminar viscous stresses in the momentum equation can be expressed as [Lo and Shao,
2002]

<p align="center">
<img src="https://i.imgur.com/P7BXWYL.png"/> (9)
</p>

where υo is kinematic viscosity (typically 10^(-6) for water). In SPH discrete notation
this can be expressed as

<p align="center">
<img src="https://i.imgur.com/UhXKZwz.png"/> (10)
</p>

The concept of the Sub-Particle Scale (SPS) was first described by [Gotoh et al., 2001]
to represent the effects of turbulence in their Moving Particle Semi-implicit (MPS)
model. The momentum conservation equation is defined as

<p align="center">
<img src="https://i.imgur.com/PrCkxCv.png"/> (11)
</p>

where the laminar term is treated as per Eq. 9 and <img src="https://i.imgur.com/GCGmUXz.png" /> represents the SPS stress tensor. Favre-averaging is needed to account for compressibility in weakly compressible SPH
[Dalrymple and Rogers, 2006] where eddy viscosity assumption is used to model the
SPS stress tensor with Einstein notation for the shear stress component in coordinate
directions i and j <img src="https://i.imgur.com/z7vOxa2.png" /> where <img src="https://i.imgur.com/Ijsxbkq.png" /> is the sub-particle stress
tensor, <img src="https://i.imgur.com/cETvBL8.png" /> the turbulent eddy viscosity, k the SPS turbulence kinetic
energy, Cs the Smagorinsky constant (0.12), CI=0.0066, <img src="https://i.imgur.com/HS6vhQh.png" /> the particle to particle spacing and <img src="https://i.imgur.com/OtlzhLP.png" /> where <img src="https://i.imgur.com/CaDoLwa.png" /> is an element of the SPS strain tensor. [Dalrymple and Rogers, 2006] introduced SPS into weakly compressible SPH using Favre averaging, Eq.11 can be re-written as

<p align="center">
<img src="https://i.imgur.com/RUG9SJF.png"/> (12)
</p>

### 3.3 Continuity equation
Throughout the duration of a weakly-compressible SPH simulation (as presented
herein) the mass of each particle remains constant and only their associated density
fluctuates. These density changes are computed by solving the conservation of mass, or
continuity equation, in SPH form:

<p align="center">
<img src="https://i.imgur.com/CTsBQPl.png"/> (13)       
</p>

## 3.4 Equation of state
Following the work of [Monaghan, 1994], the fluid in the SPH formalism defined in
DualSPHysics is treated as weakly compressible and an equation of state is used to
determine fluid pressure based on particle density. The compressibility is adjusted so that
the speed of sound can be artificially lowered; this means that the size of time step taken
at any one moment (which is determined according to a Courant condition, based on the
currently calculated speed of sound for all particles) can be maintained at a reasonable
value. Such adjustment however, restricts the sound speed to be at least ten times faster
than the maximum fluid velocity, keeping density variations to within less than 1%, and
therefore not introducing major deviations from an incompressible approach. Following
[Monaghan et al., 1999] and [Batchelor, 1974], the relationship between pressure and
density follows the expression

<p align="center">
<img src="https://i.imgur.com/zbT9A4G.png"/> (14)
</p>

where <img src="https://i.imgur.com/noiD8EZ.png" /> where <img src="https://i.imgur.com/b9ppfL9.png" /> is the reference density and <img src="https://i.imgur.com/xDA7oho.png" /> which is the speed of sound at the reference density.

## 3.5 Density diffusion term
Within DualSPHysics it is also possible to apply a density diffusion term, that
introduces a diffusive term to reduce density fluctuations. The state equation describes a
very stiff density field, and together with the natural disordering of the
particles, high-frequency low amplitude oscillations are found to populate the density
scalar field. DualSPHysics uses a diffusive term in the
continuity equation, now written as

<p align="center">
<img src="https://i.imgur.com/mRVNwfw.png"/> (15.1)      
</p>

with,

<p align="center">
<img src="https://i.imgur.com/p6J9R8x.png"/> (15.2)   
</p>

This represents the density diffusion formulation by [Molteni and Colagrossi, 2009],
with a free parameter that needs to be attributed a suitable value. This modification
can be explained as the addition of the Laplacian of the density field to the continuity
equation. [Antuono et al., 2012] has presented a careful analysis of the influence of this
term in the system, by decomposing the Laplacian operator, observing the converge of
the operators and performing linear stability analysis to inspect the influence of the
diffusive coefficient. This equation represents exactly a diffusive term in the domain
bulk. The behaviour changes close to open boundaries such as free-surface. Due to
truncation of the kernel (there are no particles being sampled outside of an open
boundary), the first-order contributions are not null [Antuono et al., 2010], resulting in a
net force applied to the particles. This effect is not considered relevant for nonhydrostatic
situations, where this force is many orders of magnitude inferior to any
other force involved. Corrections to this effect were proposed by [Antuono et al., 2010],
but involve the solution of a renormalization problem for the density gradient, with
considerable computational cost. A (_δ_<sub>_Φ_</sub>) coefficient of 0.1 is recommended
for most applications.

The work of [Fourtakas et al., 2020] introduces a correction in Eq. (15.2). The key idea is to use the same formulation proposed by [Molteni and Colagrossi, 2009] but substituting the dynamic density with the total one. Thus, the term _ψ_<sub>_ab_</sub> takes the following form,

<p align="center">
<img src="https://i.imgur.com/sBfTPgw.png"/> (16)  
</p>

where the superscript _D_ denotes the dynamic density or pressure. Since _ρ_<sub>_D_</sub>=_ρ_<sub>_T_</sub>-_ρ_<sub>_H_</sub> (where superscript _T_ and _H_ denote the total and hydrostatic component, respectively), Eq. (16) can be rewritten in term of the hydrostatic and total parts as, 

<p align="center">
<img src="https://i.imgur.com/ndN6ySn.png"/> (17)  
</p>

In the context of the weakly compressible SPH, the equation of state relates the density to the total pressure at the particle location. However, only the hydrostatic part of the pressure is needed. Using the equation of state (EOS), the hydrostatic density difference can be obtained by,

<p align="center">
<img src="https://i.imgur.com/GaMbfSg.png"/> (18) 
</p>

The term _P_<sup>_H_</sup> is simply the hydrostatic pressure difference of particle _a_ and _b_,

<p align="center">
<img src="https://i.imgur.com/m2UHAnl.png"/> (19) 
</p>

where _z_<sub>_ab_</sub> is the vertical distance between particle _a_ and _b_ and

<p align="center">
<img src="https://i.imgur.com/SPKMCml.png"/> (20)   
</p>

In comparison with the formulation of the diffusive term proposed by [Molteni and Colagrossi, 2009] of Eq. (15.2), Eq. (16) improves the behaviour of pressure near the wall boundaries by avoiding the troublesome dynamic pressure and avoiding to compute the normalized density gradient. However, it must be noted that the formulation of [Antuono et al., 2010] is consistent and it can be adopted for any type of flow, whereas the use of total density in the diffusive term of Eq. (16) is expected to work better than Eq. (15.2) mostly for gravity-dominated flows. In the absence of a gravity force the formulation collapses to the original formulation of [Molteni and Colagrossi, 2009].

## 3.6 Shifting algorithm
Anisotropic particle spacing is an important stability issue in SPH as, especially in
violent flows, particles cannot maintain a uniform distribution. The result is the
introduction of noise in the velocity and pressure field, as well as the creation of voids
within the water flow for certain cases.

To counter the anisotropic particle spacing, [Xu et al., 2009] proposed a particle shifting
algorithm to prevent the instabilities. The algorithm was first created for incompressible
SPH, but can be extended to the weakly compressible SPH model used in
DualSPHysics [Vacondio et al., 2013]. With the shifting algorithm, the particles are
moved ("shifted") towards areas with fewer particles (lower particle concentration)
allowing the domain to maintain a uniform particle distribution and eliminating any
voids that may occur due to the noise.

An improvement on the initial shifting algorithm was proposed by [Lind et al., 2012]
who used Fick's first law of diffusion to control the shifting magnitude and direction.
Fick's first law connects the diffusion flux to the concentration gradient:

<p align="center">
<img src="https://i.imgur.com/N4Ufk40.png"/> (21)
</p>

where J is the flux, C the particle concentration, and D<sub>F</sub> the Fickian diffusion coefficient.

Assuming that the flux, i.e. the number of particles passing through a unit surface in
unit time, is proportional to the velocity of the particles, a particle shifting velocity and
subsequently a particle shifting distance can be found. Using the particle concentration,
the particle shifting distance δr<sub>s</sub> is given by:

<p align="center">
<img src="https://i.imgur.com/UZtavpb.png"/> (22)
</p>

where D is a new diffusion coefficient that controls the shifting magnitude and absorbs
the constants of proportionality. The gradient of the particle concentration can be found
through an SPH gradient operator:

<p align="center">
<img src="https://i.imgur.com/c6fJZ7j.png"/> (23)
</p>

The proportionality coefficient D is computed through a form proposed by [Skillen et
al., 2013]. It is set to be large enough to provide effective particle shifting, while not
introducing significant errors or instabilities. This is achieved by performing a Von
Neumann stability analysis of the advection-diffusion equation:

<p align="center">
<img src="https://i.imgur.com/6d2cuqH.png"/> (24)
</p>

where Δt<sub>max</sub> is the maximum local time step that is permitted by the CFL condition for a
given local velocity and particle spacing. The CFL condition states that:

<p align="center">
<img src="https://i.imgur.com/14FfvsR.png"/> (25)
</p>

Combining Eq. 24 and 25 we can derive an equation to find the shifting coefficient D:

<p align="center">
<img src="https://i.imgur.com/H42Ukai.png"/> (26)
</p>

where A is a dimensionless constant that is independent of the problem setup and
discretization and dt is the current time step. Values in the range of [1,6] are proposed
with 2 used as default.

The shifting algorithm is heavily dependent on a full kernel support. However, particles
at and adjacent to the free surface cannot obtain the full kernel support, which will
introduce errors in the free-surface prediction, potentially causing non-physical
instabilities. Applying Fick's law directly would result in the rapid diffusion of fluid
particles from the fluid bulk, due to the large concentration gradients at the free surface.

To counter this effect, [Lind et al., 2012] proposed a free-surface correction that limits
diffusion to the surface normal but allow shifting on the tangent to the free surface.
Therefore, this correction is only used near the free surface, identified by the value of
the particle divergence, which is computed through the following equation, first
proposed by [Lee et al., 2008]:

<p align="center">
<img src="https://i.imgur.com/x6jnVya.png"/> (27)
</p>

This idea is applied to the DualSPHysics code by multiplying the shifting distance of
Equation (22) with a free-surface correction coefficient AFSC.

<p align="center">
<img src="https://i.imgur.com/o0itVZQ.png"/> (28.1)
</p>

where AFST is the free-surface threshold and AFSM is the maximum value of the particle
divergence. The latter depends on the domain dimensions:

<p align="center">
<img src="https://i.imgur.com/Yz8AusQ.png"/> (28.2)
</p>

while the free surface threshold is selected for DualSPHysics as:

<p align="center">
<img src="https://i.imgur.com/SE2ii1z.png"/> (28.3)
</p>

To identify the position of the particle relative to the free surface, the difference of the
particle divergence to AFST is used. Therefore, the full shifting equation (Eq. 22) with the
free surface correction is:

<p align="center">
<img src="https://i.imgur.com/G2RY5Yu.png"/> (29)      
</p>

More information about the shifting implementation can be found in [Mokos, 2013].

## 3.7 Time stepping

In DualSPHysics two explicit time integration schemes are implemented. For brevity, the governing equations are written as 

<p align="center">
<img src="https://i.imgur.com/kzpoD9e.png"/>    
</p>

These equations are integrated in time using a computationally simple Verlet based
scheme or a more numerically stable but computationally intensive two-stage
Symplectic method.

###  3.7.1 Verlet scheme
The Verlet scheme [Verlet, 1967] is commonly used in molecular dynamics since it is a low computational cost scheme with a second order accurate space integrator that does not require multiple calculation steps within an iteration interval, the WCSPH variables are calculated according to

<p align="center">
<img src="https://i.imgur.com/nqlcXSb.png"/> (30)   
</p>

Due to the integration over a staggered time interval, the equations of density and velocity are decoupled, which may lead to divergence of the integrated values. Therefore, an intermediate step is required every N_S steps (Ns≈40 is recommended) according to

<p align="center">
<img src="https://i.imgur.com/1HPIRtl.png"/> (31)    
</p>

where the subscript _n_ denotes the time step and _t_= _nΔt_

###  3.7.2 Symplectic Position Verlet scheme
The symplectic position Verlet time integrator scheme [Leimkuhler and Matthews, 2016] is second order accurate in time. It is ideal for Lagrangian schemes as it is time reversible and symmetric in the absence of diffusive terms that preserve geometric futures. The position Verlet scheme in the absence of dissipation forces reads, 

<p align="center">
<img src="https://i.imgur.com/GpljYGY.png"/> (32)   
</p>  

However, in the presence of viscous forces and density evolution in DualSPHysics, the velocity is required in n+1/2 step thus, a velocity Verlet half step is used to compute the required velocity for the acceleration and density evolution for <img src="https://i.imgur.com/IWYnnF6.png" /> and <img src="https://i.imgur.com/WxrRmQJ.png" /> respectively. The scheme implemented in DualSPHysics reads,

<p align="center">
<img src="https://i.imgur.com/BX60V6e.png"/> (33)     
</p>

where <img src="https://i.imgur.com/3PB1yqV.png" /> is substituted to <img src="https://i.imgur.com/1rY4BOR.png" /> in Eq. 32 to eliminate dependence on <img src="https://i.imgur.com/MO9iU7a.png" />.

Finally, the density evolution follows the half time steps of the symplectic position Verlet scheme as follows [Parshikov et al, 2000], 

<p align="center">
<img src="https://i.imgur.com/AR6RY84.png"/> (34)    
</p>

where <img src="https://i.imgur.com/onHyc7t.png" />.

### 3.7.3 Variable time step
With explicit time integration schemes the timestep is dependent on the Courant-
Friedrichs-Lewy (CFL) condition, the forcing terms and the viscous diffusion term. A
variable time step Δt is calculated according to [Monaghan et al., 1999] using

<p align="center">
<img src="https://i.imgur.com/XjFLZ1F.png"/> (35)  
</p>

where Δtf is based on the force per unit mass (|fa|), and Δtcv combines the Courant and
the viscous time step controls.

## Features

- <a id="Monaghan1992"></a> **Monaghan1992**: Monaghan1992 of feature 1.
- <a id="feature-2"></a> **Feature 2**: Description of feature 2.
- <a id="feature-3"></a> **Feature 3**: Description of feature 3.
