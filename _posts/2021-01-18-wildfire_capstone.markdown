---
layout: post
title:      "Wildfire Capstone"
date:       2021-01-18 19:49:26 +0000
permalink:  wildfire_capstone
---


Well, the end has finally come. I’ve finished all my lessons, all my module projects, and here I am finishing up my capstone. My current job in the environmental sector influenced my decision to choose wildfire data for my capstone project.

The data comes from [Monitoring Trends in Burn Severity (MTBS)](https://www.mtbs.gov/direct-download) which is a “multiagency program designed to consistently map the burn severity and perimeters of fires across all lands of the United States from 1984 and beyond.” This includes all fires above 500 acres in the Eastern U.S. and fires above 1,000 acres in the Western U.S. In addition to the MTBS fire dataset, I also pulled in daily climate data from National Oceanic and Atmospheric Administration's (NOAA) [Global Historical Climatology Network](https://www.ncei.noaa.gov/metadata/geoportal/rest/metadata/item/gov.noaa.ncdc:C00861/html) as well as ecoregion information from the [Environmental Protection Agency (EPA)](https://www.epa.gov/eco-research/ecoregions-north-america).

My intended plan for this project was then to use climate data (averaged by ecoregion) and geographical information (ecoregion and state) to generate a linear regression model that would predict the size of fire. I’ve realized, after much EDA and many model iterations later, that there are many more variables out there that determine that have an effect on the final burn area of a fire than I initially thought.

I averaged climate data across all weather monitoring stations in a given ecoregion (Levels 1 through 3) and then using the date of a ignition for a particular fire in that particular ecoregion, I generated average (in the case of temperatures) or total (in the case of precipitation) weather data for the 30, 90, 180, and 365 days leading up to the ignition date of the fire. This gave insight into variables like how much rain the region had received in the timeframes leading up to the fire, or how hot (or cold) it had been before the fire started. 

Unfortunately, these models didn’t turn out so well. Almost all didn’t have an R-squared value above 0.1, and those that did, were trained on either older portions of the whole dataset or on fires with burn areas that were considered outliers. Considering this, I had to give up on generating a model that would more accurately predict fire size.

After further investigative research, there are a handful of other factors at play that I not only didn’t consider, but didn’t have the data for either. These factors include topography, fire-weather conditions (not conditions prior to the ignition, but the weather conditions during the fire), human-response to fire, and fuel-type. The only one of these factors I may have been able to add to my model dataset was the fire-weather conditions, but the MTBS dataset didn’t include a fire containment date, so I couldn’t accurately grab fire-weather conditions for each fire.

Though the models generated in the capstone project were less than stellar, I did come away with a few insights from the data as well as a valuable lesson to take with me to future endeavors. First, the insights.

After some statistical testing, I found that wildfires are getting bigger, some states and ecoregions experience larger wildfires than others, and wildfires are getting bigger in certain areas of the U.S.

1) When looking at the top ten states with the most wildfires, Idaho, Oregon, and Nevada seem to be the three states with the largest average wildfires (**between 12,000 and 14,000 acres**) and Florida has the smallest average wildfires (**just over 2,000 acres**).

<a href="https://imgur.com/Q7vkwA2"><img src="https://imgur.com/Q7vkwA2.png" title="source: imgur.com" width="600" height="325" /></a>

2) For the top ten Level 3 Ecoregions with the most wildfires, the Northern Basin and Range and the Idaho Batholith experience the largest average wildfire, at around **15,000 acres**, while the Central Appalachians and the Southern Coastal Plain experience the smallest average wildfire, at around **2,500 acres.** The other 6 ecoregions fall somewhere in the middle.

<a href="https://imgur.com/JhfL59b"><img src="https://imgur.com/JhfL59b.png" title="source: imgur.com" width="707" height="325" /></a>

3) When comparing the average wildfire burn area in 1986-1988 to the average wildfire burn area in 2016-2018, I found that on average, wildfires are **6,000 acres bigger**.

<a href="https://imgur.com/PXmFIYE"><img src="https://imgur.com/PXmFIYE.png" title="source: imgur.com" width="800" height="500" /></a>

4) The following states all show a statistically significant increase in wildfire size compared to historical wildfire data: Nevada, California, Oregon, Colorado, Utah, New Mexico, Arizona, and Florida. The largest increase in average wildfire size was in Nevada, with an average increase of **14,382 acres**. Both West Virginia and Minnesota have experienced a negative trend in wildfire size.

<a href="https://imgur.com/DgkNhNy"><img src="https://imgur.com/DgkNhNy.png" title="source: imgur.com" width="800" height="500" /></a>

5) The following regions all experienced a statistically significant increase in wildfire size compared to historical wildfire data: Mediterranean California, Cold Deserts, Western Cordillera, Everglades, Upper Gila Mountains, and the Western Sierra Madres Piedmont. The largest increase in average wildfire size was in the Mediterranean California region, with an average increase of **11,075 acres**. The Mixed Wood Shield region experienced a negative trend in wildfire size.

<a href="https://imgur.com/CWNOdL0"><img src="https://imgur.com/CWNOdL0.png" title="source: imgur.com" width="800" height="500" /></a>

Even though my predictive models didn’t turn out as well as I’d hoped, I was still able to come away from this dataset with some valuable insights. With the effects of climate change starting to be felt by more and more of the population, it’s important to determine which areas in the country are experiencing more frequent and larger wildfires than they were in the past. By knowing which regions are at higher risk of wildfires, governments can better allocate funds to deal with wildfires in those regions and individuals living in high risk states and regions can decide for themselves if it would be better to move to other parts of the country with less risk of wildfire.

