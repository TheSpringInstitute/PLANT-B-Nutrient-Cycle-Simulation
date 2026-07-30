# Simulating Carbon and Nitrogen Cycles for a Space Terrarium

![The Spring Institute for Forests on the Moon logo.](https://github.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/blob/main/img/The_Spring_Institute_Logo.png)

## Mission Overview

The PLANT-B CubeSat Terrarium Mission is a project by The Spring Institute for Forests on the Moon to send a bioactive—or self-sustaining—terrarium on a satellite into low-Earth orbit (LEO) for two to five years. PLANT-B is an acronym that stands for Passive Light and Nutrient Terrarium-Biosphere, representative of the system's passive operations; the satellite is engineered to passively light and heat the 0.7 L terrarium. Inhabited by a plant and numerous microorganisms, this terrarium is unique in that it is one of the first attempts to maintain a self-sustaining, Earth-like ecosystem directly in the space environment; terrarium experiments have been conducted on the the International Space Station (ISS), but true biological payloads are rare, especially on satellites. By incorporating multiple trophic levels, the terrarium ecosystem grants us insight into the functioning of closed ecological life support systems (CELSS)—a biological space life support system that also incorporates multitrophic species assemblages to replenish life-sustaining resources for and maintain the habitability of a closed system (Grove, 2023). When space settlements become a reality, prospective inhabitants must be able to replenish their own resources to reduce dependence on resupply flights.

![An early PLANT-B terrarium prototype showing the spiral of Hygrolon the moss will grow on.](https://github.com/TheSpringInstitute/PLANT-B-Stoichiometric-Nutrient-Cycle-Simulation/blob/main/img/PLANT-B_Prototype.JPG)

To create a self-sustaining terrarium ecosystem that can function in space without outside intervention, all ecological processes must be accounted for. The "PLANT-B Nutrient Cycle Simulation" GitHub repository was developed to simulate the terrarium ecosystem's carbon (C) and nitrogen (N) cycles. Initial simulations will provide a baseline reference point for understanding how nutrients flow throughout the terrarium ecosystem.

## Meet the Residents

The LEO environment will pose two main challenges to the terrarium's inhabitants: rapidly shifting light-dark cycles and microgravity. The orbital path dictates that the sealed ecosystem will be subject to rapidly shifting 60-30 minute light-dark cycles—similar to the daylight cycle occupants of the ISS experience. Additionally, if the ISS is used as a reference point, the terrarium will experience gravity at 89% the strength of Earth's gravity at sea level; this will not be felt by the terrarium's occupants because the orbit will cause the terrarium to be in a state of constant freefall (National Aeronautics and Space Administration, 2015).

When conducting space experiments with biological organisms, a great degree of uncertainty is anticpated due to limited data, which is why model organisms are commonly used. One such model organism is *Physcomitrium patens*. This moss was selected as the producer for the terrarium because of its remarkably resilient spores, which are capable of germinating after surviving in the vacuum of space for over nine months (Maeng et al., 2025). Regrettably, this resilience has its limits; a study found that LEO daylight cycles inhibit plant development and photosynthetic productivity, and as a C3 plant, *P. patens* may have difficulty continuously "restarting" photosynthesis (Kalbacher & Gonzalez, 2016). *P. patens* is more photosynthetically productive in stronger-than-Earth gravity, so microgravity is expected to inhibit photosyntesis (Takemura et al., 2016).

![A cluster of Physcomitrium patens. Photo by Pirex at Wikimedia Commons.](https://upload.wikimedia.org/wikipedia/commons/d/dd/Physcomitrella.jpg?_=20101210214832)

*Trichorhina tomentosa* and *Folsomia candida* were the chosen invertebrates because they are common fixtures in bioactive terrariums, serving as the clean up crew that break down waste like feces and mold. Their primary role will be to break down the decomposing leaf litter of *P. patens*. It is difficult to infer how the space environment will impact these invertebrates because no space experiments involving isopods or springtails exist. *F. candida* is eyeless, but some of its movement behaviors are light dependent (Ruiz et al., 2017). It is reasonable to infer that the altered light-dark cycles will negatively impact the invertebrates' circadian rhythms. 

![Trichorhina tomentosa specimens in a test terrarium with soil. Frame taken from a video by Patrick Grove.](https://github.com/TheSpringInstitute/PLANT-B-Stoichiometric-Nutrient-Cycle-Simulation/blob/main/img/PLANT-B_Prototype.JPG)

## Gathering Data for the Simulation

To simulate carbon and nitrogen cycles, soil nutrient concentrations need to be known. To identify an appropriate area to take data from, observation data of *P. patens*, *T. tomentosa*, and *F. candida* was taken from the Global Biodiversity Information Facility (GBIF) and mapped out. This [interactive map](https://github.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/blob/main/plots/Interactive_PLANT-B_Species_Distribution_Plot.html) was used to identify an appropriate area of habitat overlap around the German-Polish-Czech border.

![PLANT-B species distribution near the German-Polish-Czech border.](https://github.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/blob/main/plots/PLANT-B_Species_Border_Distribution_Plot.png)

To gather soil nutrient data for the overlap area, a request was submitted to the the European Soil Data Centre (ESDAC) for the LUCAS 2018 TOPSOIL data. When data within the set bounding box was examined, only one relevant soil sample was found. This soil sample yielded a C:N—or carbon: nitrogen—ratio of 9.86:1, indicating an environment where decomposition will occur very rapidly. Per an inquiry to the TRY Plant Trait database, *Physcomitrium* species have a nitrogen Ellenberg Indicator Value of 6 or 7) (Kattge et al., 2020)—indicating a preference for moderately fertile, nitrogen-rich soils—which corresponds to a C:N ratio of 10:1 (Sürmen et al., 2014). The recorded values were used to calculate the absorbed nutrient quantitites present in the Hygrolon.

![Carbon and nitrogen concentrations in a soil sample in the overlapping habitat area.](https://github.com/TheSpringInstitute/PLANT-B-Stoichiometric-Nutrient-Cycle-Simulation/blob/main/plots/PLANT-B_Species_Overlapping_Habitat_OC_and_N_Concentrations_Plot.png)

The StoichLife dataset was used to determine carbon and nitrogen concentrations in *T. tomentosa*, *F. candida*, and *P. patens*. As the target species were not present in the dataset, it was filtered for closely related species, and carbon and nitrogen percentages were extracted. These percentages were used to determine starting carbon and nitrogen concentrations in the starting *T. tomentosa*, *F. candida*, and *P. patens* populations.

![Carbon and nitrogen compositions of the PLANT-B species by percent dry mass.](https://github.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/blob/main/plots/PLANT-B_Species_Dry_Mass_Elemental_Composition_Plot.png)



## References

Gallardo Ruiz, M., Le Galliard, J.-F., & Tully, T. (2017). Genetic Variation in Light Vision and Light-dependent Movement Behaviour in the Eyeless Collembola *Folsomia candida*. *Pedobiologia*, 61, 33–41. https://doi.org/10.1016/j.pedobi.2016.12.001

Grove, Patrick. (2023, June 30). *Comparing Life Support Solutions: PCLSS vs BLSS vs CELSS*. The Spring Institute for Forest on the Moon. https://thespringinstitute.com/comparing-life-support-solutions-pclss-vs-blss-vs-celss/

Kalbacher, K. T., & Gonzalez, E. N. M. (2016). Analysis of a Low Earth Orbit Photoperiod on the Development of Aquaponic Lettuce. *AIAA 2016-5352*. https://doi.org/10.2514/6.2016-5352

Kattge, J., Bönisch, G., Díaz, S., Lavorel, S., Prentice, I. C., Leadley, P., Tautenhahn, S.,Werner, G., et al. (2020). TRY plant trait database - enhanced coverage and open access. *Global Change Biology*, *26*(1), 119-188. doi.org/10.1111/gcb.14904.

Maeng, C., Hiwatashi, Y., Nakamura, K., Matsuda, O., Mita, H., Tomita-Yokotani, K., Yokobori, S., Yamagishi, A., Kume, A., & Fujita, T. (2025). Extreme environmental tolerance and space survivability of the moss, *Physcomitrium patens*. *iScience*, *28*(12), 113827. https://doi.org/10.1016/j.isci.2025.113827

National Aeronautics and Space Administration. (2015, February). *Microgravity Science on the ISS: A Primer for New Researchers* [PowerPoint slides]. https://www.nasa.gov/wp-content/uploads/2015/02/501343main_microgravity_science.pdf

Sürmen, B., Kutbay, H. G., Kılıç, D. D., Huseynova, R., & Kilinç, M. (2014). Ellenberg’s Indicator Values for Soil Nitrogen Concentration and pH in Selected Swamp Forests in the Central Black Sea Region of Turkey. *Turkish Journal of Botany*, *38*(5), 883–895. https://doi.org/10.3906/bot-1311-43