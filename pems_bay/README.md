# PEMS-Bay

## Description

Traffic speed dataset from 325 loop detectors in the San Francisco Bay Area. Collected by the Caltrans Performance Measurement System (PeMS) at 5-minute intervals over 6 months (January–June 2017).

## Data Format

### Main Data

| File | Format | Description |
|------|--------|-------------|
| `pems-bay.h5` | HDF5 | Traffic speed data matrix |

### HDF5 Structure

| Key | Shape | Description |
|-----|-------|-------------|
| `speed` | `(num_timesteps, num_sensors)` | Traffic speed values (mph or km/h) |

### Sensor Metadata

| File | Description |
|------|-------------|
| `graph_sensor_locations_bay.csv` | Sensor IDs and GPS coordinates |
| `distances_bay_2017.csv` | Pairwise sensor distances |

### Sensor Locations

```
sensor_id,latitude,longitude
```

### Distance Matrix

```
from_sensor,to_sensor,distance(meters)
```

## Example

```python
import h5py
import pandas as pd

# Read speed data
with h5py.File('pems-bay.h5', 'r') as f:
    print(f.keys())
    speeds = f['speed'][:]  # shape: (num_timesteps, 325)

# Read sensor locations
sensors = pd.read_csv('graph_sensor_locations_bay.csv')
print(sensors.head())

# Read distances
distances = pd.read_csv('distances_bay_2017.csv')
print(distances.head())
#    400001,400001,0.0
#    400030,400045,5108.4
```

## Task

Traffic speed forecasting — predict future traffic speeds across 325 Bay Area sensors using spatial-temporal graph neural networks.

## Source

Caltrans PeMS (DCRNN paper), via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
