# LIMP (LLM-based Intent-aware Mobility Prediction)

## Description

LIMP is an LLM-based intent-aware mobility prediction dataset containing mobile application location data from Beijing and call detail records (CDR) from Shanghai. It includes human-annotated mobility intent labels for a subset of the Beijing data, covering 6 intent categories.

## Introduction

We collected two representative datasets: one comprising mobile application location data from a popular social network vendor, referred to as the Beijing dataset, and the other consisting of call detail records (CDR) data from a major cellular network operator, referred to as the Shanghai dataset. The data generation mechanisms differ significantly: mobile application data with location records is generated on application servers when users request location-based services within the app, while call detail records data with location information is generated at cellular network base stations when users access the network for communication or data services.

## Data Statistics

| Dataset | City | Users | POIs | Records | Time Span |
|---------|------|-------|------|---------|-----------|
| Beijing | Beijing | 1,566 | 5,919 | 744,813 | Sep–Nov 2019 |
| Shanghai | Shanghai | 841 | 6,955 | 215,379 | Jan 2016 |

## Data Format

### Raw Data (`beijing/` and `shanghai/`)

CSV files with the following columns:

| Field | Type | Description |
|-------|------|-------------|
| `trajectory_id` | string | Trajectory identifier (`{user_id}_{seq_num}`) |
| `user_id` | int | Anonymous user ID |
| `start_time` | datetime | Arrival time at POI |
| `end_time` | datetime | Departure time (Beijing only) |
| `poi_id` | string | POI identifier (e.g., `POI_12098...`) |
| `POI_name` | string | Name of the POI |
| `POI_category_id` | int | Category ID |
| `POI_category_name` | string | Category name |
| `longitude` | float | Longitude |
| `latitude` | float | Latitude |
| `norm_in_day_time` | float | Normalized arrival time [0,1] within a day |

### Intent Labels (`intent_label.csv`)

Manually annotated by 10 undergraduate students on a subset of 4,005 records from 71 Beijing users. The annotation logic first labels "At Home" and "Working" based on daily behavior patterns, then labels other intents based on POI information and visit time.

| Column | Description |
|--------|-------------|
| `intent` | Intent category in Chinese |
| `intent_en` | Intent category in English |

6 intent categories: `At Home`, `Working`, `Running Errands`, `Shopping`, `Leisure and Entertainment`, `Eating Out`.

### Pipeline Directories

| Directory | Purpose |
|-----------|---------|
| `A2I/` | Address-to-Intent: POI → intent mapping data (step 1) |
| `SFT/` | Supervised Fine-Tuning: training data for intent prediction (step 2) |
| `Predict/` | Trajectory prediction: next-location prediction data (step 3) |

## Example

```python
import pandas as pd

# Load Beijing data
df = pd.read_csv('beijing/beijing_train_1566.csv')
print(df.head())
```

```
  trajectory_id user_id          start_time            end_time  ... longitude latitude norm_in_day_time
0          29_1      29 2019-10-07 11:33:10 2019-10-07 21:52:16  ...    116.32    40.01           0.458
1          29_2      29 2019-10-07 23:17:30 2019-10-08 03:03:11  ...   116.325     40.0           0.958
```

## Task

Intent-aware next-location prediction — jointly predict a user's mobility intent and their next destination given historical trajectory and POI context.

## Source

LIMP paper, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
