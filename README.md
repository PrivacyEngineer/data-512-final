# Analysis of the Seattle Fire Department 911 calls.

## Context

The Seattle Fire Department (SFD) provides emergency medical services and fire protection to the population of the city of Seattle. According to Wikipedia, https://en.wikipedia.org/wiki/Seattle_Fire_Department, SFD started out as a volunteer force that was taken over by the city in 1884. After the great Seattle Fire of 1889, a catastrophe that destroyed more than 64 acres of the city, SFD was re-established as a paid professional department. 

With 34 stations, its Head Quarters and a permanent presence at the Harborview Medical Center, the SFD provides services to more 700 thousand inhabitants, covering a surface of 142.5 square miles, and 193 miles of waterfront.
Home to Amazon and Starbucks, neighbor to Boeing, Microsoft and T-Mobile, a target for expansions by Silicon Valley companies, and home to the of the state's university system flagship, the University of Washington, keeping up with Seattle's emergency services needs is no easy feat.

For this project we plan to analyze 911 calls assigned to SFD between November 2011 and November 2018, and attempt to establish if and how demand for emergency medical services and fire incident response have changed over this period, in different areas of the city. Time permitting, we will also look for possible correlations between average temperatures and rainfall, and 911 calls to SFD in these same areas, over the last few years.

## Research questions

Our intention is to divide the city in up to six areas representative of local conditions and address the following questions:

- How has the quarterly/yearly volume of 911 calls for both; emergency medical services and fire response, changed over this seven year period?
- Are these changes statistically significant and if so, what are the trends for both types of calls?
- Are call volumes correlated to local air temperature and rainfall? If so, what are the trends?

## Process and sources of data

All data used for this project will come from the city of Seattle's Open Data Portal, which can be found here: https://data.seattle.gov/. Specific data sets are:

- Seattle real time 911 calls to SFD. Approximately 770 thousand calls received between 11/11 and 11/18: http://web5.seattle.gov/MNM/incidentresponse.aspx. This dataset is licensed under a Creative Commons CC0 1.0 Universal license: https://creativecommons.org/publicdomain/zero/1.0/legalcode. This type of license refers to copyright and other rights that are conferred to the author and owner of an original work. It is used by "Certain owners that wish to permanently relinquish those rights to a work for the purpose of contributing to a commons of creative, cultural and scientific works that the public can reliably and without fear of later claims of infringement build upon, modify, incorporate in other works, reuse and redistribute as freely as possible in any form whatsoever and for any purposes, including without limitation commercial purposes."
- Ambient air temperature measurements taken from sensor stations placed on bridges and surface streets within city limits: https://data.seattle.gov/Transportation/Road-Weather-Information-Stations/egc4-d24i, available as a public domain dataset.
- Observed monthly rain gauge accumulations: https://data.seattle.gov/City-Business/Observed-Monthly-Rain-Gauge-Accumulations-Oct-2002/rdtp-hzy3, also available as a public domain dataset.

We note that while the 911 calls and rain gauge accumulations datasets are compact enough that it's reasonable to download them in full, the air temperature measurements dataset, however, is significantly larger. Consequently we'll have to employ the Socrata API, https://dev.socrata.com/consumers/getting-started.html, to filter the data before download. The Socrata API is made available under a Creative Commons CC-BY-NC-SA 3.0 license that requires us to ".... give appropriate credit, provide a link to the license (https://creativecommons.org/licenses/by-nc-sa/3.0/deed.en_US), and indicate if changes were made." The license does not allow use of the API for commercial purposes, and requires ShareAlike. That is, "If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original."

## Unknowns and dependencies of our project

- After a visual inspection it seems that the quality and amount of data in the 911 calls and rain gauge datasets is adequate for the type of analysis we intend to perform, but we will not know for sure until we have had the opportunity to advance the project further.
- As stated earlier in this document, the amount of data in the temperature dataset is significant, to the point where it is not reasonable to download the full dataset. Thus, we will have to employ the Socrata API to filter the data. We have registered to use the API, but have so far not had a chance to use it, therefore we are not 100% sure we will be able to access a subset of it in a usable form for this project, or that the quality and completeness of the data for the period we are interested in will be satisfactory.
- Our findings may turn out to be negative. That is, we may find that there are no statistically significant changes in call volumes over the period we analyze, and that there is no significant correlation between call volume on one side, and temperature and rainfall on the other.

## Human Centered Data Science

This project is most directly related to the societal implications of data science, as it shows how data science can be used to analyze various aspects of societal needs to understand how we are currently addressing them, and also to plan for future needs. Our project will also address data provenance, preparation and reproducibility of this study, and there is a small but non-zero probability that we may discover bias in the data, and are able to associate that bias to its consequences.

## Suggestions Provided in Class

- Include population figures.
- Compare call to population density.
- Can we say something about the type of building in each zone?
- Fires due to human error or electronic failure may have nothing to do with weather/air temperature.