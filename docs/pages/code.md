---
title: IM-POWER website
summary: This page describes the methodology of the project
authors: 
    - Bonaventura Tagliafierro
    - Malin Göteman
date: 2024-09-11
some_url: TBD
---
To reduce the LCOE and thus unlock the potential of offshore wind, floating platforms under high-impact low-probability (HILP) events need to be studied to allow more efficient and accurate design procedures. One of the investigative tools that can reliably inform on the structural response of FOWTs is **numerical modeling** ([Otter et al. 2022](#Otter2022 "Otter et al. (2022). Oceanographic processes and marine renewable energy.")). A large body of research suggests that high-fidelity computational techniques, usually known as Computational Fluid Dynamics (CFD) methods, are required to accurately simulate the fluid-platform interaction under highly-energetic waves, thereby obtaining reliable model results ([Robertson et al. 2017](#Robertson2017 "Robertson et al. (2017). Numerical modeling of floating offshore wind turbines."), [Draycott et al. 2019](#Draycott2019 "Draycott et al. (2019). Experimental assessment of the fluid-structure interaction of offshore floating wind turbines."), [Zhang et al. (2024)](#ZHANG_2024_reviewCfdFowt "Zhang et al. 2024. Review of CFD applications in offshore wind engineering.")). However, the current software fleet does not provide a unified solution for adaptation to the special features of FOWTs, and while robust and accurate, simulating a complete wind farm with CFD-based computer programs is computationally cumbersome due to hardware limitations.

## DualSPHysics

DualSPHysics ([Domínguez et al. 2022](#Dominguez2022 "Domínguez et al. (2022). DualSPHysics: from fluid dynamics to multiphysics problems.")) is an open-source Computational Fluid Dynamics (CFD) code based on the Smoothed Particle Hydrodynamics (SPH) method. It is intended to simulate free-surface flow phenomena with complex geometries and fluid-structure interactions. Recent work by [Tagliafierro et al. (2023)](#TAGLIAFIERRO_2023 "Tagliafierro et al. (2023). Numerical validations and investigation of a semi-submersible floating offshore wind turbine platform interacting with ocean waves using an SPH framework.") has demonstrated its capabilities in modeling floating offshore wind turbines. This study proposed numerical validations of the DeepCwind semi-submersible floating platform, using data from two experimental investigations, which will serve as preliminary validations for the IM-POWER project.



## Development

Developed through collaboration between the University of Vigo (Spain) and the University of Manchester (UK), DualSPHysics is continuously evolving with contributions from researchers worldwide. For more information, visit the [DualSPHysics website](https://dual.sphysics.org/).

 
## References

- <a id="Otter2022"></a> **Otter et al. (2022)**: Otter, A., Murphy, J., Pakrashi, V., Robertson, A., & Desmond, C. (2022). A review of modelling techniques for floating offshore wind turbines. *Wind Energy*, 25(5), 831-857. https://doi.org/10.1002/we.2701

- <a id="Robertson2017"></a> **Robertson et al. (2017)**: Robertson, A. N., Wendt, F., Jonkman, J. M., Popko, W., Dagher, H., Gueydon, S., ... & Debruyne, Y. (2017). OC5 Project Phase II: Validation of Global Loads of the DeepCwind Floating Semisubmersible Wind Turbine. *Energy Procedia*, 137, 38-57. https://doi.org/10.1016/j.egypro.2017.10.333

- <a id="ZHANG_2024_reviewCfdFowt"></a> **Zhang et al. (2024)**: Zhang, W., Calderon-Sanchez, J., Duque, D., & Souto-Iglesias, A. (2024). Computational Fluid Dynamics (CFD) applications in Floating Offshore Wind Turbine (FOWT) dynamics: A review. *Applied Ocean Research*, 150, 104075. https://doi.org/10.1016/j.apor.2024.104075

- <a id="Draycott2019"></a> **Draycott 2019**: Draycott, S., Sellar, B., Davey, T., Noble, D.R., Venugopal, V., & Ingram, D.M. (2019). Capture and simulation of the ocean environment for offshore renewable energy. *Renewable and Sustainable Energy Reviews*, 104, 15-29. https://doi.org/10.1016/j.rser.2019.01.011

- <a id="Dominguez2022"></a> **Domínguez et al. (2022)**: Domínguez, J.M., Fourtakas, G., Altomare, C., Canelas, R., Tafuni, A., García Feal, O., Martínez-Estévez, I., Mokos, A., Vacondio, R., Crespo, A., Rogers, B., Stansby, P.K., & Gómez-Gesteira, M. (2022). DualSPHysics: from fluid dynamics to multiphysics problems. *Computational Particle Mechanics. https://doi.org/10.1007/s40571-021-00404-2

- <a id="TAGLIAFIERRO_2023"></a> **Tagliafierro et al. (2023)**: Tagliafierro, B., Karimirad, M., Altomare, C., Göteman, M., Martínez-Estévez, I., Capasso, S., Domínguez, J. M., Viccione, G., Gómez-Gesteira, M., & Crespo, A. J. C. (2023). Numerical validations and investigation of a semi-submersible floating offshore wind turbine platform interacting with ocean waves using an SPH framework. *Applied Ocean Research*, 141, 103757. https://doi.org/10.1016/j.apor.2023.103757