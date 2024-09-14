---
title: From SPHysics to DualSPHysics
summary: Introduction to wiki doc
authors: 
    - Bonaventura Tagliafierro
    - Alejandro J. C. Crespo
date: 2023-11-11
some_url: TBD
---  

# My Document

This is a statement that needs a reference[^that].

## References
[^that]: Author Name. *Title of the Paper or Book*. Publisher, Year.

The DualSPHysics code originates from SPHysics, which is an open-source SPH model developed by researchers at the Johns Hopkins University (US), the University of Vigo (Spain), the University of Manchester (UK), and the University of Rome, La Sapienza. The software is available download at www.sphysics.org. A complete guide of the FORTRAN code is found in (Gómez-Gesteira et al., 2012a[^Sphysics_1]; 2012b[^Sphysics_2]).
The SPHysics FORTRAN code was validated for different problems of wave breaking [Dalrymple and Rogers, 2006], dam-break behaviour [Crespo et al., 2008], interaction with coastal structures [Gómez-Gesteira and Dalrymple, 2004] or with a moving breakwater [Rogers et al., 2010].

Although SPHysics allows problems to be simulated using high resolution and a wide range of formulations, the main problem for its application to real engineering problems is the excessively long computational runtimes, meaning that SPHysics is rarely applied to large domains. Hardware acceleration and parallel computing are required to make SPHysics more useful and versatile for engineering application.

!!! note annotate "Phasellus posuere in sem ut cursus (1)"

    Lorem ipsum dolor sit amet, (2) consectetur adipiscing elit. Nulla et
    euismod nulla. Curabitur feugiat, tortor non consequat finibus, justo
    purus auctor massa, nec semper lorem quam in massa.

1.  :man_raising_hand: I'm an annotation!
2.  :woman_raising_hand: I'm an annotation as well!
   
Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
{ .annotate }

1.  :man_raising_hand: I'm an annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be expressed in Markdown.

Originating from the computer games industry, Graphics Processing Units (GPUs) have now established themselves as a cheap alternative to High Performance Computing (HPC) for scientific computing and numerical modelling. GPUs are designed to manage huge amounts of data and their computing power has developed in recent years much faster than conventional central processing units (CPUs).  Compute Unified Device Architecture (CUDA) is a parallel programming framework and language for GPU computing using some extensions to the C/C++ language. Researchers and engineers of different fields are achieving high speedups implementing their codes with the CUDA language. Thus, the parallel power computing of GPUs can be also applied for SPH methods where the same loops for each particle during the simulation can be parallelised. 

DualSPHysics is implemented in C++ and CUDA language to carry out simulations with millions of particles on either the CPU or GPU respectively. The new CPU code presents some advantages, such as more optimised use of the memory. The object- oriented programming paradigm provides a code that is easy to understand, maintain and modify with a sophisticated control of errors available. Furthermore, better optimisations are implemented, for example particles are reordered to give faster access to memory, and the best approach to create the neighbour list is implemented [Domínguez et al., 2011]. The CUDA language manages the parallel execution of threads on the GPUs. The best approaches were considered to be implemented as an extension of the C++ code, so the most appropriate optimizations to parallelise particle interaction on GPU were implemented [Domínguez et al., 2013a; 2013b]. The first rigorous validations were presented in [Crespo et al., 2011]. The version 3.0 of the code is fully documented in [Crespo et al., 2015]. 
[^Sphysics_1]:
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.
[^Sphysics_2]:
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.


