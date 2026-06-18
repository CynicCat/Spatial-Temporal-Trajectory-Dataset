# Independent

## Description

Synthetic or independently-sourced spatio-temporal point process data. Each sequence contains events with time and 2D spatial coordinates.

## Data Format

The data is stored in pickle (`.pkl`) files split into train/val/test sets:

| File | Size | Sequences |
|------|------|-----------|
| `data_train.pkl` | ~5.4 MB | 5,000 |
| `data_val.pkl` | ~214 KB | — |
| `data_test.pkl` | ~214 KB | — |

## Data Schema

Each sequence is a list of events, where each event is a 3-element list:

```
[time, x, y]
```

| Field | Type | Description |
|-------|------|-------------|
| `time` | float | Timestamp of the event |
| `x` | float | X-coordinate (arbitrary spatial dimension) |
| `y` | float | Y-coordinate (arbitrary spatial dimension) |

## Example

```python
import pickle

with open('data_train.pkl', 'rb') as f:
    data = pickle.load(f)

print(len(data))        # 5000 sequences
print(data[0][:5])      # first 5 events of first sequence
# [[0.306, 5.433, 5.764], [0.401, 6.571, 6.160], ...]
```

## Task

Spatio-temporal point process modeling — general-purpose event sequence prediction in continuous time and space.
