---
title: IM-POWER website
summary: This page provides the backbone of the project
    - Bonaventura Tagliafierro
    - Malin Göteman
date: 2026-08-14
some_url: TBD
---

Capturing the overall performance of a floating offshore wind farm requires simulating a storm of realistic duration — on the order of four hours — across a domain spanning kilometres, while resolving wind and wave interaction with each turbine at a scale of tens of centimetres. Simulating an entire farm directly remains prohibitive on current hardware, as recent reviews of CFD applications for FOWTs confirm ([Zhang et al. 2024](#ZHANG_2024_reviewCfdFowt)). IM-POWER follows the multi-tier strategy set out in [**RO1**](overview.md): the farm is decomposed to the level of the individual turbine, each turbine is resolved at high fidelity, and total farm output is reconstructed by integration under coherent environmental loading.

<div style="background: linear-gradient(135deg, #E3F2FD 0%, #F1F8FE 100%); padding: 24px; border-radius: 10px; box-shadow: 0 4px 10px rgba(0,0,0,0.12); margin-bottom: 24px; border-left: 6px solid #1565C0;">
  <div style="font-size: 0.75em; letter-spacing: 0.08em; text-transform: uppercase; color: #1565C0; font-weight: 700; margin-bottom: 6px;">Core contribution</div>
  <h3 style="margin: 0 0 12px 0; color: #0D47A1; font-size: 1.4em;">Neural-network surrogate for hydrodynamic force reconstruction</h3>
  <p style="color: #000000; margin: 0 0 14px 0;">A physics-based pipeline for training and deploying a neural-network surrogate, embedded directly within a velocity-Verlet integration scheme so that the reconstructed force at each sub-step is inferred from the evolving system state. This is what makes farm-scale simulation tractable: the response of many turbines can be reconstructed without resolving each one at full fidelity.</p>
  <div style="display: inline-block; background-color: #ffffff; padding: 10px 16px; border-radius: 6px; font-weight: 600; color: #1565C0; box-shadow: 0 1px 3px rgba(0,0,0,0.08);">Scalability demonstrated to 1024 floating bodies in a coherent sea state</div>
</div>

<div style="background-color: #f0f8ff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); margin-bottom: 24px;">
  <h3 style="margin-top: 0; color: #0D47A1; border-bottom: 2px solid #3498db; padding-bottom: 10px;">Supporting framework</h3>
  <ul style="list-style-type: none; padding-left: 0;">
    <li style="margin-bottom: 12px; color: #000000;">
      <strong style="color: #2980b9;">DualSPHysics–OpenFAST coupling.</strong> Tower-base loads integrating aerodynamic, control and structural effects are transferred to the hydrodynamic solver, which advances the platform dynamics and returns displacements, velocities and accelerations.
    </li>
    <li style="margin-bottom: 12px; color: #000000;">
      <strong style="color: #2980b9;">MoorDynPlus coupling.</strong> Mooring dynamics resolved alongside platform motion, giving line tensions directly from the coupled simulation.
    </li>
    <li style="margin-bottom: 12px; color: #000000;">
      <strong style="color: #2980b9;">Open release.</strong> Distributed as part of the open-source DualSPHysics framework, with documentation and reproducible simulation templates.
    </li>
  </ul>
</div>

<div style="background-color: #f0f8ff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); margin-bottom: 24px;">
  <h3 style="color: #0D47A1; border-bottom: 2px solid #3498db; padding-bottom: 10px; margin-top: 0;">Blocks of Work</h3>
  <ul style="list-style-type: none; padding-left: 0;">
    <li style="margin-bottom: 15px;">
      <h4 style="color: #2980b9; margin-bottom: 5px;">BoW 1: Feature Design and Implementation &nbsp;<span style="font-size: 0.75em; color: #1565C0; font-weight: 600;">&#10003; completed</span></h4>
      <p style="color: #000000;">The functionalities required to simulate floating offshore wind turbines within a high-fidelity solver are implemented. A numerical wave tank reproducing severe sea states interacting with the platform is configured and validated against experimental data from a scaled model campaign.</p>
    </li>
    <li style="margin-bottom: 15px;">
      <h4 style="color: #2980b9; margin-bottom: 5px;">BoW 2: Model Input Parameter Identification &nbsp;<span style="font-size: 0.75em; color: #1565C0; font-weight: 600;">&#10003; completed</span></h4>
      <p style="color: #000000;">Storm patterns and environmental conditions are characterised, and platform and mooring configurations defined, drawing on practical design experience from the floating wind sector through the industrial partnership.</p>
    </li>
    <li style="margin-bottom: 15px;">
      <h4 style="color: #2980b9; margin-bottom: 5px;">BoW 3: Final Results Reconstruction &nbsp;<span style="font-size: 0.75em; color: #1565C0; font-weight: 600;">&#10003; completed</span></h4>
      <p style="color: #000000;">Farm-level output is reconstructed by integrating the response of individual turbines, using the neural-network surrogate embedded within the rigid-body dynamics solver.</p>
    </li>
  </ul>
</div>

<div class="methodology" style="background-color: #f0f8ff; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
<h2 style="color: #0D47A1; margin-top: 0;">Modeling Approach</h2>
<hr style="border: 0; height: 2px; background-color: #3498db; margin-top: 10px; margin-bottom: 20px;">
<a id="figure-1"></a>
<figure>
  <img src="../../figures/model_strategy.png" alt="IM-POWER project methodology" style="width: 100%; max-width: 800px;">
  <figcaption><em>Figure 1: IM-POWER project methodology - Model strategy overview</em></figcaption>
</figure>

<a href="#figure-1">Figure 1</a> illustrates the multi-tier modeling approach for simulating floating offshore wind farms during storm conditions. The methodology comprises the following components:

  <div class="component" style="margin-bottom: 15px;">
    <h4 style="color: #2980b9;">1. Environmental Modeling</h4>
    <ul style="list-style-type: none; padding-left: 20px;">
      <li>• Wave propagation across the farm area using phase-resolving wave models</li>
      <li>• Wind conditions represented through steady and sheared inflow profiles</li>
    </ul>
  </div>

  <div class="component" style="margin-bottom: 15px;">
    <h4 style="color: #2980b9;">2. Farm Layout (representation of different FOWT configurations)</h4>
    <ul style="list-style-type: none; padding-left: 20px;">
      <li>• Tension-leg platform</li>
      <li>• Semi-submersible platform</li>
      <li>• Semi-submersible hybrid wind–wave platform</li>
    </ul>
  </div>

  <div class="component" style="margin-bottom: 15px;">
    <h4 style="color: #2980b9;">3. Individual Turbine Simulation</h4>
    <ul style="list-style-type: none; padding-left: 20px;">
      <li>• High-fidelity modelling of wave–platform interaction using DualSPHysics</li>
      <li>• Aero-servo-elastic turbine response resolved through the coupling with OpenFAST</li>
      <li>• Mooring dynamics resolved through the coupling with MoorDynPlus</li>
      <li>• Validation against experimental data and code-to-code comparison against standard engineering tools</li>
    </ul>
  </div>

  <div class="component" style="margin-bottom: 15px;">
    <h4 style="color: #2980b9;">4. Farm-level Integration</h4>
    <ul style="list-style-type: none; padding-left: 20px;">
      <li>• Neural-network surrogate for hydrodynamic force reconstruction, trained on high-fidelity simulation data</li>
      <li>• Scalability demonstrated for up to 1024 floating bodies within a coherent sea state</li>
      <li>• High-performance computing on national (NAISS, UPPMAX) and European (EuroHPC) infrastructures</li>
    </ul>
  </div>

  <div class="component" style="margin-bottom: 15px;">
    <h4 style="color: #2980b9;">5. Data Collection and Analysis</h4>
    <ul style="list-style-type: none; padding-left: 20px;">
      <li>• Simulation inputs, geometries and execution scripts archived openly with a persistent identifier</li>
      <li>• Reproducible templates released alongside the software</li>
    </ul>
  </div>
</div>