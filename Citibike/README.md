# Citibike

## Description

Citi Bike trip trajectory data from New York City's bike-sharing system. Each sequence represents a bike's movement across stations over time.

## Data Format

The data is stored in pickle (`.pkl`) files split into train/val/test sets:

| File | Size | Sequences |
|------|------|-----------|
| `data_train.pkl` | ~10.7 MB | 2,440 |
| `data_val.pkl` | ~1.6 MB | — |
| `data_test.pkl` | ~1.6 MB | — |

## Data Schema

Each sequence is a list of events, where each event is a 3-element list:

```
[time, longitude, latitude]
```

| Field | Type | Description |
|-------|------|-------------|
| `time` | float | Timestamp (in hours from start) |
| `longitude` | float | Longitude of the bike station |
| `latitude` | float | Latitude of the bike station |

## Example

```python
import pickle

with open('data_train.pkl', 'rb') as f:
    data = pickle.load(f)

print(len(data))        # 2440 sequences
print(data[0][:3])      # first 3 events of first sequence
# [[1.062, -73.942, 40.788], [1.467, -73.995, 40.751], ...]
```

## Task

Spatio-temporal event prediction — modeling bike trip patterns and predicting future bike usage across NYC stations.

## Source

Citi Bike NYC trip data.
