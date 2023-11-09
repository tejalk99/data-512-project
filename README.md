# Longview, Washington Smoke Impact Analysis

## Goal
The goal of this project is to observe the impact of wildfires  on the town of Longview, Washington. Specifically, I investigate fires that occurred within 1250 miles of Longview over the last 60 years (1963 - 2023). First, I conduct an analysis of historical wildfire data to create an annual wildfire smoke impact estimate based on parameters such as the distance of the fire from the city, the total area burned, and the number of fires that occurred. I compare my wildfire estimate to AQI estimates for the same time period, and forecast my wildfire estimate for the next 25 years (2024 - 2049).

## Data
Please see below for a list of datasets used and produced in this project. 

### Data Inputs
#### Files
- Combined wildland fire datasets for the United States and certain territories, 1800s-Present (combined wildland fire polygons) (*USGS_Wildland_Fire_Combined_Dataset.json*): This dataset was accessed at this [link](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). It contains historical wildfire data across the United States beginning from the 1800s, and contains features such as the fire name, year, and geographic coordinates.

#### API
- Air Quality System (AQS) API: Documentation for this API is available at this [link](https://aqs.epa.gov/aqsweb/documents/data_api.html): This API, produced by the U.S. Environmental Protection Agency (EPA) was used to access historical Air Quality Index (AQI) measure data from monitors in the surrounding area. I obtained these measures using a bounding box of 100 miles around Longview, Washington.

### Data Outputs
- Fires and Distances (*gj_df_dist.csv*): This dataset is an intermediary data file, and can be viewed in the `data` folder of this repository. It contains the distances of each fire in the given time period and distance from Longview that was used in my analysis. Each field is outlined below:
  - *feature* (object): The number of the fire, ranging from 0 to 73746.
  - *distance* (float64): The distance from Longview to the fire (calculated using the centroid of the fire).
- Annual AQI Parameters (*boundbox_df.csv*): This dataset is an intermediary data file, and can be viewed in the `data` folder of this repository. It contains the values of each AQI measure from monitors within 50 miles of Longview over the specified time period. Each field is outlined below:
  - parameter_code (*object*): The ID number of the parameter.
  - aqi (*object*): The AQI measure.
  - year (*int64*): The year of the measurement.

### Special Considerations
Please note that although this analysis is intended to cover the years 1963 - 2023, the wildfire data set only contains data up to the year 2020. In addition, as satellites began to map fires beginning in the early 1980s, the quality of data is much lower before this time period. As for the AQI data, the EPA states that 1980 marked the start of nationally consistent operational and quality assurance procedures for air quality monitoring. Although data from previous years is available, there is uncertainty in the results.

## Code
