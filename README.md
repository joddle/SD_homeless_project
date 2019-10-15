## Downtown San Diego Homelessness Project

### The Research Question
###### The primary research question we want to answer is whether homeless people are more likely to congregate near bus stops, and this research can be extended to other types of public landmarks such as police stations and homeless shelters.

###### In order to answer this question, I used the homelessness data set created and released by the San Diego Regional Data Library. The raw data was downloaded from https://www.sandiegodata.org/2019/09/downtown-homeless-data-released/ and has been posted under the SD_homeless_project/sandiegodata.org-dowtown_homeless-8/ directory.

### The Data Sets
###### The homeless dataset has approximately 41,900 observations containing features: time stamps, temperature, and geographic location (geoid, latitude, longitude, neighborhood) of homeless people for 62 months between 2012 and 2018. 

###### The dictionary for the homeless dataset is provided below.

| Column Name   | Data Type     | Description |
|:------------- |:------------- |:----- |
| neighborhood  | string        | Neighborhood, from the label on the source map |
| date          | date          | Date of the observation. Many dates have no day of month; for these dates, the day of month is set to 1 |
| type          | string        | Type of sleeper: individual, vehicle or structure  |
| temp          | float         | Temperature, if it was written on the source map   |
| rain          | string        | Rain or clear, if it was written on the source map |
| geoid         | string        | Census geoid for the 2010 Census block the observation is in, in ACS format |
| x             | number        | X geographic position, in California State Plane 6, EPSG:2230|
| y             | number        | Y geographic position, in California State Plane 6, EPSG:2230|
| geometry      | string        | Geographic position of observation, in Lat/Lon, EPSG:4326 |


###### The MTS dataset collected from the San Diego MTS webpage contains the geographic location of all MTS bus stops in San Diego County.

###### Both datasets were imported as geopandas data types in order to better use the geographical information, make diagrams, and perform statistical analysis.

### Data Preprocessing 
###### The approximate polygon of the area surrounding downtown San Diego will allow us to sort busstops that are within a "reasonable" proximity to downtown San Diego. I selected MTS bus stops that were 4-5 blocks further than the official perimeter of the downtown San Diego area to account for MTS bus stops that the homeless might congregate near that are close to downtown San Diego but technically not within the perimeter. 

### Data Analysis
###### A heatmap of homeless counts, as well as a time heatmap of homeless counts should provide visual insight into the research question. 

![alt text](https://github.com/joddle/SD_homeless_project/blob/master/heatmap_zoom.png "Heatmap")

###### In order to determine if the location of homeless people are random relative to the location of the mts bus stops, I simulated a fixed number of data points around each mts bus stop, taking the assumption that the majority of homeless people (95% or 2 standard deviations) would be found a 5 minute walk = 400 meters from each stop).

###### The heatmap of the simulated data set shows a strong relationship to the mts bus stops. 
![alt text](https://github.com/joddle/SD_homeless_project/blob/master/heatmap_simulation_diag.png "Simulated Heatmap"])
<!-- .element width = "500px" -->

###### A statistical signifiance test was carried out between the two data sets (simulated versus observed) by comparing the distrution of ANNs (average nearest neighbors) from each point to the MTS stops. The ANN value is calculated by summing up the average distance between each point and all of the MTS stops, summing these average distances over all points in the data set, and then dividing by the number of data points. Lower ANN values indicate more clustering around MTS stops, and higher ANN values indicate less clustering around MTS stops.

###### Running N = 100 simulations and calculating the ANN for each simulation, allows us to plot a histogram of the simulated ANN values. We then compare single ANN value from the observed data set to the distribution of ANN values for the N = 100 simulations, and the p-value is the proportion of ANN values from the simulations that lie above the single ANN value for the observed data set. 
