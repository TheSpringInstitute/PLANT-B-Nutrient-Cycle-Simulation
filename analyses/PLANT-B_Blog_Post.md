# Simulating Carbon and Nitrogen Cycles for a Space Terrarium

![The Spring Institute for Forests on the Moon logo.](https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/img/The_Spring_Institute_Logo.png)

## Mission Overview

The PLANT-B CubeSat Terrarium Mission is a project by The Spring Institute for Forests on the Moon to send a bioactive—or self-sustaining—terrarium on a satellite into low-Earth orbit (LEO) for two to five years. PLANT-B is an acronym that stands for Passive Light and Nutrient Terrarium-Biosphere, representative of the system's passive operations; the satellite is engineered to passively light and heat the 0.7 L terrarium. Inhabited by a plant and numerous microorganisms, this terrarium is unique in that it is one of the first attempts to maintain a self-sustaining, Earth-like ecosystem directly in the space environment; terrarium experiments have been conducted on the the International Space Station (ISS), but true biological payloads are rare, especially on satellites. By incorporating multiple trophic levels, the terrarium ecosystem grants us insight into the functioning of closed ecological life support systems (CELSS)—a biological space life support system that also incorporates multitrophic species assemblages to replenish life-sustaining resources for and maintain the habitability of a closed system (Grove, 2023). When space settlements become a reality, prospective inhabitants must be able to replenish their own resources to reduce dependence on resupply flights.

![An early PLANT-B terrarium prototype showing the spiral of Hygrolon the moss will grow on.](https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/img/PLANT-B_Prototype.png)

To create a self-sustaining terrarium ecosystem that can function in space without outside intervention, all ecological processes must be accounted for. The "PLANT-B Nutrient Cycle Simulation" GitHub repository was developed to simulate the terrarium ecosystem's carbon (C) and nitrogen (N) cycles. Initial simulations will provide a baseline reference point for understanding how nutrients flow throughout the terrarium ecosystem.

## Meet the Residents

The LEO environment will pose two main challenges to the terrarium's inhabitants: rapidly shifting light-dark cycles and microgravity. The orbital path dictates that the sealed ecosystem will be subject to rapidly shifting 60-30 minute light-dark cycles—similar to the daylight cycle occupants of the ISS experience. Additionally, if the ISS is used as a reference point, the terrarium will experience gravity at 89% the strength of Earth's gravity at sea level; this will not be felt by the terrarium's occupants because the orbit will cause the terrarium to be in a state of constant freefall (National Aeronautics and Space Administration, 2015).

When conducting space experiments with biological organisms, a great degree of uncertainty is anticpated due to limited data, which is why model organisms are commonly used. One such model organism is *Physcomitrium patens*. This moss was selected as the producer for the terrarium because of its remarkably resilient spores, which are capable of germinating after surviving in the vacuum of space for over nine months (Maeng et al., 2025). Regrettably, this resilience has its limits; a study found that LEO daylight cycles inhibit plant development and photosynthetic productivity, and as a C3 plant, *P. patens* may have difficulty continuously "restarting" photosynthesis (Kalbacher & Gonzalez, 2016). *P. patens* is more photosynthetically productive in stronger-than-Earth gravity, so microgravity is expected to inhibit photosyntesis (Takemura et al., 2016).

![A cluster of Physcomitrium patens. Photo by Pirex at Wikimedia Commons.](https://upload.wikimedia.org/wikipedia/commons/d/dd/Physcomitrella.jpg?_=20101210214832)

*Trichorhina tomentosa* and *Folsomia candida* were the chosen invertebrates because they are common fixtures in bioactive terrariums, serving as the clean up crew that break down waste like feces and mold. Their primary role will be to break down the decomposing leaf litter of *P. patens*. It is difficult to infer how the space environment will impact these invertebrates because no space experiments involving isopods or springtails exist. *F. candida* is eyeless, but some of its movement behaviors are light dependent (Ruiz et al., 2017). It is reasonable to infer that the altered light-dark cycles will negatively impact the invertebrates' circadian rhythms. 

![Trichorhina tomentosa specimens in a test terrarium with soil. Frame taken from a video by Patrick Grove.](https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/img/White_Dwarf_Isopods.png)

![Folsomia candida specimens.](https://dubiaroaches.com/cdn/shop/files/unnamed_22_990x.jpg?v=1752547045)

## Gathering Data for the Simulation

To simulate carbon and nitrogen cycles, soil nutrient concentrations need to be known. To identify an appropriate area to take data from, observation data of *P. patens*, *T. tomentosa*, and *F. candida* was taken from the Global Biodiversity Information Facility (GBIF) and mapped out. This [interactive map](https://github.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/blob/main/plots/Interactive_PLANT-B_Species_Distribution_Plot.html) was used to identify an appropriate area of habitat overlap around the German-Polish-Czech border.

![PLANT-B species distribution near the German-Polish-Czech border.](https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/plots/PLANT-B_Species_Border_Distribution_Plot.png)

To gather soil nutrient data for the overlap area, a request was submitted to the the European Soil Data Centre (ESDAC) for the LUCAS 2018 TOPSOIL data. When data within the set bounding box was examined, only one relevant soil sample was found. This soil sample yielded a C:N—or carbon: nitrogen—ratio of 9.86:1, indicating an environment where decomposition will occur very rapidly. Per an inquiry to the TRY Plant Trait database, *Physcomitrium* species have a nitrogen Ellenberg Indicator Value of 6 or 7 (Kattge et al., 2020)—indicating a preference for moderately fertile, nitrogen-rich soils—which corresponds to a C:N ratio of 10:1 (Sürmen et al., 2014). The recorded values were used to calculate the absorbed nutrient quantitites present in the Hygrolon.

![Carbon and nitrogen concentrations in a soil sample in the overlapping habitat area.]((https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/plots/PLANT-B_Species_Overlapping_Habitat_OC_and_N_Concentrations_Plot.png)

The StoichLife dataset was used to determine carbon and nitrogen concentrations in *T. tomentosa*, *F. candida*, and *P. patens*. As the target species were not present in the dataset, it was filtered for closely related species, and carbon and nitrogen percentages were extracted. These percentages were used to determine starting carbon and nitrogen concentrations in the starting *T. tomentosa*, *F. candida*, and *P. patens* populations.

![Carbon and nitrogen compositions of the PLANT-B species by percent dry mass.](https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/plots/PLANT-B_Species_Dry_Mass_Elemental_Composition_Plot.png)

Before conducting the final simulation, the predicted population growth of *T. tomentosa* and *F. candida* was plotted. The carrying capacities were configured to be 20 and 250 for *T. tomentosa* and *F. candida* respectively. Though conventional terrariums will have higher carrying capacities, soil invertebrate populations depend on resource availability, so carrying capacities were adjusted to ensure longevity for the nutrient cycles (McGee et al., 2020).

![The modeled population growth of the PLANT-B intertebrates.](https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/plots/PLANT-B_Invertebrate_Population_Growth_Plot.png)

## Simulation Results and Discussion

Carbon and nitrogen cycles in the *T. tomentosa*, *F. candida*, and *P. patens* populations were simulated using ordinary differential equations.

![Carbon and nitrogen pool trajectories in the PLANT-B terrarium ecosystem.](https://raw.githubusercontent.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation/main/plots/PLANT-B_Nutrient_Cycle_Plot.png)

As observed in the population growth curves, *T. tomentosa* and *F. candida* hit their carrying capacities quickly—within two months of simulation initiation. Conversely, it would take *P. patens* over three months to hit its maximum biomass. This biomass has a cap on how much carbon it can absorb, but as the carbon pool for the moss is still growing at the end of the five-year timeframe, this cap has not been reached. 

With the exception of this moss carbon pool and the *F. candida* carbon pool, all nutrient pool masses look to have leveled off by the time the simulation concludes. This corresponds with the carrying capacities being reached; though it takes several years to reach an equilibrium, the conclusion of population growth suggests a balanced end state is eventually reached. As limited carbon is present in the terrarium, the still-growing carbon pools will also level off at some point.

The achievement of an equilibrium suggests carbon and nitrogen cycles can be sustained indefinitely in the terrarium ecosystem. However, this will ultimately depend on the true population parameters of the selected species. The carrying capacities of the invertebrates and maximum biomass for the moss were configured to achieve this sustained equilibrium, but differing values may lead to the nutrient pools being depleted prematurely. Additional testing is needed to confirm if the ecosystem is truly self-sustaining. 

## What's Next for this Project?

The preliminary simulation results speaks to PLANT-B's potential to contribute to biological space life support systems, but additional testing is needed to truly confirm this. The simulation covers a limited scope: only two nutrient cycles are covered—ecological stoichiometry datasets also typically incorporate phosphorus (P) and potassium (K) cycles—and LEO conditions are not incorporated into the simulation. The literature review will be widened to find additional elemental stoichiometry data, and the simulation will be configured to account for LEO conditions. To more accurately incorporate soil microbe data into the simulation, ESDAC's “Soil biodiversity - DNA Bacteria and Fungi” dataset will be accessed and downloaded. Finally, data from physical PLANT-B experiments will be incorporated into the final simulation to accurately adjust its parameters and height its accuracy.

## Interested in Finding Out More?

The PLANT-B Nutrient Cycle Simulation repository can be accessed on GitHub [here](https://github.com/TheSpringInstitute/PLANT-B-Nutrient-Cycle-Simulation). You can read more about the PLANT-B CubeSat Terrarium Mission on [The Spring Institute's website](https://thespringinstitute.com/plant-b-cube-satellite-terrarium/).

## References

Grove, Patrick. (2023, June 30). *Comparing Life Support Solutions: PCLSS vs BLSS vs CELSS*. The Spring Institute for Forest on the Moon. https://thespringinstitute.com/comparing-life-support-solutions-pclss-vs-blss-vs-celss/

Kalbacher, K. T., & Gonzalez, E. N. M. (2016). Analysis of a Low Earth Orbit Photoperiod on the Development of Aquaponic Lettuce. *AIAA 2016-5352*. https://doi.org/10.2514/6.2016-5352

Kattge, J., Bönisch, G., Díaz, S., Lavorel, S., Prentice, I. C., Leadley, P., Tautenhahn, S.,Werner, G., et al. (2020). TRY Plant Trait Database - Enhanced Coverage and Open Access. *Global Change Biology*, *26*(1), 119-188. https://doi.org/10.1111/gcb.14904.

Maeng, C., Hiwatashi, Y., Nakamura, K., Matsuda, O., Mita, H., Tomita-Yokotani, K., Yokobori, S., Yamagishi, A., Kume, A., & Fujita, T. (2025). Extreme Environmental Tolerance and Space Survivability of the Moss, *Physcomitrium patens*. *iScience*, *28*(12), 113827. https://doi.org/10.1016/j.isci.2025.113827

McGee, K. M., Porter, T. M., Wright, M., & Hajibabaei, M. (2020). Drivers of Tropical Soil Invertebrate Community Composition and Richness Across Tropical Secondary Forests using DNA Metasystematics. *Scientific Reports*, *10*(1). https://doi.org/10.1038/s41598-020-75452-4

National Aeronautics and Space Administration. (2015, February). *Microgravity Science on the ISS: A Primer for New Researchers* [PowerPoint slides]. https://www.nasa.gov/wp-content/uploads/2015/02/501343main_microgravity_science.pdf

Ruiz, G. M., Le Galliard, J.-F., & Tully, T. (2017). Genetic Variation in Light Vision and Light-dependent Movement Behaviour in the Eyeless Collembola *Folsomia candida*. *Pedobiologia*, *61*, 33–41. https://doi.org/10.1016/j.pedobi.2016.12.001

Sürmen, B., Kutbay, H. G., Kılıç, D. D., Huseynova, R., & Kilinç, M. (2014). Ellenberg’s Indicator Values for Soil Nitrogen Concentration and pH in Selected Swamp Forests in the Central Black Sea Region of Turkey. *Turkish Journal of Botany*, *38*(5), 883–895. https://doi.org/10.3906/bot-1311-43


