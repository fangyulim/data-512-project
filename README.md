# data-512-project

# Project Overview
The goal of this project is to explore the impact of wildfires on Wichita, Kansas. This project begins with an analysis of the wildfire smoke produced by fires in the region and its potential health impacts on local citizens. By analyzing these effects, the objective is to inform policymakers and government bodies about the need to consider or implement strategies to mitigate future impacts from wildfires, particularly on public health.
            
The primary focus of the analysis is on the health consequences of wildfire smoke exposure, particularly on respiratory health and lung cancer. Specifically, this project investigates two key health outcomes:       
1. Asthma-related hospitalization rates at the county level.
2. Cancer rates in the respiratory system, with an emphasis on lung and bronchial cancers.
                     
Key findings:
1. Asthma-related Hospitalization: Between 2008 and 2018, asthma hospitalization rates increased and were moderately correlated with wildfire smoke. This suggests that wildfire smoke exacerbates respiratory conditions like asthma, leading to more hospitalizations during high-smoke events. The intensity of the impact however was not investigated.
2. Cancer Rates: Cancer rates in Kansas did not show a consistent upward trend. While there were fluctuations, the overall cancer trend was relatively stable. However, a surprising negative correlation was found between Larynx cancer and wildfire smoke. This was unexpected, but one possible explanation is that preventative actions due to increased public awareness could lower cancer risks. Alternatively, there are other confounding factors such as smoking behavior that might influence the results. 
            
You can find more information about my findings in the [final_report](reports/final_report.docx).

# Project Structure*
*The USGS Wildland dataset can be downloaded [here](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). The files downloaded were the GepJSON Files.zip*       

project-main/ <br>
| <br>
|--data            
|-- |-- wild_fire_data/            
|   |-- |-- USGS_Wildland_Fire_Combined_Dataset.json (This file is NOT on GitHub due to size restrictions.)           
|-- |-- [cdc_cancer_statistics_txt](./data/cdc_cancer_statistics.txt)          
|-- |-- [death-injury-data-sets-2022.xlsx](./data/death-injury-data-sets-2022.xlsx)           
|-- |-- [epht_asthma.csv](./data//epht_asthma.csv)           
|-- |-- [state_size_data.xlsx](./data/state_size_data.xlsx)            
|-- example_notebooks       
|   |-- [epa_air_quality_history_example.ipynb](./resources/example_notebooks/epa_air_quality_history_example.ipynb)        
|   |-- [wildfire_geo_proximity_example](./resources/example_notebooks/wildfire_geo_proximity_example.ipynb)                
|-- intermediate_data/          
|   |-- [avg_aqi_per_year](./intermediate_data/avg_aqi_per_year.csv)        
|   |-- [wildfire](./intermediate_data/wildfire.csv)        
|-- modules/        
|   |-- [part1_AQI_index.ipynb](./modules/part1_AQI_index.ipynb)        
|   |-- [part1_common_analysis](./modules/part1_common_analysis.ipynb)               
|   |-- apikeys/        
|   |-- |-- [KeyManager_BriefUserGuide.pdf](./modules/apikeys/KeyManager_BriefUserGuide.pdf)      
|   |-- |-- [KeyManager.py](./modules//apikeys//KeyManager.py)      
|-- graphs/       
|   |-- [acres_burned_per_year_max_650_miles](./graphs/acres_burned_per_year_max_650_miles.png)      
|   |-- [acres_burned_per_year_max_650_miles_log_scale](./graphs/acres_burned_per_year_max_650_miles_log_scale.png)    
|   |-- [aqi_vs_predicted_smoke](./graphs/aqi_vs_predicted_smoke.png)       
|   |-- [num_fires_every_50_miles](./graphs/num_fires_every_50_miles.png)  
|-- reports/         
|   |-- [final_report.docx](./reports/final_report.docx)       
|   |-- [final_report.zip](./reports/final_report.zip)     
|-- README.md       
|-- LICENSE         

# Reports 
- [final_report.docx](./reports/final_report.docx)
Word format for the final report.
- [final_report.zip](./reports/final_report.zip)
Zipped pdf format of final report due to size constraint.

# Intermediary files
  - [avg_aqi_per_year](./intermediate_data/avg_aqi_per_year.csv)
    It contains the average AQI per year. 

      **Schema**: 
        [year : integer,
         avg_aqi: float]

  - [wildfire](./intermediate_data/wildfire.csv)
    It contains details about the wildfires occurring between 1961 to 2020. I filtered for results between 1961 to 2024. However, I was unable to retrieve data for after 2020.  

      **Schema**: 
        [Year : integer,
         Acres: float,
         Distance: float,
         Fire_Type: string]


# Graphs
 - [acres_burned_per_year_max_650_miles](./graphs/acres_burned_per_year_max_650_miles.png)
   This time series graph shows the total acres burned per year for the fires occurring up to 650 miles from Wichita, Kansas.
 - [acres_burned_per_year_max_650_miles_log_scale](./graphs/acres_burned_per_year_max_650_miles_log_scale.png)
   This time series graph shows the total acres burned per year for the fires occurring up to 650 miles from Wichita, Kansas. The difference with the first one is that the y axis is computed on a log scale to examine trends. 
 - [aqi_vs_predicted_smoke](./graphs/aqi_vs_predicted_smoke.png)
   This time series graph contains the fire smoke estimates for Wichita, Kansas, and the AQI estimates. 
 - [num_fires_every_50_miles](./graphs/num_fires_every_50_miles.png)
   This histogram shows the number of fires occurring every 50 miles, ranging up to 1600 miles from Wichita, Kansas. 


# Data Sets
- [Combined Wildland Fire Datasets ](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)    
  - This cleaned wildfire dataset was generated by the US Geological Survey. This project uses the GeoJSON data format stored under GeoJSON Files.zip. It contains a raw merged datasets containing duplicated, and a combined dataset that is free of duplicates. This project uses the combined data which contains information on fires (wildfires and prescribed) from 1961 to 2020. For this project we filter for data that is between 1961 and 2024, and only preserve 4 attributes (Fire_Year, Listed_Fire_Names, GIS_Acres, Assigned_Fire_Type) and save it to a [csv file](./intermediate_data/wildfire.csv)
  - Description: 
    The inital datset is a JSON dictionary containing the following fields:     
    ['displayFieldName', 'fieldAliases', 'geometryType', 'spatialReference', 'fields', 'features']    
    We are mainly interested in the 'features' key which is another dictionary.

- [aqi_data](https://aqs.epa.gov/data/api)
  - The historical air quality index (AQI) data was retrieved using the US Environmental Protection Agency (EPA) Air Quality Service (AQS) API. Their [documentation](https://aqs.epa.gov/aqsweb/documents/data_api.html) provides definitions of different call parameters and examples of calls that can be made. The terms of use can be found under the **Request Limits and Terms of Service** in the documentation.     
  Our attempt at using this API is in the [part_1_AQI_index.ipynb](./modules/part1_AQI_index.ipynb) notebook.     

- [cdc_cancer_statistics](https://wonder.cdc.gov/cancer-v2021.HTML)
  - This dataset contains detailed cancer statistics from the CDC and covers cancer incidence rates for various cancer sites across the United States and Puerto Rico (The dataset available in this project has been filtered for Kansas only.). It provides data on cancer diagnoses over time, along with demographic breakdowns by state and year. 

  - Description:            
    Time range: 1999 - 2021 (yearly data)        
    It contains the following fields:         
    "Notes": String. Additional information related to the data.              
    "Cancer Sites": String. Different types of cancers.      
    "Cancer Site Code": Int. A unique identifier code for each cancer site.        
    "States": String. The name of the state in data was collected.       
    "State Code": Int. A code assigned to each state.          
    "Year": Int. The year the data was collected.            
    "Year Code": Int. A code given to the year the data was collected.                
    "Count": Int. The number of reported cancer cases for each site in that year and state.               
    "Population": Float. The population of the state for the year.            
    "Age-Adjusted Rate": Float. The age-adjusted cancer rate.           
    "Crude Rate": Float. The unadjusted rate of cancer cases per 100,000 individuals in the population

  - Terms of Use: Publicly accessible, usage should comply with CDC WONDER’s guidelines. (Data was provided for the purpose of statistical reporting and analysis only, users should not attempt to identify an individual.)
  
- [asthma_data](https://maps.kdhe.state.ks.us/ksepht/?ContentAreaID=3&GeoLayer=2&IndicatorID=90&MeasureID=437&StratFieldName=None&StratLocalId=None&Year=2011&page=Home)
  - This dataset contains annual asthma statistics for Kansas, provided by the KDHE (Kansas Department of Health and Environment). It county level information on asthma hospitalization rates stratified by year.     

  - Description:      
    Time Range: 2008 - 2018 (yearly data)     
    It contains the following fields:        
    - "County": String. The name of the county in Kansas where the data was collected.
    - "Year": Integer. The year the data was collected.
    - "Hospitalization Rate": Float. The rate of asthma-related hospitalizations per 100,000 people in the county.
    - "Population": Integer. The population of the county in the given year.
    - "Age Group": String. The age group for which the data is reported (e.g., "0-4", "5-14", "15-24").
    - "Gender": String. The gender of the population group reported (e.g., "Male", "Female").
    - "Race/Ethnicity": String. The race/ethnicity category of the population group (e.g., "White", "African American").
    - "Measure": String. The specific asthma measure being reported (e.g., "Hospitalization Rate").
    - "Indicator": String. The public health indicator being measured (e.g., "Asthma Hospitalization").

  - Citations & Terms of Use
  Kansas Department of Health and Environment. Kansas Environmental Public Health Tracking Network. (n.d.) Web. Accessed: [11/3/2024] https://keap.kdhe.ks.gov/ephtm/.
  Terms of Use: The data should only be used for statistical reporting and analysis, findings should not imply Kansas Environmental Public Tracking Program’s endorsement.

- [Fire death and injury rate](https://www.usfa.fema.gov/statistics/data-sets/)
  - This dataset contains 9 worksheets presenting statistics for U.S. states and various population groups on fire death/injury rates and relative risk of dying in a fire. 
  - Description:     
    Time Range: 2022      
    Worksheet: State Deaths, Rate, Risk 2022         
    It contains the following fields:
    - State: String. The name of the state.   
    - Fire Deaths (2022). Int. The number of deaths caused by fire in 2022.   
    - Fire Death Rate Per Million Population (2022): Float. The fire death rate per million population.   
    - Relative Risk of Fire Death (2022): Float. The relative risk of fire death. 
    * Data cleaning necessary for this document is discussed in the [part2_extension_plan.ipynb](./modules/part2_extension_plan.ipynb) *
  
  - Citations & Terms of Use
  Citations: U.S. Fire Administration (USFA), FEMA. "Fire Death and Injury Rates". (n.d.) Web. Accessed: [Date of Access].          
  Terms of Use: Data should only be used for statistical reporting and analysis purposes. Users should not imply that the U.S. Fire Administration or FEMA endorses any findings based on the dataset. Proper attribution is required when using the data in reports or research.

- [state_size_data](https://en.wikipedia.org/wiki/List_of_U.S._states_and_territories_by_area)
  - I scrapped the table from the Wikipedia page containing the list of U.S. states and territories by area. 
  - Description: This dataset lists the area of U.S. states and territories broken down into land area and water area. 
    It contains the following fields:
    - State / territory State / territory: String. The name of the region. 
    - Total area sq mi:. Int. The rounded total area of the region in square miles. 
    - Total area km2: Int. The rounded up total area of the region in square kilometers.
    - Land area sq mi:Int. The rounded up total land area of the region in square miles.
    - Land area km2 :Int. The rounded up total land area of the region in square kilometers.
    - Water area sq mi: Int. The rounded up total water area of the region in square miles.
    - Water area km2: Int. The rounded up total water area of the region in square kilometers.
    - Water area %: string The percentage of water area of the region.
  - Citations & Terms of Use:
  Citations: Wikipedia contributors. "List of U.S. states and territories by area". (n.d.) Web.    
  Creative Commons Attribution-ShareAlike 3.0 (CC-BY-SA 3.0)      
  GNU Free Documentation License (GFDL)         
  Terms of Use: By utilizing this data, you agree to comply with the attribution requirements specified by the CC-BY-SA license. Any adaptations or modifications of the dataset must be shared under a similar license. Care should be taken to respect user privacy and adhere to applicable data protection regulations. 


# Citation/ License
- [Comined Wildland Fire Datasets](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81)
  Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3.

- [epa_air_quality_history_example](../data-512-project/resources/example_notebooks/epa_air_quality_history_example.ipynb)
  This code example was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - August 16, 2024

- [wildfire_geo_proximity_example](../data-512-project/resources/example_notebooks/wildfire_geo_proximity_example.ipynb)
  This code example was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.1 - August 16, 2024

- [US EPA AQI](https://aqs.epa.gov/aqsweb/documents/data_api.html)

# Code
- [apikeys](./modules/apikeys/KeyManager.py): This python file contains the module needed to create and store credentials that were used to make the API calls. There is a pdf in the apikeys folder for more information. The code was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. Copyright by Author. All rights reserved. Not for reuse without express permissions.

- [part1_AQI_index.ipynb](./modules/part1_AQI_index.ipynb): This jupyter notebook provides details on how to make the API calls to retrieve the AQI data. Please note the citation and license mentioned in the notebook.   

- [part1_common_analysis.ipynb](./modules/part1_common_analysis.ipynb): This jupyter notebook provides details on the data exploration and analysis of the wildfire dataset.Please note the citation and license mentioned in the notebook.   

- [part2_extension_plan.ipynb](./modules/part2_extension_plan.ipynb): This jupyter notebook provides details of the data exploration, analysis, and some forecasting for our health concerns. We also reevaluate the models used to predict smoke from part 1. 

# Issues/ To reproduce 
 - You will need to download the GeoJSON Files.zip from [sciencebase.gov](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) and used the USGS_Wildland_Fire_Combined_Dataset.json file. You might want to create a wild_fire_data folder to save this file if you want to follow a similar file path to this project. 
 - You might want to come up with different transformations for the variables when making smoke predictions.
 - For the wildfire data, under *wf_feature["geometry"]["rings"][0]*, some entries are a dictionary where the value is a list of lists. You might want to convert and clean these entries too. 
 - When trying to do an API call for AQI, there might be multiple FIP code for the area. 
 - Please follow the instructions to set up the API key before making an API call to retrieve AQI data. Instructions can be found [here](./example_notebooks/epa_air_quality_history_example.ipynb).


# Installation Instructions
You will need to install these libraries to run the notebooks. You can follow the instructions in [part2_extension_plan.ipynb](./modules/part2_extension_plan.ipynb).     
(using %pip install library)           

- Python version: 3.13.0 
- pyproj version: 3.7.0
- geojson version: 3.1.0
- pandas version: 2.2.3
- matplotlib version: 3.9.3
- numpy version: 2.1.3
- scikit-learn version: 1.5.2
- requests version: 2.32.3
- seaborn version: 0.13.2
- scipy version: 1.14.1
- statsmodels version: 0.14.4
- prophet version: 1.1.6

# Acknowledgement 
Huge thank you to my peers for the discussion around the smoke impact models and April Gao for sharing her experience. 
