Abstract
The implementation of the energy policy to clean our energy system will lead to massive offshore wind power installations in the coming decades, thus causing the electricity grid balance to increasingly rely on intermittent renewable energy sources. Such dependence, and the increased electrification, leaves power grids vulnerable to the risk of negative impacts of climate-induced weather extremes. Nevertheless, the effects of extreme events on the reliability of electricity distribution systems remain an open question, and to address this point, IM-POWER is proposed here. The Action aims to develop a numerical integrated model to predict the power generation performance of emerging offshore wind technologies during storm conditions and anticipate their impact on power grids. IM-POWER will set a comprehensive numerical strategy to assess the power output of offshore wind farms that comprise wind turbines installed on floating platforms. High-fidelity modeling techniques for simulating marine structures and harsh marine conditions – involving wind effects, floating foundations, and power generators – will be combined. Three representative configurations of floating offshore wind turbines (FOWTs) will be arrayed into wind farms. To provide relevance to the layouts, their design will be tackled in cooperation with the world-leading project developer Hexicon AB (Sweden). Therefore, the computational tool will be used to investigate the power output of  the FOWTs by assessing their transient response when the peak of storms (usually lasting three or four hours) hits the wind farm. Owing to the effort required by the numerical procedure, hardware acceleration provided by the National Supercomputer Centre (Sweden) will be used to perform the calculations. The knowledge gained from the power production variability during storms using IM-POWER, for different platform configurations, will permeate FOWT design and optimization procedures, and support power grid upgrades. 

# Inputs

## Current File
Here is the file I'm looking at. It might be truncated from above and below and, if so, is centered around my cursor.

Please consider including several sections, each of which dedicated to possible scientific outcomes, take into account the following info: {\color{gray1}{\footnotesize{\#@APP-FORM-HEMSCAPF@\#}}}

# Part B-1

## Excellence {\color{gray1}{\footnotesize{\#@REL-EVA-RE@\#}}}

### Quality and pertinence of the project's research and innovation objectives (and the extent to which they are ambitious, and go beyond the state of the art)

#### Overview of the Action and objectives

# Inputs

## Current File
Here is the file I'm looking at. It might be truncated from above and below and, if so, is centered around my cursor.

Please consider including several sections, each of which dedicated to possible scientific outcomes, take into account the following info: {\color{gray1}{\footnotesize{\#@APP-FORM-HEMSCAPF@\#}}}

# Part B-1

## Excellence {\color{gray1}{\footnotesize{\#@REL-EVA-RE@\#}}}

### Quality and pertinence of the project's research and innovation objectives (and the extent to which they are ambitious, and go beyond the state of the art)

#### Overview of the Action and objectives

# Inputs

## Current File
Here is the file I'm looking at. It might be truncated from above and below and, if so, is centered around my cursor.

Please consider including several sections, each of which dedicated to possible scientific outcomes, take into account the following info: {\color{gray1}{\footnotesize{\#@APP-FORM-HEMSCAPF@\#}}}

# Part B-1

## Excellence {\color{gray1}{\footnotesize{\#@REL-EVA-RE@\#}}}

### Quality and pertinence of the project's research and innovation objectives (and the extent to which they are ambitious, and go beyond the state of the art)

#### Overview of the Action and objectives

# Inputs

## Current File
Here is the file I'm looking at. It might be truncated from above and below and, if so, is centered around my cursor.

Please consider including several sections, each of which dedicated to possible scientific outcomes, take into account the following info: {\color{gray1}{\footnotesize{\#@APP-FORM-HEMSCAPF@\#}}}

# Part B-1

## Excellence {\color{gray1}{\footnotesize{\#@REL-EVA-RE@\#}}}

### Quality and pertinence of the project's research and innovation objectives (and the extent to which they are ambitious, and go beyond the state of the art)

#### Overview of the Action and objectives

The Action IM-POWER will develop *A numerical **I**ntegrated **M**odel for the **POWER** output of floating offshore wind farms that are fully grid-connected during sea storms*. The researcher Dr. Bonaventura Tagliafierro will carry out the activities envisioned by this Action with a 24-month fellowship at Uppsala University (UU) (Uppsala, Sweden). The objective of IM-POWER is to ultimately impact the design procedures for floating offshore wind turbines (FOWTs) and support power grid updates. Due to the transversal competences that this task requires, Dr. Tagliafierro will be enrolled at the Department of Electrical Engineering @ UU under the supervision of Ass. Prof. Malin Göteman. The pragmatism of this Action is further promoted by the collaboration with a world-leading project developer and technology provider company in the emerging sector of offshore floating wind, Hexicon AB (Hexicon) (Stockholm, Sweden). In addition, UU has formed a Group of Experts (GoP) that will support this Action. To achieve the final goal of the project, two research objectives will be met:

- **RO1**: Define and validate model-chain free software to address the spatial multi-scale nature of wave/wind generation and propagation for offshore wind farms under storm scenarios; and
- **RO2**: Enhance the capabilities of existing open-source software towards a fully integrated tool for FOWTs suitable for high-fidelity simulations.

#### Motivation

The European Commission has lately recommitted through the REPowerEU Plan to targeting a green house gas reduction of 55% compared to the 1990s' emissions. Additionally, the share of renewables in the EU's overall energy mix should rise from 40% to 45% (ref., European Green Deal (EGD)), leading to a renewable power generation capacity of 1236 GW, in contrast with the total capacity reached in 2021 of 236 GW (189 GW in EU-27).

To achieve this goal, the Commission has endorsed wind energy, in particular **offshore wind**, as a relevant opportunity by prompting policy for fast deployment. The reasoning is simple: offshore wind resources are greater and more constant due to the absence of barriers, and not to be discounted is its greater acceptance by the public. As such, in Europe and globally, large installations of offshore wind farms are being planned and realized at faster rates.

Large **knowledge gaps** still remain regarding the performance and reliability of offshore wind systems in storm conditions, and how they could impact power grid reliability. A case study for Sweden suggests that extreme climate events can greatly challenge power systems, when 50% of intermittent renewable energy (IRE) is plugged in.

The objectives of this Action are complex, and interdisciplinary challenges will require combining state-of-the-art methods in modelling wind and wave loads; wind farm response (including dynamics, structural response, and power control); as well as grid balance and reliability. Dr. Tagliafierro is an expert in assessing the performance of wind farms subject to wind and wave loadings with high-fidelity software. The Department of Electrical Engineering at @ UU is a leading research environment for future electric grid and renewable energy systems, and has a second-to-none collaboration with relevant industry leaders, international research centres, and regulatory authorities. Lastly, Hexicon will permit to investigate the issues considering a great level of detail owing to the company's experience in offshore wind energy.

#### State-of-the-art

Currently, offshore wind power consists of generating electricity through wind farms installed at sea. In relatively shallow water (up to 50 meters depth), fixed-foundation wind turbines are employed, essentially preserving the structural features of onshore twins. To increase the installation depths, **floating structures** must be used. These platforms are stabilized by moorings and anchors that flexibly connect them to fixed points on the seabed, thus safely providing support in up to 300 meters of water depth. Floating wind farms comprise wind turbines that are placed on platforms, and connected to an offshore substation through submarine cables to transmit the generated electricity (Figure 1). Such complexity reflects into its average total cost per megawatt-hour over its lifetime (known as Levelised Cost of Energy -- LCOE), which is still high, even if compared with fixed-foundation offshore wind: this is what has hampered its use at large scales so far.

![Figure 1: Floating offshore wind farm diagram](figure_1.png)

To reduce the LCOE and thus unlock the potential of offshore wind, floating platforms under high-impact low-probability (HILP) events need to be studied to allow more efficient and accurate design procedures. One of the investigative tools that can reliably inform on the structural response of FOWTs is **numerical modeling**. A large body of research suggests that high-fidelity computational techniques, usually known as Computational Fluid Dynamics (CFD) methods, are required to accurately simulate the fluid-platform interaction under highly-energetic waves, thereby obtaining reliable model results.

#### Beyond the state of the art and innovative aspects of the research program

The Action will set a cutting-edge CFD platform that portrays the **first open-source software** able to precisely simulate FOWTs, with high accuracy and robustness. The software can be used by users out of the box, without requiring modification of the source code. Furthermore, not only will the estimation of the power output of floating wind farms constitute critical information for the optimization/design/update of power grids and short-term storage facilities, but also provide guidelines for the efficient allocation of the farms themselves. The assessment of floating wind farm power output under storm conditions has never been attempted before, and as of the writing of this document, there is no data publicly available regarding FOWTs under sea storm conditions.

### Soundness of the proposed methodology (including interdisciplinary approaches, consideration of the gender dimension and other diversity aspects if relevant for the research project, and the quality of open science practices)

#### Research methodology and approach

Wind farms that comprise FOWTs must be simulated using CFD methods for a length of time of 4 hours, which corresponds to a reasonable storm time duration. Due to the large scale of wind farms (on the order of km) and the high level of detail required to simulate wind and wave interactions with the turbine (on the order of tens of cm), a multi-tier modelling procedure is necessary to reduce the overall complexity, as postulated in RO1. In fact, as of now, the straightforward simulation of whole wind farms is prohibitive on account of the computational costs and hardware requirements. The **farm total power output** can be anticipated by breaking down the simulation of a farm to the wind-turbine level, thereby reconstructing it through integration. The outcome consistency is guaranteed by coherent environmental loads (wind profiles and waves) as generated by time-integrated numerical models for wave and wind propagation. In the following Blocks of Work (BoWs), a preliminary description of the activities to be performed are presented:

- **BoW 1**: Feature design and implementation. The required functionalities to simulate FOWTs with CFD codes are identified; a wave tank that reproduces extreme ocean waves interacting with the platform is configured. For these activities, the Researcher will be supported by the Supervisor and the GoP (detailed in WP3 and WP4).
- **BoW 2**: Model input parameter identification. A testing area is identified for the characterization of the storm pattern; definition of the local wave input by propagating real sea states for the entirety of the farm stretch of sea; definition of the park arrangement, comprising anchoring systems and power connectivity. Note that these activities require the support of Hexicon (detailed in WP4).
- **BoW 3**: Final results reconstruction. The power output of the wind farm is computed by integration of the response of all the wind turbines on each farm. The Researcher, the Supervisor, the GoP, and Hexicon will be involved in data interpretation and restitution (description in WP4).

The objective introduced in RO2 will be achieved by developing new software within the open-source DualSPHysics code. The latter is a CFD solver that is based on the Smoothed Particle Hydrodynamics method (SPH) for simulating the fluid mechanics; it has proved to be particularly suitable to simulate free-surface and violent flows. New functionalities to simulate wind-blade interaction and power control systems are embedded using a multiphysics set of functions (known as *library*), called Project Chrono, used as an interface.

Specifically, the following **tools** will be developed to comply with BoW 1:

- **Tool 1**: An **aerodynamic solver** for wind-blade interaction (in WP3);
- **Tool 2**: Two **open-loop control functions** for simulating blade pitch adjustment and generator absorbed power; (in WP3)

#### Inter/multidisciplinary aspects

The development of a multi-pronged profile by the candidate is conditional on the success of IM-POWER, which embraces objectives in different scientific fields, albeit synergistically related. An interdisciplinary understanding is key to taking this Action to completion, and the success of the project will be endorsed by the fact that the Researcher and the Supervisor have complementing backgrounds. In fact, the team can deal with structural design, use of high-fidelity numerical modelling procedures, control electrical systems, and finally indicate the implications on loss of power output on grid reliability. Dr. Tagliafierro's close cooperation and interaction with researchers and professionals at the host and the associated partner (electrical engineering, wind energy, power grid design) will be beneficial to developing a solid background on wind energy and energy delivery systems.

#### Gender dimension

The gender dimension is not explicitly relevant to the scientific contents of the project, since no personal/animal data will be involved. However, energy research has an implicit gender dimension, as the access to clean and sustainable energy is not equally distributed. Developing countries, and in particular women in developing countries, often suffer from unreliable and insufficient energy supply, and climate and environmental threats often affect women more than men; they are more vulnerable to natural hazards such as droughts and floods. The project aims to enable a future reliable and sustainable energy supply. This is of high relevance for all, but in particular for women and other groups exposed to environmental and climate threats.

#### Open science practices and research data management

The software that has been considered for engineering the new features is completely open-source, and all the novel implementations will be released as such, including supporting documentation. It is relevant now to mention that the source code of DualSPHysics is redistributed under the terms of the GNU Lesser General Public License (LGPL), the most favourable to attract industry usage.

Research papers will target peer-reviewed forums, endorsing Open Access with CC BY-NC-ND 4.0 (Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International). The costly publishing fees will be covered by UU, which has publish agreements with all the targeted journals.

The *DiVA* -- Academic Archive Online -- is a system for electronic publishing developed and maintained by UU Library and will be employed to securely store long-term data, and share, using a standard mechanism (DOI); data will be distributed under the Creative Commons (CC) license. Data repositories concerning the dissemination activities will always be made accessible during the review processes, thus improving third-party *accessibility* to procedures and data. Note that the data generated with items of direct interest to Hexicon **will not be made available** due to high-level non-disclosure agreement (NDA). A data management system will be arranged to provide the primary platform of data delivery to other researchers and the public, fulfilling the EU data requirements in accordance with FAIR (Findable, Accessible, Interoperable, and Reusable) principles. The Researcher will set a **Data Management Plan** (DMP) using the digital tool *DMPonline* provided by the UU data office, to create, update, and share the DMP.

Should the results produced during this fellowship have a commercial potential, their exploitation and protection will be discussed and with Hexicon and advisors from the UU Innovation (UUI), which provides support to researchers on **Intellectual Property** (IP) issues.

### Quality of the supervision, training and of the two-way transfer of knowledge between the researcher and the host

Malin Göteman is an Associate Professor at the Department of Electrical Engineering @ UU and will supervise IM-POWER. She has been the Deputy Director of the Centre of Natural Hazards and Disaster Science (CNDS) since 2016, a leading research centre in Sweden that brings together scientists and researchers from engineering, social and earth sciences to work together on collaborative projects on natural hazards, socio-technological vulnerabilities, and societal security. Prof. Göteman's research focuses on marine energy technologies, specifically, wave energy and offshore resilience. She has over 10 years of experience in theoretical, numerical, and physical modeling applied to renewable energy devices. She has published 56 research articles in peer-reviewed international journals and 30 papers in influential conference proceedings (*h*-index 15 based on Scopus). She has strong expertise in leading and coordinating large research collaborations. Prof. Göteman and has supervised five Ph.D. theses and more than 10 Master's graduations.

Prof. Göteman is highly qualified to supervise Dr. Tagliafierro during this Action due to her expertise that partly overlaps and partly complements the Researcher's background. She is an expert as well in using mesh-based CFD tools and survivability offshore renewable energy structures, and so can exercise extensive control over the tasks associated with numerical methodologies. The activities of this Action are in close connection to a project for the *Resilience of the electric grid with increased dependencies on offshore renewable energy systems*, proposed by a consortium of academic and industrial partners led by Prof. Göteman, and that aims to participate in a Horizon Europe project within the call *Disaster Resilience Society 2022*. Prof. Göteman, at the start of the Action, will compile the **Career Development Plan** (CDP) providing a detailed description of the training activities.

Dr. Victor Mendoza is a mechanical engineer and has been collaborating with the Dept. of Electrical Engineering @ UU since 2018. In 2020, Dr. Mendoza joined the R&D division as Project Engineer at Hexicon. Dr. Mendoza has specialised in the design of offshore wind farms and floating platforms for wind turbines. He will supervise the Researcher during his 6-month secondment in Stockholm and guide the fellow's professional development until the end of the Action.

#### Training and two-way transfer of knowledge

**Host to Researcher:** *Training-through-research* will strengthen the candidate's standing as expert in numerical modelling and structural design. Moreover, the Researcher will receive top-notch training and be enrolled in an individual personalized program that, starting from the candidate's current know-how, will provide him with competence on the relevant topics to effectively take the Action to completion. In particular, four activities are identified, mostly concentrated at the beginning of the fellowship period:

- **Courses:** The candidate will audit relevant lectures, and will be provided with the relevant material. The activities include the candidate's attendance in eight modules (80 hours) from the courses *Wind Power - Technology and systems*, *Introduction to power computer control systems*, and *Analysis of power distribution grid*. The aim here is to inform the candidate on the relevant and most common techniques to manage wind turbine components, and power grid management base principles. Note that the Researcher has already experience in CFD methods and structural dynamics.
- **Personalized short seminars:** The five experts who compose GoP will supply short one-to-one intense classes focused on issues that need to be addressed. Each member will supply 10 hours of seminar in total.
- **Professional training:** Dr. Tagliafierro will work for six months at Hexicon on two main research issues: firstly, to tackle the design of offshore steel structures (offshore platforms) and their anchoring systems using well-established engineering principles. Secondly, to arrange FOWT parks with power output of 500 MW, comprising mooring connections and power cable inter-connectivity. The Researcher will take three professional update seminars that are usually provided by Hexicon to its employees.
- **Transferable skills:** Dr. Tagliafierro will receive training and coaching organized at the host's premises on: time and stress management (management skills); gender perspectives in research projects (gender related issues); leadership and people management (interpersonal competencies). The training will in part be in the form of a mentorship program for young researchers, in which Dr. Tagliafierro will participate. Lastly, he will have for the first time the chance to lead and manage a project of this breadth, providing him experience that will open career prospects at managerial levels both in academia and in commercial or industrial companies.

**Researcher to Host:** Dr. Tagliafierro, from his side, will transfer to the partner organization his strong expertise in CFD methods, and his experience in the design of steel structures. This will be pursued by participating in the half-term research reviews (6 in total) that are arranged at the Division of Electricity, involving more than 20 Ph.D. students. Thanks to the targeted code development, the candidate will establish new relationships between the software developer teams he collaborates with EPhysLab (University of Vigo, Spain), and the Simulation-Based Engineering Lab (SBEL @ UW-Madison, WI), and the working group at UU. All of them are interested, with different perspectives, in improving the profitability of renewable energy devices.

### Quality and appropriateness of the researcher's professional experience, competences and skills

Dr. Tagliafierro is a civil engineer and architect, who earned his doctorate at the University of Salerno (Italy) in *Risk and Sustainability in Civil, Architectural and Environmental Engineering Systems*. Since 2019, he has been collaborating with EPhysLab as a fellow researcher and has joined the DualSPHysics code project. Of relevance for the scope of this Action, the candidate's research has aimed to promote the use of high-fidelity computational frameworks to support the design of early-stage development phases of wave energy converters (WECs). In particular, the latest research has been performed in cooperation with the host on the validation and investigation of a point-absorber WEC with different methods to model extreme wave conditions.

The Researcher is self-motivated, has an adequate level of professional maturity, and has demonstrated his ability to work independently, having received research funding from European Agencies to pursue and promote his research objectives. He has been able to quickly fit into research teams and make the most of his collaborations with them, proved by the research papers published as a result of each project he has led (four). Furthermore, the candidate is perfectly suited for tackling the code development envisioned by this Action for RO2 since he is a code developer for the *DSPHChronoLib*, a piece of code that transfers information between DualSPHysics and Chrono. A final observation on Dr. Tagliafierro's suitability is due: he was awarded a 6-month *Fulbright Schuman Research Fellowship* to develop a Project Chrono implementation for control algorithms in renewable energy devices. This work will affect the very software that will be used during this Action and the strong relationship that will be developed with the SBEL team will certainly add value to the objectives of this Action.

## Impact {\color{gray1}{\footnotesize{\#@IMP-ACT-IA@\#}}}

### Credibility of the measures to enhance the career perspectives and employability of the researcher and contribution to his/her skills development

Dr. Tagliafierro's fellowship at UU will be the ideal stage to prove and reinforce his professional maturity and independence, to become an leading international actor in a newly established research area. In the next decade, most of the power grid will see a reconfiguration process to keep up with the skyrocketing electricity demand (baseline increase EU-27 final 157% by 2050), and the profile developed by the Researcher during IM-POWER will appeal to administrations and stakeholders. The Host and the Associated Partner will provide a springboard effect to enhance the visibility of Dr. Tagliafierro in Europe and beyond, and, more relevantly, with leading companies in the sector of renewable energy management and development, such as SINTEF (Norway). The candidate's training/research activities in Stockholm with a team that comprises more than 40 employees will provide him with experience in the design practices and modelling techniques integrated into real engineering routines to cope with offshore wind energy. Considering that the computational fluid dynamics (CFD) market alone is currently growing at 13%, experienced and skilled researchers with a solid background in applied research are likely to benefit and find more possibilities in this new developing labour market.

### Suitability and quality of the measures to maximise expected outcomes and impacts, as set out in the dissemination and exploitation plan, including communication activities

{\color{gray1}{\footnotesize{\#@COM-DIS-VIS-CDV@\#}}}

The commencement of the project will be **communicated** to the general public by using dedicated media channels (website, Twitter account, YouTube channel, all with name and logo of the Action) through which the scope and the main objectives will be publicized, and updated monthly with details on the project progress and outcomes. The results of this Action will be **disseminated** through peer-reviewed scientific papers, targeting journal forums covering research on energy engineering and power grid design (e.g., Ocean Engineering, Applied Energy) for RO1, whereas journals on computational methods for engineering problems (e.g., Computer Physics Communications) will be targeted for RO2. Moreover, the international conferences and workshops in Table 1 will be aimed to promptly divulge the code development achievements and gather feedback on them; preliminary results of RO1 will be presented as well.

**Exploitation** of results and outputs will be carried out through the following activities:

- A public git-based repository (e.g., GitHub), with the details on the implementation (known as *wiki*), set and maintained to increase the visibility and provide feedback to the Researcher (two-way activity);
- The release of a new package of DualSPHysics containing template cases to simulate FOWTs, which will also be supported (and relayed) by the Project Chrono core developers; and
- Continuing Professional Development (CPD) courses to train engineers and scientists in the use of the developed numerical tool. The outreach courses will comprise a 4-hour module given by the Researcher during the activities of the DualSPHysics team ([dual.sphysics.org/training/](https://dual.sphysics.org/training/)).

The dissemination and exploitation activities will aim to increase the visibility of the scientific progress of the Action, to obtain feedback for future improvements, and to enhance the awareness on the troublesome relationship between renewable energy sources and power grid reliability, thereby ensuring the continuity of the research line.

Table 1: Dissemination and outreach activities of the Action. *When* indicates the scheduled month.

| Activity | Type | When | Where |
|----------|------|------|-------|
| ... | ... | ... | ... |

### The magnitude and importance of the project's contribution to the expected scientific, societal and economic impacts

#### Expected scientific impact

The results of the Action will have a great impact on  the two scientific disciplines the project hinges on. First, it impacts the current software fleet for the simulation of FOWTs with CFD tools. The code container DualSPHysics has received more than 50,000 downloads in the last two years, and at the same pace, and considering the wider field of application, it will guarantee mid- and long-term efficacy to this Action, with an estimation of **100,000 downloads** in the two-year period following the first code release (M7). The proposed protocol that would allow predicting the power output of floating wind farms under a set of environmental constraints will be **highly important, and timely,** due to the need for new research to produce practical recommendations/guidelines for the installation/refurbishment process that power grids have been undergoing as a result of the changing global energy policy and market.

#### Societal impact

The project provides sensible, although difficult to quantify, contributions to the understanding, and thus to the better design of energy distribution systems especially against extreme weather events. The importance of power grids to the functioning of our society cannot be understated: in 2009 the so-called *Continental Synchronous Area* served 400 million people from more than 20 European countries with a production capacity of almost 700 GW (1.75 kW/per capita). By anticipating the impact of storms on farms' power output, better grid planning can enhance preparedness and management of extreme events for a more disaster-resilient society (Horizon Europe – Disaster-Resilient Society – 2022). Moreover, due to the impact of the project on the LCOE for offshore wind, the Action promotes renewable energy sources, in line with the 2030 Agenda for Sustainable Development (UNESCO), contributing to the knowledge-based economy and society. The outcomes of the present project are directly relevant to Goal #7 (Affordable and clean energy) and Goal #13 (Climate action).

#### Towards technological/economic impact

IM-POWER has a twofold positive impact on the LCOE of offshore wind. First of all, it has been identified that increasing the rated power (upsizing) of turbines and plant capacity can reduce the LCOE by about 23%. Thus, the CFD code development envisioned by this Action can support research on bigger wind turbines installed on floating platforms so that their performance can be anticipated. Additionally, it is important to mention that more than 50% of the installation capital costs for wind turbines is taken up by foundation construction and maintenance (only 25% by the turbine). The results of the Action can help optimize the supporting structures, thus delivering more overall economic feasibility.

Second of all, the project main outcome will provide useful knowledge to **strengthen grid reliability**. Grid inter-connectivity is tremendously important since it comes with several technical advantages that offshore wind sources would need to improve their cost effectiveness: especially the possibility of balancing loads at great distances. This is relevant also for the additional €29 billion of investment that REPowerEU will put into the power grid by 2030, to accommodate the increased use and production of electricity.



## Quality and Efficiency of the Implementation

### Quality and effectiveness of the work plan, assessment of risks and appropriateness of the effort assigned to work packages

The action comprises a 24-month fellowship at UU, with a 6-month secondment at Hexicon head-quartered in Stockholm, Sweden. The secondment will take place in two separate periods, to comply with the needs of the training/research schedule envisaged by this Action. The project is organized in five interrelated Work Packages (WPs) regarding project management and training (WP1-WP2), science development (WP3-WP4), dissemination and public engagement (WP5); the WPs comprise different tasks (**T**) and deliverables (**D**). Encompassing the activities, three major Milestones (**M**) are identified along with the WPs. Figure 2 illustrates the project schedule, presenting the temporal correlations among the various WPs and tasks. Figure 3 schematically depicts the flow of events, supporting the technical WPs' description. The action implementation strategy is presented and described in Table 2.

![Figure 2: Gantt chart showing the Action's activities displayed against time](gantt_chart.png)

![Figure 3: Schematic flowchart for the proposed multi-tier approach to simulate wind farms](flowchart.png)

Table 2: Action implementation strategy

| Work Package | Description | Tasks | Deliverables |
|--------------|-------------|-------|--------------|
| WP1 | ... | ... | ... |
| WP2 | ... | ... | ... |
| Work Package | WP3 | Development and implementation | Months M3-M10 | *6 person-months* |
|--------------|-----|--------------------------------|---------------|-------------------|

Implementation of new software in an open-source CFD solver to cope with wind forces and electromechanical loads on wind turbines. The control and electrical systems, which comprise the actuators of the blade-pitch controller, the generator, and power-converter components of the electrical drive motor, will be simulated within the same time-integrated numerical framework. Tool 1 and Tool 2 will be validated using analytical and experimental references, and finally embedded within the DualSPHysics program (including an end-user interface). The various algorithms and feedback systems will be discussed in collaboration together with the Supervisor and the GoP.

**T3.1** Identification of mainstream and novel control algorithm for power generators embedded in wind turbines. Theoretical investigation of the blade element momentum (BEM) method for horizontal axis wind turbines.

**T3.2** Software implementation and validation of the new functionalities as separated sets of instructions (called *Classes*) in Project Chrono to simulate active control systems within the main solver DualSPHysics.

**T3.3** Numerical SPH setup to model wave-platform interaction, parametrically defined to accommodate various platform/mooring system configurations. Numerical model validation with regular waves and constant wind profiles.

**D3.1** Release of new software to be included in the DualSPHysics package (GitHub repository); **D3.2** Preparation of template cases for the setup and simulation of different platform configurations.

**M1** Successful validation of the novel implementations in the DualSPHysics code.
| Work Package | WP4 | Design, simulation, and data collection | Months M11-M22 | *7 person-months* |
|--------------|-----|------------------------------------------|----------------|-------------------|

Characterization of the site and environmental conditions (storm parameters for wave and wind definitions), which are then used to define the local wave/wind time series. The prediction of the power output of a whole farm using running a single CFD code instance per each wind turbine. For each wind farm layout, all the FOWTs are simulated in single code instances.

**T4.1** Arrangement of offshore wind farm layouts: three different platform configurations: i) tension-leg, ii) semi-submersible, and iii) semi-submersible with double-wind turbine design of an array of FOWTs using consolidated practices.

**T4.2** The depth-integrated SWASH software (https://swash.sourceforge.io/) is used for wave propagation in the farm area; wind propagates in a atmospheric domain overlapping the area of interest with the mesh-based solver OpenFOAM (https://openfoam.org/).

**T4.3** Total power output computed using the outputs of the CFD simulations for each wind turbine on the farm. Computational resources made available by UU @ Swedish National Infrastructure for Computing (SNIC) system will be used (ref. to Section 3.2). The dataset will be compiled into a searchable structure and will contain all the source data (model input files) for the sake of reproducibility.

**D4.1** Report and Program tools: farm design procedure; **D4.2** Database: local wave/wind condition time evolution for wind turbines; **D4.3** Database: numerical simulations output and metadata (source files).

**M2** Completion of all the CFD simulations for the wind farms and data collection.
| WP5 | ... | ... | ... |




#### Risk management

Risk monitoring and control will be addressed monthly and, if required, detours will be taken to respond to any specific risks or delays. Meetings will take place every two weeks with the Supervisor to follow up the execution of the project in compliance with the grant agreement. Possible research risks and mitigation measures have been reported in Table 3. Most of the administrative issues and related aspects, such as the allocation of resources and the details on the schedule implementation have been settled during a 3-week stay that Dr. Tagliafierro performed @ UU (funded by UU), thereby minimizing the risks related to bureaucratic aspects. Finally, it is worth mentioning that in case of limitations to travel or presential activities (pandemic, adverse weather conditions), interactive activities will take place using virtual conferences, webinars, and online networking in place of in-person events whenever the efficacy of them is not altered.

Table 3: Risk management: identification and proposed mitigation actions

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| ... | ... | ... | ... |

### Quality and capacity of the host institutions and participating organisations, including hosting arrangements

The Dept. of Electrical Engineering comprises more than 60 senior researchers and almost 30 Ph.D. students, with competences that cover wave/wind energy exploitation, power grid design, and novel methods for wind turbines. The integration of Dr. Tagliafierro will be facilitated by the fact that the whole department staff shares the same relax area/lunch room, and by frequent review activities and students supervision. The Researcher has already started his integration since he visited the host for 3 weeks during summer to finalize the IM-POWER proposal and to meet the Supervisor and the GoP. The Researcher will be given access to personal office space and have access to the GPU-based HPC that allows for green-computation tasks. UU provides support to the researchers with EU support and EU economy experts, Uppsala University Innovation, legal dept. in all financial and administrative tasks. The International Faculty and Staff Services @ UU, a EURAXESS Centre, will help Dr. Tagliafierro integrate into Swedish society, including participation in social and cultural events. UU has received the European Commission's acknowledgment *Excellence in Research* (HR), indicating that the employer has a stimulating working environment.

The GoP, coordinated by the Supervisor, will support and complement the supervision and the investigation activities of the candidate throughout the Action's implementation. Each member is an expert, validated by research papers in top-ranked peer-reviewed journals, in a disciplinary sector of interest to this Action; they will be providing guidelines and feedback, referring Dr. Tagliafierro to state-of-the-art publications, literature, methods, and software. Details about the group are given below:

- **Janaina Goncalves de Oliveira** Senior Lecturer and Ass. Prof.; experience in electrical engineering, with emphasis on control systems and power electronics applied to energy storage.
- **Hans Bernhoff** Ass. Prof. in the Division of Electricity. An expert in energy wind technology and numerical methods for wind turbine. Chief technology officer (CTO) of the *World Wide Wind AS* (Norway).
- **Anders Goude** Dept. of Engineering Sciences. Has developed a number of new computer programs and scripts for simulating wind turbines. An expert in computational physics and fluid dynamics.
- **Karin Thomas** Senior Lecturer and Ass. Prof. in Division of Electricity. Researches on the balancing techniques for power grid stability, and the power grid fluctuation when plugging in marine current turbines.
- **Mikael Bergkvist** Senior Lecturer and Ass. Prof. in Division of Electricity. Main lines of research on the assessment of power grid weaknesses when share of renewable energy resources goes beyond 70%.

The associated partner, **Hexicon AB**, is a world-leading company in the emerging sector of offshore floating wind. Hexicon will provide access to the company's private database (with an NDA) for the dual-turbine platform TwinWind™. The participation of Hexicon comprises the Researcher's work activities in Stockholm, but will also include continuous collaboration with the supervisor Dr. Victor Mendoza starting from M4 till the end of the Action, and due to Dr. Mendoza's affiliation at UU, the research team will have the chance to interact from day one. Note that the travel to and from Stockholm, strongly endorsed by this Action to boost the Researcher's skills, will in line with the MSCA Green Charter leave a small carbon footprint since the commute journey will consist of the use of bike and train.