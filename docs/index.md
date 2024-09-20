---
title: Welcome to the IM-POWER website
summary: Introduction to the wiki doc
authors: 
    - Bonaventura Tagliafierro
    - Malin Göteman
date: 2024-09-11
some_url: TBD
---
# Introduction <img src="assets/images/logo.png" alt="IM-POWER Logo" style="height: 60px; vertical-align: middle; float: right; margin-left: 10px;">


**IM-POWER** aims to develop _A numerical Integrated Model for the POWER output of floating offshore wind farms that are fully grid-connected during sea storms_. This Horizon 2022 Marie Skłodowska-Curie Postdoctoral Fellowship project, funded by the Research Executive Agency (REA), focuses on renewable energy, wind energy, and floating offshore wind. The project also incorporates aspects of Computational Fluid Dynamics, power grid management, electricity distribution systems, and Smoothed Particle Hydrodynamics [(EC CORDIS)](https://ec.europa.eu/info/funding-tenders/opportunities/portal/screen/how-to-participate/org-details/999999999/project/101109440/program/43108390/details). The objective of IM-POWER is to ultimately:


- Impact the design procedures for floating offshore wind turbines (FOWTs);
- Support power grid updates.

To achieve the final goal of the project, two research objectives (**RO1** and **RO2**) will be met:

<div class="objectives" style="background-color: #e3f2fd; padding: 15px; border-left: 5px solid #2196f3; margin-bottom: 15px;">
<strong>Objectives:</strong> 
<ul class="fancy-list">
  <li id="ro1"><strong>RO1</strong> Define and validate model-chain free software to address the spatial multi-scale nature of wave/wind generation and propagation for offshore wind farms under storm scenarios;</li>
  <li id="ro2"><strong>RO2</strong> Enhance the capabilities of existing open-source software towards a fully integrated tool for FOWTs suitable for high-fidelity simulations.</li>
</ul>
</div>

Significant **knowledge gaps** persist in several key areas of offshore wind systems during storm conditions:

1. **Turbine behavior**: The dynamic response of FOWTs under extreme wind and wave loads is not fully understood.
2. **Farm-level effects**: Interactions between multiple turbines in a farm during storms, including wake effects and power load redistributions, remain unclear.
3. **Grid integration**: The impact of rapid power fluctuations from storm-affected wind farms on grid stability and reliability is not well-characterized.
4. **Forecasting challenges**: Accurate prediction of power output during extreme weather events is still difficult, complicating grid management.

These gaps have implications for power grid reliability, as highlighted by [Olauson et al. (2016)](#Olauson2016). A case study for Sweden by [Holtinger et al. (2019)](#Holtinger2019) further emphasizes that extreme climate events can significantly challenge power systems when just 50% of intermittent renewable energy (IRE) is integrated.


## **Innovative aspects of the research program**

**IM-POWER** will use a CFD platform that portrays the first open-source software able to precisely simulate FOWTs, with high accuracy and robustness. This software can be used out of the box, without requiring modification of the source code. Furthermore, the project will provide:

- Critical information for the optimization, design, and update of power grids and short-term storage facilities through the estimation of floating wind farm power output;
- Guidelines for the efficient allocation of the offshore wind farms.

The assessment of floating wind farm power output under storm conditions has never been attempted before. As of the writing of this document, there is no data publicly available regarding FOWTs under sea storm conditions.

## **Our research team**
The objectives of this Action are complex, and interdisciplinary challenges will require combining state-of-the-art methods in modelling wind and wave loads; wind farm response (including dynamics, structural response, and power control); as well as grid balance and reliability. The work team is composed as follows:

* **Dr Bonaventura Tagliafierro**. Uppsala University – Uppsala, Sweden (Researcher)
* **Prof Malin Göteman**. Uppsala University – Uppsala, Sweden (Supervisor)
* **Dr Victor Mendoza**. Hexicon AB – Stockholm, Sweden (External Supervisor)

<div style="display: flex; justify-content: space-around; align-items: center; margin-top: 20px; background-color: #e6f3ff; padding: 20px; border-radius: 10px;">
    <img src="assets/images/uppsala_logo.png" alt="Uppsala University Logo" style="height: 100px;">
    <img src="assets/images/hexicon_logo.svg" alt="Hexicon AB Logo" style="height: 100px;">
</div>

The Department of Electrical Engineering at Uppsala University (Sweden) is a leading research environment for future electric grid and renewable energy systems, and has a second-to-none collaboration with relevant industry leaders, international research centres, and regulatory authorities. Hexicon parnership will permit to investigate the issues considering a great level of detail owing to the company's experience in offshore wind energy, platform design, and control systems.

## References

- <a id="Olauson2016"></a> **Olauson et al. (2016)**: Olauson, J., Ayob, M.N., Bergkvist, M., Carpman, N., Castellucci, V., Goude, A., Lingfors, D., Waters, R., & Widén, J. (2016). Net load variability in Nordic countries with a highly or fully renewable power system. *Nature Energy*, 1(12). https://doi.org/10.1038/nenergy.2016.175

- <a id="Holtinger2019"></a> **Höltinger et al. (2019)**: Höltinger, S., Mikovits, C., Schmidt, J., Baumgartner, J., Arheimer, B., Lindström, G., & Wetterlund, E. (2019). The impact of climatic extreme events on the feasibility of fully renewable power systems: A case study for Sweden. *Energy*, 178, 695-713. https://doi.org/10.1016/j.energy.2019.04.128

