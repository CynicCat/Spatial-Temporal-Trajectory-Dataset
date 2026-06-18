# AgentMove

## Description

AgentMove is a comprehensive check-in dataset covering 11 global cities with venue category information. It is designed for agent-based mobility modeling and cross-city transfer learning. Also includes preprocessed NPZ training data and JSON trajectory representations.

## Data Format

### Check-in Data

CSV files for each city with the same schema:

| City | Records |
|------|---------|
| `Checkins_CapeTown.csv` | 13,304 |
| `Checkins_London.csv` | 188,531 |
| `Checkins_Moscow.csv` | 353,911 |
| `Checkins_Mumbai.csv` | 40,593 |
| `Checkins_Nairobi.csv` | 28,454 |
| `Checkins_NewYork.csv` | 380,248 |
| `Checkins_Paris.csv` | 111,326 |
| `Checkins_SanFrancisco.csv` | 106,649 |
| `Checkins_SaoPaulo.csv` | 809,199 |
| `Checkins_Sydney.csv` | 54,251 |
| `Checkins_Tokyo.csv` | 1,030,106 |
| **Total** | **3,116,572** |

### Data Schema

```
city,user,time,venue_id,utc_time,lon,lat,venue_cat_name
```

| Field | Type | Description |
|-------|------|-------------|
| `city` | string | City name |
| `user` | int | User ID |
| `time` | int | Time offset (minutes) |
| `venue_id` | string (hex) | Venue identifier (Foursquare-compatible) |
| `utc_time` | string | UTC timestamp |
| `lon` | float | Longitude |
| `lat` | float | Latitude |
| `venue_cat_name` | string | Venue category name |

### Additional Files

| File | Description |
|------|-------------|
| `1000_1000_all.json` | Trajectory sequences in JSON format |
| `1000_1000_cat.json` | Category-annotated trajectories |
| `1000_1000_loc.json` | Location-only trajectory data |
| `1000_1000_time.json` | Time-only trajectory data |
| `1000_1000_train.npz` | Preprocessed training data (NumPy format) |
| `Tokyo2_filtered.csv` | Filtered Tokyo subset |

### JSON Trajectory Format

Each trajectory is a list of events, where each event is:

```
[event_id, location_id, time_id, user_id, sequence_pos, lon, lat]
```

## Example

**Check-ins:**
```python
import pandas as pd

df = pd.read_csv('Checkins_London.csv')
print(df.head())
```

```
   city    user  time                         venue_id  ...       lon       lat venue_cat_name
London  262915    60  4aec9f4bf964a52091c921e3  ... -0.090546  51.498044            Pub
London   78404    60  4b9024ccf964a5204a7833e3  ... -0.302248  51.514978      Restaurant
```

**JSON Trajectories:**
```python
import json

with open('1000_1000_all.json') as f:
    trajs = json.load(f)

# Each user ID maps to a list of trajectory segments
print(list(trajs.keys())[:3])  # ['1', '2', '3']
```

## Task

Cross-city mobility modeling, agent-based simulation, and transfer learning for location prediction.

## Source

AgentMove dataset, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
