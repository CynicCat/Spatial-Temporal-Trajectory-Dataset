# Foursquare

## Description

Foursquare is a location-based social network where users check in at venues. This dataset contains global check-in records and POI (Point of Interest) metadata including venue categories.

## Data Format

| File | Records | Size |
|------|---------|------|
| `Checkins_Unknown.txt` | 33,263,633 | ~1.1 GB |
| `POIs_Unknown.txt` | 3,680,126 | ~102 MB |

## Data Schema

### Check-ins (`Checkins_Unknown.txt`)

Tab-separated file:

```
user_id	venue_id	utc_time	timezone_offset
```

| Field | Type | Description |
|-------|------|-------------|
| `user_id` | int | Anonymous user identifier |
| `venue_id` | string (hex) | Foursquare venue ID |
| `utc_time` | string | UTC timestamp in `Day Mon DD HH:MM:SS +0000 YYYY` format |
| `timezone_offset` | int | Timezone offset in minutes from UTC |

### POIs (`POIs_Unknown.txt`)

Tab-separated file:

```
venue_id	latitude	longitude	venue_category	country
```

| Field | Type | Description |
|-------|------|-------------|
| `venue_id` | string (hex) | Foursquare venue ID (joins with check-ins) |
| `latitude` | float | Latitude coordinate |
| `longitude` | float | Longitude coordinate |
| `venue_category` | string | Category name (e.g., "Coffee Shop", "Gym") |
| `country` | string | Country code (e.g., "US") |

## Example

**Check-ins:**
```
50756	4f5e3a72e4b053fd6a4313f6	Tue Apr 03 18:00:06 +0000 2012	240
190571	4b4b87b5f964a5204a9f26e3	Tue Apr 03 18:00:07 +0000 2012	180
221021	4a85b1b3f964a520eefe1fe3	Tue Apr 03 18:00:08 +0000 2012	-240
```

**POIs:**
```
3fd66200f964a52000e71ee3	40.733596	-74.003139	Jazz Club	US
3fd66200f964a52000e81ee3	40.758102	-73.975734	Gym	US
```

```python
import pandas as pd

checkins = pd.read_csv('Checkins_Unknown.txt', sep='\t', header=None,
                        names=['user_id', 'venue_id', 'utc_time', 'timezone_offset'])
pois = pd.read_csv('POIs_Unknown.txt', sep='\t', header=None,
                    names=['venue_id', 'latitude', 'longitude', 'venue_category', 'country'])

# Join to get spatial coordinates
df = checkins.merge(pois, on='venue_id')
print(df.head())
```

## Task

Location-based social network analysis — venue recommendation, user mobility prediction, and category-aware next-POI prediction.

## Source

Foursquare, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
