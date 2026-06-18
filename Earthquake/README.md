# Earthquake

## Description

Earthquake event data represented as spatio-temporal sequences. Each sequence records earthquake occurrences with their magnitudes and epicenter coordinates over time.

## Data Format

The data is stored in pickle (`.pkl`) files split into train/val/test sets:

| File | Size | Sequences |
|------|------|-----------|
| `data_train.pkl` | ~2.8 MB | 950 |
| `data_val.pkl` | ~141 KB | — |
| `data_test.pkl` | ~174 KB | — |

## Data Schema

Each sequence is a list of events, where each event is a 3-element list:

```
[normalized_time, longitude, latitude]
```

| Field | Type | Description |
|-------|------|-------------|
| `normalized_time` | float | Normalized timestamp of the earthquake |
| `longitude` | float | Longitude of the epicenter |
| `latitude` | float | Latitude of the epicenter |

## Example

```python
import pickle

with open('data_train.pkl', 'rb') as f:
    data = pickle.load(f)

print(len(data))        # 950 sequences
print(data[0][:3])      # first 3 events of first sequence
# [[0.244, 140.039, 27.653], [0.361, 127.876, 28.716], ...]
```

## Task

Spatio-temporal point process modeling — predicting future earthquake locations and timing.

## Source

Seismic monitoring catalogs (e.g., USGS, JMA).
