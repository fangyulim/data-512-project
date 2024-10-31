# data-512-project

# Goal
The goal of this project is to be able to inform policy makers, government bodies, to make an informed plan for how they could or whether they should make plans to mitigate future impacts from wildfires. <br>
For this project, we will be analyzing wildfire impacts in Wichita City, Kansas State. 

# Project Structure
project-main/ <br>
| <br>
|-- wild_fire_data/  
|   |-- USGS_Wildland_Fire_Combined_Dataset.json (This file is NOT on GitHub due to size restrictions.)
|-- intermediate_data/  
|   |-- [avg_aqi_per_year](./intermediate_data/avg_aqi_per_year.csv)  
|   |-- [wildfire](./intermediate_data/wildfire.csv)  
|-- modules/  
|   |-- [part1_AQI_index.ipynb](./modules/part1_AQI_index.ipynb)  
|   |-- [art1_common_analysis](./modules/part1_common_analysis.ipynb)
|   |-- [apikeys](./modules/apikeys.zip)
|-- graphs/  
|   |-- [acres_burned_per_year_max_650_miles](./graphs/acres_burned_per_year_max_650_miles.png)
|   |-- [acres_burned_per_year_max_650_miles_log_scale](./graphs/acres_burned_per_year_max_650_miles_log_scale.png)
|   |-- [aqi_vs_predicted_smoke](./graphs/aqi_vs_predicted_smoke.png)
|   |-- [num_fires_every_50_miles](./graphs/num_fires_every_50_miles.png)
|-- resources/  
|   |-- [epa_air_quality_history_example.ipynb](./resources/example_notebooks/epa_air_quality_history_example.ipynb)  
|   |-- [wildfire_geo_proximity_example](./resources/example_notebooks/wildfire_geo_proximity_example.ipynb)
|-- README.md  
|-- LICENSE  


# Intermediary files
  - [avg_aqi_per_year](./intermediate_data/avg_aqi_per_year.csv)
    It contains the average AQI per year. 

      **Schema**: 
        [year : integer,
         avg_aqi: float]

  - [wildfire](./intermediate_data/wildfire.csv)
    It contains details about the wildfires occuring between 1961 to 2020. I filtered for results between 1961 to 2024. However, I was unable to retrieve data for after 2020.  

      **Schema**: 
        [Year : integer,
         Acres: float,
         Distance: float,
         Fire_Type: string]


# Graphs
 - [acres_burned_per_year_max_650_miles](./graphs/acres_burned_per_year_max_650_miles.png)
   This time series graph shows the total acres burned per year for the fires occuring up to 650 miles from Wichita, Kansas.
 - [acres_burned_per_year_max_650_miles_log_scale](./graphs/acres_burned_per_year_max_650_miles_log_scale.png)
   This time series graph shows the total acres burned per year for the fires occuring up to 650 miles from Wichita, Kansas. The difference with the first one is that the y axis is computed on a log scale to examine trends. 
 - [aqi_vs_predicted_smoke](./graphs/aqi_vs_predicted_smoke.png)
   This time series graph contains the fire smoke estimates for Wichita, Kansas and the AQI estimates. 
 - [num_fires_every_50_miles](./graphs/num_fires_every_50_miles.png)
   This histogram shows the number of fires occuring every 50 miles, ranging up to 1600 miles from Wichita, Kansas. 

# Issues/ To reproduce 
 - You will need to download the GeoJSON Files.zip from [sciencebase.gov](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) and used the USGS_Wildland_Fire_Combined_Dataset.json file. You might want to create a wild_fire_data folder to save this file if you want to follow a similar file path to this project. 
 - You might want to come up with a different transformations for the variables when making smoke predictions.
 - For the wildfire data, under *wf_feature["geometry"]["rings"][0]*, some entries are a dictionary where the value is a list of lists. You might want to convert and clean these entries too. 
 - When trying to do an API call for AQI, there might be multiple FIP code for the area. 

# Installation Instructions

 - Python Version: 3.11.9
 - pyproj: 3.7.0
 - geojson: 3.1.0
 - pandas: 2.21
 - matplotlib:3.8.0
 - numpy: 1.24.3
 - scikit-learn: 1.5.2

# Citation/ License
- [Comined Wildland Fire Datasets](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)
  Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3.

- [epa_air_quality_history_example](../data-512-project/resources/example_notebooks/epa_air_quality_history_example.ipynb)
  This code example was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - August 16, 2024

- [wildfire_geo_prxoimity_example](../data-512-project/resources/example_notebooks/wildfire_geo_proximity_example.ipynb)
  This code example was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.1 - August 16, 2024

- [US EPA AQI](https://aqs.epa.gov/aqsweb/documents/data_api.html)

# Acknowledgement 
Huge thank you to my peers for the discussion around the smoke impact models and April Gao for sharing her experience. 