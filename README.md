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
###### The approximate polygon of the area surrounding downtown San Diego will allow us to sort busstops that are within a "reasonable" distance from the official border of downtown San Diego. In selecting which MTS bus stops to examine in relation to the proximity of the homeless counted in the data set, I selected bus stops for 4-5 blocks further than the official perimeter of the downtown San Diego area to account for MTS bus stops that might fall outside of the offical downtown San Diego border yet still be in close proximity to the homeless in the data set.

### Data Analysis
###### A heatmap of homeless counts, as well as a time heatmap of homeless counts should provide visual insight into the research question. 

![alt text](https://github.com/joddle/SD_homeless_project/blob/master/heatmap.png "Heatmap")

###### The metric we will use to do a statistical analysis is the mean of the sum of the inverse of the haversine distance between each homeless observation and every MTS bus stop within the 4-5 blocks of the downtown San Diego perimeter. 

###### This can be written as: (1/n)∑(1/hav(p1,p2)^2) where n is the number of MTS bus stops in our analysis, and hav(p1,p2) is the haversine distance between each homeless observation and all of the MTS bus stops. The haversine distance between two latitude and longitude points is given by:

![alt text](https://github.com/joddle/SD_homeless_project/blob/master/haversine_distance.png "haversine distance")
