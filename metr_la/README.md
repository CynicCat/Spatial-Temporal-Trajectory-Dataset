# METR-LA

## Description

Traffic speed dataset from loop detectors in the Los Angeles County highway system. Contains average traffic speeds measured by 207 sensors at 5-minute intervals over 4 months (March–June 2012).

## Data Format

### Main Data

| File | Format | Description |
|------|--------|-------------|
| `metr-la.h5` | HDF5 | Traffic speed data matrix |

### HDF5 Structure

| Key | Shape | Description |
|-----|-------|-------------|
| `df` | `(num_sensors, num_timesteps)` | Traffic speed values |
| `axis0` | `(num_sensors,)` | Sensor IDs |
| `axis1` | `(num_timesteps,)` | Timestamps |

### Sensor Graph (`sensor_graph/`)

| File | Description |
|------|-------------|
| `adj_mx.pkl` | Adjacency matrix (sensor proximity graph) |
| `graph_sensor_ids.csv` | Sensor ID mapping |

### Output Directory (`output/`)

Contains precomputed model outputs for baselines.

## Example

```python
import h5py
import numpy as np

with h5py.File('metr-la.h5', 'r') as f:
    print(f.keys())  # ['axis0', 'axis1', 'block0_values', ...]
    speeds = f['df'][:]  # shape: (num_timesteps, num_sensors)
    sensor_ids = f['axis0'][:]  # shape: (num_sensors,)
    timestamps = f['axis1'][:]  # shape: (num_timesteps,)

print(f"Sensors: {speeds.shape[1]}, Timesteps: {speeds.shape[0]}")
print(f"Sample speeds (first 5 sensors, first 3 timesteps):\n{speeds[:3, :5]}")
```

## Task

Traffic forecasting — predict future traffic speeds across the sensor network given historical observations.

## Source

Los Angeles County traffic loop detectors (DCRNN paper), via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
