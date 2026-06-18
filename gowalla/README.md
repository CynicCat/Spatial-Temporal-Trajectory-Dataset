# Gowalla

## Description

Gowalla was a location-based social networking service where users checked in at venues. This dataset contains the global check-in records with user IDs, timestamps, and geographic coordinates.

## Data Format

| File | Records | Size |
|------|---------|------|
| `Checkins_Unknown.txt` | 6,442,892 | ~259 MB |

## Data Schema

Tab-separated file with the following columns:

```
user_id	timestamp	latitude	longitude	venue_id
```

| Field | Type | Description |
|-------|------|-------------|
| `user_id` | int | Anonymous user identifier |
| `timestamp` | string (ISO 8601) | UTC timestamp in `YYYY-MM-DDTHH:MM:SSZ` format |
| `latitude` | float | Latitude coordinate (WGS84) |
| `longitude` | float | Longitude coordinate (WGS84) |
| `venue_id` | int | Venue identifier |

## Example

```
0	2010-10-19T23:55:27Z	30.2359091167	-97.7951395833	22847
0	2010-10-18T22:17:43Z	30.2691029532	-97.7493953705	420315
0	2010-10-17T23:42:03Z	30.2557309927	-97.7633857727	316637
```

```python
import pandas as pd

df = pd.read_csv('Checkins_Unknown.txt', sep='\t', header=None,
                 names=['user_id', 'timestamp', 'latitude', 'longitude', 'venue_id'])
df['timestamp'] = pd.to_datetime(df['timestamp'])
print(df.head())
```

## Task

Location-based social network analysis — user mobility modeling, friend recommendation, and location prediction from check-in behavior.

## Source

Gowalla (originally from SNAP Stanford), via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
