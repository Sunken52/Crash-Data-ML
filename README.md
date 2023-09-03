# Crash Stats Statistics

## Environment

Use the environment.yml for a conda environment, especially to ensure the pickled model works

## Aims
Identify cause of fatalities in crashes



## Data Sources

We utilized multiple tables in our Machine Learning analysis to classify fatality rates in crash data. Below is an overview of the tables, their descriptions, and whether they were used in our analysis.

| Table              | Description                                    | Used in Analysis |
|--------------------|------------------------------------------------|------------------|
| `Accidents`        | General data on each accident                   | Yes              |
| `Accidents_event`  | Detailed sequential data of accident            | No               |
| `Person`           | General data on all persons involved in the accident | No            |
| `Vehicle`          | General data on all vehicles in the accident    | Yes              |
| `Node`             | Data on latitude and longitude of the accident  | No               |
| `Node_ID`          | Detailed data on nodes                          | Yes              |
| `Accident_location`| Address of accidents                            | No               |
| `Accident_chainage`| Location of accident with respect to roads      | No               |
| `Atmospheric_cond` | Weather/atmosphere conditions                   | Yes              |
| `Road_surface_cond`| Road surface conditions                         | Yes              |
| `SubDCA`           | Detailed accident description codes             | No               |

## Data Quality and Preprocessing

### Issues and Resolutions

1. **NODE_ID Table**: There were inconsistencies in the categorization of whether a node was in an urban or rural area. This table contained duplicate entries often with conflicting information. To resolve this, we used the ABS rural indexes as a substitute.

2. **Vehicle Table**: The dataset for vehicles was initially rich but contained a significant number of null values, particularly in the 'weight of vehicle' field. These entries were removed to maintain data quality.

By addressing these issues, we aimed to improve the reliability and integrity of our machine learning analysis on fatality classification in crash data.



## Analysis/feature engineering

We looked at all the columns and conducted a logistic regression against columns that were useful/didn't leak data

Some feature engineering was performed on location data, and time data

Where the logistic regression showed perfect collinearity, we remapped the categories.

We also peformed chi-squared tests for hypothesis and used Cramer-v scores to give us an understanding of the strength of the relationship


## Modeling

We ran a basic model, then optimised the hyperparameters to prevent overfitting.

We tried SMOTE, but that didn't work great (likely because KNN wasn't ideal for data)