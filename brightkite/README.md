# Brightkite

## Description

Brightkite was a location-based social networking service where users shared their locations by checking in. This dataset contains the global check-in records with user IDs, timestamps, and geographic coordinates.

## Data Format

| File | Records | Size |
|------|---------|------|
| `Checkins_Unknown.txt` | 4,747,287 | ~185 MB |

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
| `venue_id` | string (hex) | Hashed venue identifier |

## Example

```
0	2010-10-17T01:48:53Z	39.747652	-104.99251	88c46bf20db295831bd2d1718ad7e6f5
0	2010-10-16T06:02:04Z	39.891383	-105.070814	7a0f88982aa015062b95e3b4843f9ca2
0	2010-10-14T18:25:51Z	39.750469	-104.999073	9848afcc62e500a01cf6fbf24b797732f8963683
```

```python
import pandas as pd

df = pd.read_csv('Checkins_Unknown.txt', sep='\t', header=None,
                 names=['user_id', 'timestamp', 'latitude', 'longitude', 'venue_id'])
df['timestamp'] = pd.to_datetime(df['timestamp'])
print(df.head())
```

## Task

Location-based social network analysis — user mobility modeling, next-location prediction, and social relationship inference from check-in patterns.

## Source

Brightkite (originally from SNAP Stanford), via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
