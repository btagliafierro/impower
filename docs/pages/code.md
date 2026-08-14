---
title: IM-POWER website
summary: This page describes the methodology of the project
authors: 
    - Bonaventura Tagliafierro
    - Malin Göteman
date: 2026-08-14
some_url: TBD
---

Simulating a complete floating wind farm with high-fidelity CFD is computationally prohibitive on current hardware. IM-POWER addresses this by learning the fluid force rather than resolving it everywhere — replacing the expensive part of the calculation with a trained surrogate that runs inside the time integrator.

## Neural force surrogate

<div style="background: linear-gradient(135deg, #E3F2FD 0%, #F1F8FE 100%); padding: 24px; border-radius: 10px; box-shadow: 0 4px 10px rgba(0,0,0,0.12); margin-bottom: 24px; border-left: 6px solid #1565C0;">
  <p style="color: #000000; margin: 0; font-size: 1.05em;">Despite a substantial literature on machine-learning surrogates in hydrodynamics, no time-domain solver has been demonstrated that runs on a force surrogate in random waves. IM-POWER addresses that gap directly.</p>
</div>

A feed-forward neural network is trained on SPH records to reconstruct the fluid force on a floating body, and evaluated **in closed loop** inside the time integrator: the force it predicts sets the state it receives at the next step. The input window of past velocities and prescribed surface elevation plays the role that the convolution integral plays in a linear potential-flow model.

The immediate question is generalisation. Training coverage is limited to the sea states available at training time, while deployment spans a wider range of periods and amplitudes. Current results on a heaving sphere show that the coupled system integrates without divergence across the whole test set, avoiding autoregressive error growth, and that widening training coverage from one to eight sea states reduces error across the *T*<sub>p</sub>–*H*<sub>s</sub> plane, most visibly at small amplitudes. A linear BEM model remains more accurate for this particular case — a sphere in moderate seas away from resonance is only weakly nonlinear, so this comparison is a lower bound on what the surrogate offers. The nonlinear regimes that motivate training on SPH data in the first place remain largely untapped.

<div style="background-color: #f0f8ff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); margin-bottom: 20px;">
  <h4 style="margin-top: 0; color: #0D47A1;">In preparation</h4>
  <p style="color: #000000; margin-bottom: 0;">A Python stack implementing the surrogate for systems of multiple floating bodies is being prepared for release, covering training data generation, hyperparameter search, and deployment of the trained model inside the time-stepping solver.</p>
</div>

**Submitted:** *Closed-loop generalization of an SPH-trained force surrogate across random sea states* — 20th SPHERIC World Conference, Rome, Italy, 1–4 February 2027.

## Which forces should be learned

Embedding a data-driven force predictor inside a time-stepping scheme closes a feedback loop: the predicted force sets the structural response, which sets the next input to the network. Whether that loop is stable depends on which force components the network is asked to carry.

The project developed a diagnostic for this. Linearising the fluid force about a reference trajectory and regressing it against acceleration, velocity and displacement yields three sensitivity coefficients, which map directly onto the mass, damping and stiffness a solver needs for stable integration. Components with the right sign can be folded into the structural solver safely; what remains after the stable linear contributions are extracted is the nonlinear, history-dependent part that no proportional model captures — and that is the part worth giving to a neural network. The quality of the regression fit doubles as a check on the decomposition itself.

Applied to a heaving sphere near resonance using both a linear BEM model and SPH, the diagnostic separates cases cleanly: removing the hydrostatic restoring force exposes a stiffness the solver must supply, while removing the infinite-frequency added mass reveals where the two solvers diverge — BEM contributing a small stabilising term, SPH a destabilising one.

**Presented in:** *Towards ML-ready hybrid solvers for wave–structure interaction: stability of loosely coupled floating system solvers* — 41st International Workshop on Water Waves and Floating Bodies. Plitvice, Croatia, 26-29 April 2026 

## Why high-fidelity data

To reduce the LCOE and unlock the potential of offshore wind, floating platforms under high-impact low-probability (HILP) events need to be studied to allow more efficient and accurate design procedures. One of the investigative tools that can reliably inform on the structural response of FOWTs is **numerical modelling** ([Otter et al. 2022](#Otter2022 "Otter et al. (2022). A review of modelling techniques for floating offshore wind turbines.")). A large body of research suggests that high-fidelity computational techniques are required to accurately simulate fluid–platform interaction under highly energetic waves ([Robertson et al. 2017](#Robertson2017), [Draycott et al. 2019](#Draycott2019), [Zhang et al. 2024](#ZHANG_2024_reviewCfdFowt)). The available software also does not provide a unified solution adapted to the specific features of FOWTs. High-fidelity simulation is therefore both the source of the training data and the reference against which the surrogate is measured.

### DualSPHysics

DualSPHysics ([Domínguez et al. 2022](#Dominguez2022)) is an open-source CFD code based on the Smoothed Particle Hydrodynamics (SPH) method, intended to simulate free-surface flow phenomena with complex geometries and fluid–structure interaction. [Tagliafierro et al. (2023)](#TAGLIAFIERRO_2023) validated the code for floating offshore wind turbines against two experimental campaigns on the DeepCwind semi-submersible platform; those validations served as the starting point for IM-POWER.

Developed through collaboration between the University of Vigo (Spain) and the University of Manchester (UK), DualSPHysics is continuously evolving with contributions from researchers worldwide. For more information, visit the [DualSPHysics website](https://dual.sphysics.org/).

### Coupled framework

<div style="background-color: #f0f8ff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); margin-bottom: 20px;">
  <ul style="list-style-type: none; padding-left: 0; margin: 0;">
    <li style="margin-bottom: 12px; color: #000000;">
      <strong style="color: #2980b9;">DualSPHysics–OpenFAST.</strong> Tower-base loads integrating aerodynamic, control and structural effects are passed to the hydrodynamic solver, which advances the platform dynamics and returns displacements, velocities and accelerations.
    </li>
    <li style="margin-bottom: 12px; color: #000000;">
      <strong style="color: #2980b9;">MoorDynPlus.</strong> Mooring dynamics resolved alongside platform motion, giving line tensions directly from the coupled simulation.
    </li>
    <li style="margin-bottom: 0; color: #000000;">
      <strong style="color: #2980b9;">Project Chrono.</strong> Multibody and multiphysics functionality coupled to the SPH solver.
    </li>
  </ul>
</div>

## References

- <a id="Otter2022"></a> **Otter et al. (2022)**: Otter, A., Murphy, J., Pakrashi, V., Robertson, A., & Desmond, C. (2022). A review of modelling techniques for floating offshore wind turbines. *Wind Energy*, 25(5), 831-857. https://doi.org/10.1002/we.2701

- <a id="Robertson2017"></a> **Robertson et al. (2017)**: Robertson, A. N., Wendt, F., Jonkman, J. M., Popko, W., Dagher, H., Gueydon, S., ... & Debruyne, Y. (2017). OC5 Project Phase II: Validation of Global Loads of the DeepCwind Floating Semisubmersible Wind Turbine. *Energy Procedia*, 137, 38-57. https://doi.org/10.1016/j.egypro.2017.10.333

- <a id="ZHANG_2024_reviewCfdFowt"></a> **Zhang et al. (2024)**: Zhang, W., Calderon-Sanchez, J., Duque, D., & Souto-Iglesias, A. (2024). Computational Fluid Dynamics (CFD) applications in Floating Offshore Wind Turbine (FOWT) dynamics: A review. *Applied Ocean Research*, 150, 104075. https://doi.org/10.1016/j.apor.2024.104075

- <a id="Draycott2019"></a> **Draycott et al. (2019)**: Draycott, S., Sellar, B., Davey, T., Noble, D.R., Venugopal, V., & Ingram, D.M. (2019). Capture and simulation of the ocean environment for offshore renewable energy. *Renewable and Sustainable Energy Reviews*, 104, 15-29. https://doi.org/10.1016/j.rser.2019.01.011

- <a id="Dominguez2022"></a> **Domínguez et al. (2022)**: Domínguez, J.M., Fourtakas, G., Altomare, C., Canelas, R., Tafuni, A., García-Feal, O., Martínez-Estévez, I., Mokos, A., Vacondio, R., Crespo, A., Rogers, B.D., Stansby, P.K., & Gómez-Gesteira, M. (2022). DualSPHysics: from fluid dynamics to multiphysics problems. *Computational Particle Mechanics*, 9(5), 867-895. https://doi.org/10.1007/s40571-021-00404-2

- <a id="TAGLIAFIERRO_2023"></a> **Tagliafierro et al. (2023)**: Tagliafierro, B., Karimirad, M., Altomare, C., Göteman, M., Martínez-Estévez, I., Capasso, S., Domínguez, J. M., Viccione, G., Gómez-Gesteira, M., & Crespo, A. J. C. (2023). Numerical validations and investigation of a semi-submersible floating offshore wind turbine platform interacting with ocean waves using an SPH framework. *Applied Ocean Research*, 141, 103757. https://doi.org/10.1016/j.apor.2023.103757