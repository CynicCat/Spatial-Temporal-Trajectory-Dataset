# Crime

## Description

Crime event data represented as temporal event sequences with categorical event types. Each sequence records the occurrence of crime incidents over time, categorized by crime type.

## Data Format

The data is stored in pickle (`.pkl`) files split into train/val/test sets:

| File | Size | Sequences |
|------|------|-----------|
| `data_train.pkl` | ~4.3 MB | 3,000 |
| `data_val.pkl` | ~605 KB | — |
| `data_test.pkl` | ~875 KB | — |

Additional metadata:
- `event_type_num.json` — number of distinct crime types: **243**

## Data Schema

Each sequence is a list of events, where each event is a 2-element list:

```
[time, event_type_id]
```

| Field | Type | Description |
|-------|------|-------------|
| `time` | float | Timestamp of the crime incident |
| `event_type_id` | int | ID of the crime category (0–242) |

## Example

```python
import pickle, json

with open('data_train.pkl', 'rb') as f:
    data = pickle.load(f)

with open('event_type_num.json', 'r') as f:
    meta = json.load(f)

print(meta)             # {'num': 243}
print(len(data))        # 3000 sequences
print(data[0][:5])      # first 5 events of first sequence
# [[1.417, 177], [1.683, 81], [1.9, 174], [2.0, 122], [4.5, 54]]
```

## Task

Temporal point process modeling with categorical marks — predicting when and what type of crime will occur next.

## Source

Crime incident reports.
