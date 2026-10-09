### Experimental Grid Flexibility Analysis

## Overview

NDMS is an early-stage research project exploring how statistical modelling, forecasting and data analysis can support flexibility management in electricity distribution networks.

The main objective is to investigate whether sufficient flexibility is likely to be available at a specific time and location to relieve a predicted local grid constraint.

The long-term vision is to develop a modular platform for distribution system operators (DSOs), combining data intelligence, forecasting and decision support.

## Prototype 0 – Electricity Consumption Analysis

The first prototype focuses on analysing historical electricity consumption data to establish a foundation for load forecasting and flexibility assessment.

### Data Source

Electricity consumption data is obtained from [Elhub](https://data.elhub.no/).

**Dataset:** Hourly electricity consumption per customer group and metering grid area.

[Download dataset (CSV)](https://data.elhub.no/download/consumption_per_group_mga_hour/consumption_per_group_mga_hour-all-no-0000-00-00.csv)

### Data Processing

The initial analysis consists of:

1. Loading historical hourly electricity consumption data.
2. Filtering the dataset to one selected metering grid area.
3. Aggregating consumption across all customer groups for each hour.
4. Converting hourly electricity consumption from kWh to average power in MW.
5. Visualising hourly electricity demand for January 2025.

**Power conversion:**

```python
df["Power (MW)"] = df["VOLUM_KWH"] / 1000
```

Mathematically, since each observation covers one hour:

**Average power (MW) = Hourly consumption (kWh) / 1000**

For example, 450,000 kWh consumed over one hour corresponds to an average power of 450 MW.

## Planned Development

The prototype will gradually be extended through the following stages.

### 1. Load Forecasting

Develop statistical models to predict hourly electricity demand using historical consumption patterns, time variables and seasonal effects.

### 2. Grid Constraint Identification

Compare predicted electricity demand against simulated grid capacity limits to identify potential overload periods.

### 3. Flexibility Requirement Estimation

Calculate the amount of flexibility required to relieve a predicted constraint.

**Required flexibility (MW) = max(0, Forecast demand − Grid capacity)**

### 4. Flexibility Availability Estimation

Introduce simulated flexible resources and estimate their expected availability at different times.

Future models may incorporate uncertainty and the probability that sufficient flexibility can be delivered.

### 5. Decision Support

Evaluate whether available flexibility can cover predicted grid constraints and compare possible resource combinations based on capacity, availability and cost.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook

## Project Status

**Early-stage research and prototype development.**

The current implementation focuses on historical electricity consumption analysis.

Load forecasting, constraint identification, flexibility estimation and decision-support functionality are planned extensions.

Public Elhub consumption data does not provide the detailed network topology, actual grid capacity limits or individual flexibility resource information required for operational assessments. These inputs will initially be simulated.

NDMS is an experimental project and is not intended for real-world grid operation or flexibility activation at this stage.
