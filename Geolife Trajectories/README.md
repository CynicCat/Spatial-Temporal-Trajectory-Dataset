# Geolife Trajectories

## Description

The Geolife GPS trajectory dataset collected by Microsoft Research Asia. It contains 18,670 trajectories from 182 users over a period of over three years (April 2007 to August 2012). Trajectories include a variety of activities such as walking, cycling, driving, and public transit.

## Data Format

| Directory | Contents |
|-----------|----------|
| `Data/` | 182 user folders (numbered `000`–`181`) |
| `User Guide-1.3.pdf` | Original dataset documentation |

Each user folder contains `.plt` files — one per trajectory. Each `.plt` file is a text file with a header and GPS point records.

### File Structure

Each `.plt` file contains:

```
Geolife trajectory
WGS 84
Altitude is in Feet
Reserved 3
0,2,255,My Track,0,0,2,8421376
0
latitude,longitude,altitude,date,time
```

### Data Schema

| Field | Type | Description |
|-------|------|-------------|
| `latitude` | float | Latitude in WGS84 (decimal degrees) |
| `longitude` | float | Longitude in WGS84 (decimal degrees) |
| `altitude` | float (0 or -777) | Altitude in feet (often 0 = unavailable) |
| `date` | string | Date in `YYYY-MM-DD` format |
| `time` | string | Time in `HH:MM:SS` format |

After the header lines, each row has the format:
```
latitude,longitude,0,altitude,days_since_1899-12-30,date,time
```

## Example

```
Geolife trajectory
WGS 84
Altitude is in Feet
Reserved 3
0,2,255,My Track,0,0,2,8421376
0
39.984702,116.318417,0,492,39744.1201851852,2008-10-23,02:53:04
39.984683,116.318450,0,492,39744.1202546296,2008-10-23,02:53:10
39.984688,116.318385,0,492,39744.1203703704,2008-10-23,02:53:20
```

```python
import pandas as pd
import os

def read_plt(filepath):
    """Read a single Geolife .plt file, skipping the 6-line header."""
    df = pd.read_csv(filepath, skiprows=6, header=None,
                     names=['latitude', 'longitude', 'zero', 'altitude',
                            'date_days', 'date', 'time'])
    df['datetime'] = pd.to_datetime(df['date'] + ' ' + df['time'])
    return df[['latitude', 'longitude', 'datetime']]

# Read first trajectory of user 000
user_dir = 'Data/000/Trajectory/'
first_file = sorted(os.listdir(user_dir))[0]
traj = read_plt(user_dir + first_file)
print(traj.head())
```

## Task

Trajectory classification, transportation mode detection, and mobility pattern mining.

## Source

Microsoft Research Asia Geolife project, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
