# eda_and_git_colab
------------
## Project Goals and Research Questions:
The purpose of this project was to examine correlates of COVID infections, hospitalization rates, deaths, and vaccinations within the US in 2022. 

- <b>RQ1:</b> Are there any differences COVID infection and vaccination rates between lower poverty and higher poverty counties?
- <b>RQ2:</b> Which states have the highest vaccination and infection rates?
- <b>RQ3:</b> Which counties in the US had the highest/lowest infection and vaccination rates?
- <b>RQ4:</b> Does vaccination rate predict infection and hospitalization rates?
- <b>RQ5:</b> Do educational attainment differences within counties predict vaccination and infection rates?

## Data Sources and Research Methods:
The methods used in this project were purely correlational, using multiple existing databases. 

The level of analysis used in this project was a geographic-based grouped level rather than single person or individual based. 
All data points used were collapsed at the county level. 

<b>Multiple data sources were used and blended together into a data frame for this project:</b>
- Data on COVID cases, deaths, vaccinations, etc. was provided by covidactnow.org. (https://covidactnow.org/data-api)
- Data on educational attainment was provided by the US Census Bureau. (https://data.census.gov/table/ACSST1Y2022.S1501?q=educational+attainment)
- Data on poverty levels for counties in Virginia (2021) was pulled from. (https://data.ers.usda.gov/reports.aspx?ID=17826)
- State abbreviations were provided by kaggle.com. (https://www.kaggle.com/datasets/francescopettini/us-state-names-codes-and-abbreviations/)

## Data Extraction & Cleaning: (See <code>data_extraction.ipynb</code>)
Using the data sources above, the following files were generated and stored in the Outputs folder for use in analysis after cleaning and merging:
- cleaned_covid_counties.csv
- cleaned_educational_covid_merged.csv
- cleaned_va_poverty_covid_merged.csv

## Analysis of Data:
### RQ1- (See <code>analysis_covid_poverty.ipynb</code>)
In this section, determine if there are any differences in CoVID infection and vaccination rates between lower and higher poverty counties in Virginia state in the US using the 2021 poverty data available.

Note that even though the poverty data was pulled using the 2021 data for Virginia versus the COVID data from 2022, the poverty data should relatively be the same for 2022 since the change in poverty rate would not change drastically within one year
Based on the observation below, there is a significant correlation between poverty and vaccination rate (r=-0.35 p< 0.05) in the counties listed for Virginia. 

There is an overall increase in vaccination from a lower-poverty county to a higher-poverty county. 
Even though there is not a lot of variation in the vaccination completed rate which could be due to the lack of reporting, the data is still significant.

Additionally, the infection rates vs poverty rates showed a significant positive correlation (r= 0.49, p<0.05).

Poverty does have a significant relationship with the infection rate. This could be due to the lack of medical supplies, facilities (hospital beds/treatment centers), and prevention.

### RQ2- (See <code>covid_vaccination_infection_rates.ipynb</code>)
To examine the highest and lowest vaccination rates, the percentage of the population vaccinated was examined, and the highest and lowest percentages were recorded. It should be noted that some of the data appeared to have errors because 3 states showed no vaccinations at all.
Vaccination rates were highest among Connecticut, Maine, and Puerto Rico, which all had vaccination rates higher than 80%, and were lowest in Alabama, Georgia, and Wyoming, which all showed vaccinations around 50%. 

The highest and lowest case percentages were examined using the percentage of the population that had COVID in 2022. The highest and lowest percentages were recorded.

Cases were highest in Alaska, Rhode Island, and North Dakota, where cases were around 40%, and were lowest in Maryland, Oregon, and Maine, which all had percentages below 25%.

The bottom five states in terms of vaccination were all in or near the southeastern region of the US while the four of the five states with the highest vaccination rates were in the northeastern US. No similar trend was found with COVID cases. 

### RQ3- (See <code>covid_max_min_analysis.ipynb</code>)
Story County, NV has demonstrated a commendable effort in managing the COVID-19 pandemic, reporting a relatively low infection rate of 4.97%. All the lowest case counties were in western states that are less densely populated, and were generally not close to major cities (aside from Storey County, NV, which was somewhat close to Reno).

North Arctic Borough, AK has experienced a significant COVID-19 outbreak, with  infection rate of 77.06%. This county and the others with the highest cases were in somewhat surprising areas. Three of the top 5 counties were in Alaska, and the other two were in Texas. 
While the counties had a higher population compared to the lowest case counties, they were by no means highest density locations. None of them were in counties containing a large city.

Norfolk City, VA stands out as a vaccination success story, with an impressive vaccination rate of 99.86%, reflecting a high level of community immunity. 
Among the top remaining high vaccination counties, there was no emerging theme or similarity among the highest vaccinated counties. They varied in size, region, and distance from major cities.

Slope County, ND is facing vaccination challenges, as it reports a low vaccination rate of 11.33%, highlighting the need for increased vaccination efforts in this region. 
Among the lowest vaccinated counties, there’s not a lot of geographic similarity, but all of these counties are relatively rural, and not near any major cities.


### RQ4- (See <code>Hospitalization.ipynb</code> and <code>Vaccination to Hospitalization.ipynb</code>)
To test the relationship between vaccination rates and COVID outcomes, correlation and regression were used.
First, after removing a univariate outlier on vaccination rate, a linear regression was run examining the relationship between vaccination percentages and infection rates. 
The regression was significant (r=--0.33, p<0.05). 
This indicated that higher vaccination rates within a county corresponded to lower infection rates. 

Second, to examine the relationship between vaccination percentages and hospitalizations, a regression was run between the two constructs. 
The relationship was significant and positive, but small (r = 0.13, p<0.05). 
Bed usage was higher for counties with higher vaccination. 
The latter finding should be taken with a grain of salt, however. Most counties did not report data on hospitalizations, and a several counties showed bed usage numbers well above 100%. 

### RQ5- (See <code>Educational Analysis.ipynb</code>)
Research question 5 included 2 sub-components. The first question examines the relationship between educational attainment and infection rates.

To examine this, a linear regression was run examining the relationship between percentage of the county population with a Bachelor's degree and percentage of the population getting COVID in 2022.
The regression revealed a significant relationship between the two (r =-0.25, p<0.05). The regression equation for this relationship was y=0.12*x+34.97.
Counties that had higher percentage of Bachelor's degree educated people showed significantly lower COVID infection percentages. 

To further examine this research question, COVID mortality rates were also examined. Thus, this parat of the question examines the relationship between educational attainment and mortality rates. 
To examine this, a linear regression was run examining the relationship between percentage of the county population with a Bachelor's degree and percentage of the population that passed away from COVID in 2022.
The regression revealed a significant relationship between the two (r =-0.17, p<0.05). The regression equation for this relationship was y=-0.0*x+0.22.
Counties that had higher percentage of Bachelor's degree educated people showed significantly lower COVID mortality percentages. 

The second question examines the relationship between educational attainment and vaccination rates. To examine this, two additional analyses were run looking at vaccination rates and booster rates. 
To examine the former, a linear regression was run examining the relationship between percentage of the county population with a Bachelor's degree and percentage of the population that was vaccinated from COVID in 2022.
The regression revealed a significant relationship between the two (r =0.62, p<0.05). The regression equation for this relationship was y=0.67*x+39.9.
Counties that had higher percentage of Bachelor's degree educated people showed significantly higher vaccination percentages. 

Similar results for found for booster rates. A linear regression was run examining the relationship between percentage of the county population with a Bachelor's degree and percentage of the population that had recieved a booster for COVID by 2022.
The regression revealed a significant relationship between the two (r =0.64, p<0.05). The regression equation for this relationship was y=0.59*x+12.9.
Counties that had higher percentage of Bachelor's degree educated people showed significantly higher booster percentages. 

## Discussion:
In general, the extant data shows that poverty and education predict vaccination, infection, and mortality rates. More specifically, vaccination rates were higher in more educated counties with less poverty, in turn showing lower infection rates and mortality rates. 
There are multiple potential explanations to this. One explanation could've been resource differences. Counties higher in education and lower in poverty are likely more wealthy overall, meaning plausibly easier access to quality healthcare, better information flow from doctors and medical experts, and possibly more work flexibility (i.e., telework). 

Another explanation could be around knowledge and/or willingness to trust medical experts. The ultimate goal of most baccalaureate is to enhance critical thinking and analysis skills. Perhaps people in more educated counties were better equipped to sort out fact from fiction around the virus. 

However, in both cases, more data is needed to conclusively support or refute either of these explanations.

## Navigation:
- <code>CodeBase</code> folder contains all the working jupyter files
- <code>Outputs</code> folder contains all the charts and cleaned up dataset files
- <code>Resources</code> folder contains all the raw dataset files
