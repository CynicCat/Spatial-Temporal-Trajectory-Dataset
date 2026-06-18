# Source

## Description

Source-domain check-in data for cross-city transfer learning. Contains check-in records from the Foursquare global dataset (Tokyo, New York, London, and other cities) reformatted with city labels and venue categories. Used as the source domain for training mobility models that transfer to the Target datasets.

## Data Format

| File | Records | Description |
|------|---------|-------------|
| `source1.csv` | 380,248 | Check-ins with city/user/time/venue/location/category |
| `source1.txt` | 3,680,126 | POI metadata (venue_id, lat, lon, category, country) |
| `source2.txt` | 33,263,633 | Raw check-in stream (similar to Foursquare) |

## Data Schema

### `source1.csv`

```
City,User ID,Time Offset,Venue ID(Foursquare),UTC Time,Longitude,Latitude,Venue Category Name
```

| Field | Type | Description |
|-------|------|-------------|
| `City` | string | City name |
| `User ID` | int | Anonymous user ID |
| `Time Offset` | int | Timezone offset in minutes |
| `Venue ID(Foursquare)` | string (hex) | Foursquare venue ID |
| `UTC Time` | string | Timestamp |
| `Longitude` | float | Longitude |
| `Latitude` | float | Latitude |
| `Venue Category Name` | string | POI category |

### `source1.txt` (POIs)

```
venue_id	latitude	longitude	category	country
```

### `source2.txt` (Raw Check-ins)

```
user_id	venue_id	utc_time	timezone_offset
```

## Example

**source1.csv:**
```
City,User ID,Time Offset,Venue ID(Foursquare),UTC Time,Longitude,Latitude,Venue Category Name
New York,221021,-240,4a85b1b3f964a520eefe1fe3,Tue Apr 03 18:00:08 +0000 2012,-73.99228,40.748939,Coffee Shop
```

**source1.txt:**
```
3fd66200f964a52000e71ee3	40.733596	-74.003139	Jazz Club	US
```

## Task

Source domain for cross-city transfer learning — train a mobility model on source cities and adapt to new target cities.

## Source

Foursquare global check-in data, processed for cross-city transfer learning, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
