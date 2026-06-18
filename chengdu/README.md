# Chengdu

## Description

Chengdu taxi trajectory dataset. Contains GPS trajectories of taxis operating in Chengdu, China. Includes preprocessed data for multiple trajectory modeling baselines (DeepTTE, MulTTTE, TrajBERT).

## Data Format

### Raw Data

| File | Records | Description |
|------|---------|-------------|
| `chengdu.csv` | 181,173 | Raw taxi trajectory records |

### Data Schema

```
TAXI_ID,TIMESTAMP,TIMESTAMPS,POLYLINE,NUM_POINT
```

| Field | Type | Description |
|-------|------|-------------|
| `TAXI_ID` | string (hex) | Hashed taxi identifier |
| `TIMESTAMP` | int | Unix timestamp (seconds) of the first GPS point |
| `TIMESTAMPS` | string (JSON array) | Array of Unix timestamps for each GPS point |
| `POLYLINE` | string (JSON array) | Array of `[longitude, latitude]` pairs |
| `NUM_POINT` | int | Number of GPS points in the trajectory |

### DeepTTE Format

| File | Description |
|------|-------------|
| `DeepTTE/chengdu_DeepTTE_train.txt` | Training split |
| `DeepTTE/chengdu_DeepTTE_val.txt` | Validation split |
| `DeepTTE/chengdu_DeepTTE_test.txt` | Test split |

### MulTTTE Format

Network graph data in pickle format under `MulTTTE/network-chengdu/`.

### TrajBERT Format

Preprocessed trajectory representations under `TrajBERT/`.

## Example

```python
import pandas as pd
import json

df = pd.read_csv('chengdu.csv')
row = df.iloc[0]

print(f"Taxi ID: {row['TAXI_ID']}")
print(f"Start time: {row['TIMESTAMP']}")
print(f"Points: {row['NUM_POINT']}")

# Parse polyline
polyline = json.loads(row['POLYLINE'])
print(f"First 3 GPS points: {polyline[:3]}")
# [[lon1, lat1], [lon2, lat2], [lon3, lat3]]
```

## Task

Travel time estimation, trajectory representation learning, and route modeling.

## Source

Chengdu taxi GPS data, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
