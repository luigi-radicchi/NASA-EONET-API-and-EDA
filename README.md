# NASA EONET Natural Events Analysis
This project analyzes global natural events collected through NASA's EONET (Earth Observatory Natural Event Tracker) API.

The objective is to build a complete data analytics workflow starting from a REST API, performing data cleaning and feature engineering in Python, and generating both temporal and geospatial insights on natural disasters and environmental events worldwide.

The dataset includes events such as:

 - Wildfires
 - Severe Storms
 - Volcanoes
 - Earthquakes
 - Sea and Lake Ice events
 - Dust and Haze events

## Data Source
Source: NASA EONET API

EONET provides real-time and historical information on natural events collected from multiple trusted observation systems and scientific sources.

Data retrieved includes:

 - Event metadata
 - Categories
 - Observation sources
 - Temporal observations
 - Geographic coordinates

Data was collected through the NASA EONET REST API using Python and the Requests library.

## Data Cleaning
The original JSON structure contained several nested fields.

The following transformations were applied:

### Categories
Category dictionaries were flattened into a single categorical field.

### Sources
Events may contain multiple observation sources.

To preserve a one-event-per-row structure, source identifiers were concatenated into a single text field.

### Temporal Observations
Some events contain multiple temporal observations.

Only the first observation was retained to avoid event duplication and maintain analytical consistency.

### Spatial Observations
Events may contain multiple geographic observations.

The first available coordinate pair was extracted and used as the event reference location.

### Geographical Features
Latitude and longitude were extracted into dedicated columns.
The state and nations of the event has been retrieved by parsing from the title of the event which included also the location.

### Date Features
Feature engineering produced:

 - Year
 - Month Number
 - Month Name
