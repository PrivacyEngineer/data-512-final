# Analysis of the Seattle Fire Department 911 calls.

## Context

The Seattle Fire Department (SFD) provides emergency medical services and fire protection to the population of the city of Seattle. According to Wikipedia, https://en.wikipedia.org/wiki/Seattle_Fire_Department, SFD started out as a volunteer force that was taken over by the city in 1884. After the great Seattle Fire of 1889, a catastrophe that destroyed more than 64 acres of the city, SFD was re-established as a paid professional department. 

With 34 stations, its Head Quarters and a permanent presence at the Harborview Medical Center, the SFD provides services to more 700 thousand inhabitants, covering a surface of 142.5 square miles, and 193 miles of waterfront.
Home to Amazon and Starbucks, neighbor to Boeing, Microsoft and T-Mobile, a target for expansions by Silicon Valley companies, and home to the of the state's university system flagship, the University of Washington, keeping up with Seattle's emergency services needs is no easy feat.

For this project we plan to analyze 911 calls assigned to SFD between November 2011 and November 2018, and attempt to establish if and how demand for emergency medical services and fire incident response have changed over this period, in different areas of the city. Time permitting, we will also look for possible correlations between average temperatures and rainfall, and 911 calls to SFD in these same areas, over the last few years.

## Research questions

The goal for the project was to answer the research questions and understand the general dynamics of the different types of 911 calls the Seattle Fire Department received over this period. We ended addressing the research questions at the city level, rather than the zone level.

- How has the yearly volume of 911 calls for both; emergency medical services and fire response, changed over this seven year period?
- Are these changes statistically significant and if so, what are the trends for both types of calls?
- Are call volumes correlated to local air temperature and rainfall? If so, what are the trends?

Results are discussed in detail in the Jupyter notebook. As a summary of those results, however, we present the following conclusions:

- With respect to the first two research questions above:
    - There is significant statistical evidence that supports an increase in yearly volume call for non-fire related calls.
    - There is no significant statistical evidence to support an increase in yearly call volume for fire-related 911 calls.
- With respect to the third question:
    - There is a positive interaction between fire-related 911 SFD calls and average daily air temperature, albeit with a lower correlation than the boxplots seem to indicate.
    - There is a negative interaction between fire-related 911 SFD calls and average daily rainfall, but the correlation is much lower than the boxplots seem to indicate.
    - There is practically no correlation between non-fire related 911 SFD calls and either average daily air temperature or rainfall.
    - Fitting multiple linear regression models shows that average daily air temperature and rainfall, combined or independently, do not provide enough of an explanation for fire-related 911 SFD call volumes. The best model is able to explain less than 18% of the variability in call volumes, so clearly other variables are at work here.
    - Fitting multiple linear regression models shows that average daily air temperature and rainfall, combined or independently, do not provide help in explaining non-fire 911 SFD call volumes. The best model is able to explain less than 1% of the variability in call volumes.

## Data acquisition

All data used for this project will come from the city of Seattle's Open Data Portal, which can be found here: https://data.seattle.gov/. Specific data sets are:

- Seattle real time 911 calls to Seattle Fire Department. Approximately 770 thousand calls received between June 29th, 2010 and December 8th, 2018: http://web5.seattle.gov/MNM/incidentresponse.aspx. This dataset is licensed under a Creative Commons CC0 1.0 Universal license: https://creativecommons.org/publicdomain/zero/1.0/legalcode. This type of license refers to copyright and other rights that are conferred to the author and owner of an original work. It is used by "Certain owners that wish to permanently relinquish those rights to a work for the purpose of contributing to a commons of creative, cultural and scientific works that the public can reliably and without fear of later claims of infringement build upon, modify, incorporate in other works, reuse and redistribute as freely as possible in any form whatsoever and for any purposes, including without limitation commercial purposes."
- Ambient air temperature measurements taken at five minute intervals from 10 sensor stations placed on bridges and surface streets within city limits. This dataset is public domain, and covers the period of time from March 3rd, 2014 until April 16th, 2018: https://data.seattle.gov/Transportation/Road-Weather-Information-Stations/egc4-d24i.
- Rainfall measurements taken at five minute intervals, by one of thirteen stations that are spread around the city. The dataset is also public domain and large, at more than 1.5 GB, and covers the period from October 2003 until May 1st, 2017  https://data.seattle.gov/City-Business/Observed-Rain-Gauge-Readings-5-Min-Intervals-Oct-2/cg4m-emwz.

It is important to point out that the volume of all three datasets employed in this study exceeds Github recommendations for maximum file size (more than a GB for two of the datasets). Thus, the raw data uploaded to the Github page represents only a sample of that available (checked with Jonathan for this). Full datasets can be obtained from the sources described in this README, and in the project's Jupyter notebook. Raw data sample datasets can be found in:

- SFD 911 calls data: ../raw_data/SFD/Seattle_Fire_911.csv
- Weather measurements: ../raw_data/Weather/Road_Weather_Information_Stations.csv
- Rainfall measurements: ../raw_data/Rain/Observed_Rain_Gauge_Readings_-_5_Min_Intervals_-_Oct_2002_to_May_2017.csv

## Data processing

All code employed for this analysis was written using Python 3.5.6 and can be found in the Jupyter notebook: ../src/Data-512-Final-SFD_Calls.ipynb

Documentation for Python can be found here: https://docs.python.org/3.5/  

Documentation for Jupyter Notebook can be found here: http://jupyter-notebook.readthedocs.io/en/latest/  

The following Python packages were used and their documentation can be found at the accompanying links:

- pandas: https://pandas.pydata.org/
- numpy: https://www.numpy.org/
- matplotlib: https://matplotlib.org/ 
- statsmodels: https://www.statsmodels.org/stable/index.html 
- scipy.stats: https://docs.scipy.org/doc/scipy/reference/stats.html
- mpl_toolkits.mplot3d: https://matplotlib.org/mpl_toolkits/mplot3d/index.html 


### Processing steps and how they address the research questions

- Data schematization and cleansing for the SFD 911 Calls dataset. This included elimnation of incomplete data and data that would not be used, and reorganizing and casting as numeric datatypes in order to streamline processing and reduce file storage size. The clean dataset was stored in: ../data_clean/SFD/Calls_Incident.csv. In addition to this, a catalog of SFD 911 incident types was created and stored in ../data_clean/SFD/Incident_types.csv
- Data schematization and cleansing for the weather dataset. This included elimnation of incomplete data and data that would not be used, and reorganizing and casting as numeric datatypes in order to streamline processing and reduce file storage size. The clean dataset was stored in: ../data_clean/Weather/Daily_Temp_MeasuresZone.csv 
- Data schematization and cleansing for the rainfall dataset. This included elimnation of incomplete data and data that would not be used, and reorganizing and casting as numeric datatypes in order to streamline processing and reduce file storage size. The clean dataset was stored in: ../data_clean/Rain/RainDay.csv
- Addressing the first two reseach questions: This was done by creating a number of barcharts and using Analysis of Variance methods (ANOVA) to establish wether either type of 911 call, fire-related and not-fire related, was increasing in volume over time.
- Simple analyis of the geographic distribution within the city of 911 SFD calls, and how this volume is distributed between the north, south and central portions of the city.
- Addressing the third research question was done through a combination of analysis of the three dataset using box plots as visualization tools, analysis of the correlation between the three datasets, and use of linear regression methods to quantify how much of the variability in call number can be explained using temperature and rainfall data.

## Unknowns and dependencies of our project

- After a visual inspection it seems that the quality and amount of data in the 911 calls and rain gauge datasets is adequate for the type of analysis we intend to perform, but we will not know for sure until we have had the opportunity to advance the project further.
- As stated earlier in this document, the amount of data in the temperature dataset is significant, to the point where it is not reasonable to download the full dataset. Thus, we will have to employ the Socrata API to filter the data. We have registered to use the API, but have so far not had a chance to use it, therefore we are not 100% sure we will be able to access a subset of it in a usable form for this project, or that the quality and completeness of the data for the period we are interested in will be satisfactory.
- Our findings may turn out to be negative. That is, we may find that there are no statistically significant changes in call volumes over the period we analyze, and that there is no significant correlation between call volume on one side, and temperature and rainfall on the other.

With respect to the first risk listed above, the quantity and quality of the 911 calls and weather data were satisfactory. For the rainfall data we had to abandon the monthly averages dataset and replace it with a much larger dataset that containe rainfall measurements at five minute intervals, from thirteen different measuring stations.
With respect to the second risk, we were able to download the full weather data set after a couple of tries, and did not need to use the Socrata API.
Findings are discussed in the Jupyter notebook.

## Human Centered Data Science

This project is most directly related to the societal implications of data science, as it shows how data science can be used to analyze various aspects of societal needs to understand how we are currently addressing them, and also to plan for future needs. Our project will also address data provenance, preparation and reproducibility of this study, and there is a small but non-zero probability that we may discover bias in the data, and are able to associate that bias to its consequences.

## Suggestions Provided in Class
As part of a class activity one of my peers, Murtaza Jafferji, suggested enhancing the project by considering additional variables, and the exclusion of fire incidents that are unlikely to be correlated with changes in ambient variables:
- Include population figures.
- Compare call to population density.
- Can we say something about the type of building in each zone?
- Fires due to human error or electronic failure may have nothing to do with weather/air temperature.
The only change we were able to implement was the last one, as we did not have enough time to research and integrate datasets on population and building type by city zone.

## A note on reproducibility and replicability of this study.
Despite the fact that we only uploaded samples of the raw datasets used for this project, the Jupyter workbook manages to yield results on the contents of the full raw datasets because we generated much smaller "clean" datasets encoded to minimize file size. These datasets are stored in the clean data directory in the Github repository (../data_clean/).

You should be able to reproduce the study by downloading the raw datasets from the source, making sure that the contents of those files matches the dates discussed for each dataset in the corresponding "Schematizing and cleansing" sections of the workbook.

For replication, please be aware that the City of Seattle stopped updating the rainfall measurement dataset on May 1st of 2017. Unless the City produces new data, replication of this study using the code below will yield updated results and visualizations for all but the rainfall visualizations, and the linear regression portion of the results.
The code in the workbook should run without any glitches and reproduce the results currently stored in the workbook.

## License

This assignment's code is released under a MIT license.