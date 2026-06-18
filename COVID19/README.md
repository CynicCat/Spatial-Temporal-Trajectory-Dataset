# COVID19

## Description

COVID-19 case data represented as spatio-temporal event sequences. Each sequence records the progression of COVID cases across locations over time.

## Data Format

The data is stored in pickle (`.pkl`) files split into train/val/test sets:

| File | Size | Sequences |
|------|------|-----------|
| `data_train.pkl` | ~4.8 MB | 1,450 |
| `data_val.pkl` | ~149 KB | — |
| `data_test.pkl` | ~467 KB | — |

## Data Schema

Each sequence is a list of events, where each event is a 3-element list:

```
[normalized_time, longitude, latitude]
```

| Field | Type | Description |
|-------|------|-------------|
| `normalized_time` | float | Normalized timestamp of the case report |
| `longitude` | float | Longitude coordinate |
| `latitude` | float | Latitude coordinate |

## Example

```python
import pickle

with open('data_train.pkl', 'rb') as f:
    data = pickle.load(f)

# data is a list of sequences (list of lists)
print(len(data))        # 1450 sequences
print(data[0][:3])      # first 3 events of first sequence
# [[0.034, -74.860, 39.722], [0.067, -74.014, 40.761], ...]
```

## Task

Spatio-temporal point process modeling — predicting when and where future COVID cases will occur.

## Source

COVID-19 case surveillance data.
