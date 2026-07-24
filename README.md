# Simulation of Stoichiometric Nutrient Cycles for the PLANT-B CubeSat Terrarium Mission

## Project Background

This repository was initially created by Livian Von Dran—one of the entomologists for the PLANT-B CubeSat Terrarium Mission—as part of their final project for their Professional Graduate Certificate in Earth Data Analytics program at the University of Colorado Boulder.  In an effort to support The Spring Institute's mission of creating a self-sustaining terrarium ecosystem that can function in space without outside intervention, this repository was created to simulate carbon and nitrogen cycles that will happen inside the PLANT-B terrarium. 

The PLANT-B CubeSat Terrarium Mission is a project by The Spring Institute for Forests on the Moon to send a bioactive—or self-sustaining—terrarium on a satellite into low-Earth orbit (LEO) for two to five years. The PLANT-B acronym stands for <b>P</b>assive <b>L</b>ight <b>a</b>nd <b>N</b>utrient <b>T</b>errarium-<b>B</b>iosphere, representative of the system's passive operations; the satellite is engineered to passively light and heat the 0.7 L terrarium. Additionally, soil will not be used in the final terrarium design to reduce the payload weight. Inhabited by a plant and numerous microorganisms, this terrarium is unique in that it is one of the first attempts to maintain a self-sustaining, Earth-like ecosystem directly in the space environment; terrarium experiments have been conducted on the the International Space Station (ISS), but true biological payloads are rare, especially on satellites. By incorporating multiple trophic levels, the terrarium ecosystem grants us insight into the functioning of closed ecological life support systems—a biological space life support system that also incorporates multitrophic species assemblages to replenish life-sustaining resources for and maintain the habitability of a closed system. When space settlements become a reality, prospective inhabitants must be able to replenish their own resources to reduce dependence on resupply flights.

The influence of low-Earth orbit will pose two primary challenges to the terrarium's inhabitants: microgravity and rapidly shifting 60-30 minute light-dark cycles—similar to the daylight cycle occupants of the ISS experience. The chosen invertebrates—*Trichorhina tomentosa* and *Folsomia candida*—are common fixtures in bioactive terrariums, serving as the detritivorous clean up crew that break down waste like feces and mold. These detritivores will play an essential role in removing the leaf litter of *Physcomitrium patens*, the primary producer candidate for the terrarium. This moss species is known for its remarkably resilient spores, which are capable of germinating after surviving in the vacuum of space for over nine months (Maeng et al., 2025). Unfortunately, this tolerance has its limits; the light cycle is anticipated to negatively impact the circadian rhythms of all organisms in the terrarium,  and as a C3 plant, *P. patens* may have difficulty continuously "restarting" photosynthesis; a study found that LEO daylight cycles inhibit plant development and photosynthetic productivity (Kalbacher & Gonzalez, 2016). Similarly, as *P. patens* is more photosynthetically productive in stronger-than-Earth gravity, microgravity is expected to inhibit photosyntesis (Takemura et al., 2016). It is difficult to infer how the space environment will impact the invertebrates because no space experiments involving isopods or springtails exist, but *F. candida* exhibits some light dependent movement behaviors (Ruiz et al., 2017). The true impact of the space environment cannot be quantified until physical experiments are complete, but the terrarium ecosystem is anticipated to be less productive than an identical exosystem on Earth.

## Notebooks and Data Background

<ins>Notebook Parts</ins>

The coding pipeline for the project can be found in the "notebooks" folder. Three separate notebooks have been created to correspond to the three phases of the project and are numbered to indicate the correct order for which they should be run. 

The first notebook that should be run is "part-1-soil-habitats.ipynb." The purpose of this notebook is to determine appropriate soil nutrient concentrations in the area of habitat overlap for the PLANT-B species. The downloaded data comes from the Global Biodiversity Information Facility (GBIF) and the LUCAS 2018 TOPSOIL dataset from the European Soil Data Centre (ESDAC). At present, GBIF is the only database whose data was able to be downloaded through a function; ESDAC's LUCAS 2018 Topsoil Dataset requires a request to be submitted at https://esdac.jrc.ec.europa.eu/content/lucas-2018-topsoil-data#tabs-0-description=1.

The second notebook that should be run is "part-2-gathering-stoichiometric-variables.ipynb." The purpose of this notebook is to use the StoichLife dataset to determine the elemental composition of PLANT-B's three target species. Like ESDAC's dataset, the StoichLife dataset cannot be downloaded with a function; instead, it can be accessed and downloaded at https://datadryad.org/dataset/doi:10.5061/dryad.3tx95x6r2.

The third notebook that should be run is "part-3-simulating-nutrient-cycles.ipynb." The purpose of this notebook is to model population growth for the invertebrates and construct stoichiometric chemical equations to model the carbon and nitrogen cycles inside the terrarium. This notebook is still under construction.

<ins>Data Sources Background</ins>

<ins>GBIF</ins>

Observation data from GBIF was used to find an area of habitat overlap  An appropriate overlap area was found near the German-Polish-Czech border, but other locations are being examined to increase data diversity.

<ins>ESDAc</ins>

The dataset being used from ESDAC is the LUCAS 2018 TOPSOIL dataset. This dataset was used to find nutrient concentrations from a soil sample taken in the habitat overlap area. This provides a baseline for starting nutrient concentrations in an environment where the three selected species can coexist.

<ins>StoichLife Database</ins>

The StoichLife data was used to determine carbon and nitrogen concentrations in closely related species *T. tomentosa*, *F. candida*, and *P. patens*. 

## Repository Replication Instructions

This repository's data was originally processed in the earth-analytics-python environment found in [this repository](https://github.com/earthlab/earth-analytics-python-env). A tutorial to set up this Conda environment can be found at [this link](https://earthdatascience.org/workshops/setup-earth-analytics-python). An updated yml with a new environment has been added to this repository and was tested using the instructions below to ensure it functions correctly.

1. Download the installers for [Git Bash](https://git-scm.com/install/windows) and [Miniconda](https://www.anaconda.com/download/success). Run both installers.
2. Open the Git Bash terminal. Run the below commands in sequence:
   
   a.  mkdir PLANT-B-Terrarium

   This creates a directory called "PLANT-B-Terrarium."
   
   b. cd earth-analytics
    
      mkdir data

   This changes your working directory to "PLANT-B-Terrarium" and creates a directory inside it called "data."
   
3. Create a fork of [this repository](https://github.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation).
4. Return to Git Bash and run the below commands in sequence:
   
   a. cd ~

   This refreshes your working directory to default.
   
   b. cd PLANT-B-Terrarium

   This makes PLANT-B-Terrarium your working directory again.
    
   c. git clone https://github.com/[YOUR-GITHUB-USERNAME]/PLANT-B-Nutrient-Cycle-Simulation

   This clones your forked directory and downloads it to your computer.
   
   d. cd PLANT-B-Nutrient-Cycle-Simulation

   This turns "PLANT-B-Nutrient-Cycle-Simulation" into your working directory.

   e. conda env create -f environment.yml

   This creates the "plant-b-simulation-env" environment using the yml file.

   f. conda activate plant-b-simulation-env

   This activates the newly created Python environment.
   
5. Download and run the [Visual Studio Code installer](https://code.visualstudio.com/download) and [GitHub Desktop installer](https://desktop.github.com/download/). Open GitHub Desktop and create a copy of the PLANT-B-Nutrient-Cycle-Simulation directory in the data folder inside PLANT-B-Terrarium. You should now be able to open the repository in Visual Studio Code.

## DOI and Licensing

This repository is private. A fully public release of the finalized repository may be made at the discretion of The Spring Institute. 

The current license is a temporary placeholder. Unauthorized redistribution, replication, or alteration of the source code is strictly forbidden.

## Bibliography

<ins>Data Sources</ins>

Bílá, K., Moretti, M., de Bello, F., Dias, A. T. C., Pezzatti, G. B., Van Oosten, A. R., & Berg, M. P. (2014). Disentangling community functional components in a litter‐macrodetritivore model system reveals the predominance of the mass ratio hypothesis. *Ecology and Evolution*, *4*(4), 408–416. https://doi.org/10.1002/ece3.941

Boominathan Mohanasundaram, Koley, S., Allen, D. K., & Pandey, S. (2023). *Physcomitrium patens* response to elevated CO2 is flexible and determined by an interaction between sugar and nitrogen availability. *New Phytologist*, *241*(3), 1222–1235. https://doi.org/10.1111/nph.19348

Fernandez-Ugalde, O, Scarpa, S, Orgiazzi, A., Panagos, P., Van Liedekerke, M., Marechal A., & Jones, A. (2022). *LUCAS 2018 soil module - Publications Office of the EU*. Publications Office of the EU. https://doi.org/10.2760/215013

GBIF.org. (2026a) *Folsomia candida* GBIF Occurrence Download. https://doi.org/10.15468/dl.7x6zk3

GBIF.org. (2026b). *Physcomitrella patens* GBIF Occurrence Download. https://doi.org/10.15468/dl.j2xmrk

GBIF.org. (2026c). *Trichorhina tomentosa* GBIF Occurrence Download. https://doi.org/10.15468/dl.y76gsf

González, A. L., Merder, J., Andraczek, K., Brose, U., Filipiak, M., Harpole, W. S., Hillebrand, H., Jackson, M. C., Jochum, M., Leroux, S. J., Nessel, M. P., Onstein, R. E., Paseka, R., Perry, G. L. W., Rugenski, A., Sitters, J., Sperfeld, E., Striebel, M., Zandona, E., Aymes, J.-C., Blanckaert, A., Bluhm, S. L., Doi, H., Eisenhauer, N., Farjalla, V. F., Hood, J., Kratina, P., Labonne, J., Lovelock, C. E., Moody, E. K., Mozsár, A., Nash, L., Pollierer, M. M., Potapov, A., Romero, G. Q., Roussel, J.-M., Scheu, S., Scheunemann, N., Seeber, J., Steinwandter, M., Susanti, W. I., Tiunov, A., & Dézerald, O. (2025). StoichLife: A Global Dataset of Plant and Animal Elemental Content. *Scientific Data*, *12*(1). https://doi.org/10.1038/s41597-025-04852-w

González, A. L., Merder, J., Andraczek, K., Brose, U., Filipiak, M., Harpole, W. S., Hillebrand, H., Jackson, M. C., Jochum, M., Leroux, S. J., Nessel, M. P., Onstein, R. E., Paseka, R., Perry, G. L. W., Rugenski, A., Sitters, J., Sperfeld, E., Striebel, M., Zandona, E., Aymes, J.-C., Blanckaert, A., Bluhm, S. L., Doi, H., Eisenhauer, N., Farjalla, V. F., Hood, J., Kratina, P., Labonne, J., Lovelock, C. E., Moody, E. K., Mozsár, A., Nash, L., Pollierer, M. M., Potapov, A., Romero, G. Q., Roussel, J.-M., Scheu, S., Scheunemann, N., Seeber, J., Steinwandter, M., Susanti, W. I., Tiunov, A., & Dézerald, O. (2025). StoichLife: A global database of plant and animal elemental content [Dataset]. *Dryad*. https://doi.org/10.5061/dryad.3tx95x6r2

Heeley, W. (1941). Observations on the Life-Histories of some Terrestrial Isopods. *Proceedings of the Zoological Society of London*, *B111*(1–2), 79–149. https://doi.org/10.1111/j.1469-7998.1941.tb00044.x

Huotari, N., Tillman-Sutela, E., & Kubin, E. (2009). Ground vegetation exceeds tree seedlings in early biomass production and carbon stock on an ash-fertilized cut-away peatland. *Biomass and Bioenergy*, *33*(9), 1108–1115. https://doi.org/10.1016/j.biombioe.2009.05.009

Panagos, P., Van Liedekerke, M., Borrelli, P., Köninger, J., Ballabio, C., Orgiazzi, A., Lugato, E., Liakos, L., Hervas, J., Jones, A., & Montanarella, L. (2022). European Soil Data Centre 2.0: Soil data and knowledge in support of the EU policies. *European Journal of Soil Science*, *73*(6), e13315. https://doi.org/10.1111/ejss.13315

Snider, R. M., & Butcher, J. W. (1973). The Life History of *Folsomia Candida* (Willem) (Collembola: Isotomidae) Relative to Temperature. *The Great Lakes Entomologist*, *6*(4), 97-106. https://doi.org/10.22543/0090-0222.1187

Xie, L., Duan, X., Norouzi, S., de Jonge, L. W., & Topping, C. J. (2026). Integrating spatial and environmental stressors in a population model of *Folsomia candida* (Collembola, Isotomidae): a Formal Model within ALMaSS framework. *Agricultural and Environmental Modelling*, *8*, e184962. https://doi.org/10.3897/aem.8.184962

<ins>Text Citations</ins>

Gallardo Ruiz, M., Le Galliard, J.-F., & Tully, T. (2017). Genetic variation in light vision and light-dependent movement behaviour in the eyeless Collembola Folsomia candida. *Pedobiologia*, 61, 33–41. https://doi.org/10.1016/j.pedobi.2016.12.001

Kalbacher, K. T., & Gonzalez, E. N. M. (2016). Analysis of a Low Earth Orbit Photoperiod on the Development of Aquaponic Lettuce. *AIAA 2016-5352*. https://doi.org/10.2514/6.2016-5352

Maeng, C., Hiwatashi, Y., Nakamura, K., Matsuda, O., Mita, H., Tomita-Yokotani, K., Yokobori, S., Yamagishi, A., Kume, A., & Fujita, T. (2025). Extreme environmental tolerance and space survivability of the moss, *Physcomitrium patens*. *IScience*, *28*(12), 113827. https://doi.org/10.1016/j.isci.2025.113827

Takemura, K., Hiroyuki Kamachi, Kume, A., Fujita, T., Ichirou Karahara, & Hanba, Y. T. (2016). A hypergravity environment increases chloroplast size, photosynthesis, and plant growth in the moss Physcomitrella patens. *Journal of Plant Research*, *130*(1), 181–192. https://doi.org/10.1007/s10265-016-0879-z

Sürmen, B., Kutbay, H. G., Kılıç, D. D., Huseynova, R., & Kilinç, M. (2014). Ellenberg’s indicator values for soil nitrogen concentration and pH in selected swamp forests in the Central Black Sea region of Turkey. *Turkish Journal of Botany*, *38*(5), 883–895. https://doi.org/10.3906/bot-1311-43



