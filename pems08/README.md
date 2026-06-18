# PEMS08

## Description

Traffic flow dataset from the Caltrans Performance Measurement System (PeMS). Contains traffic measurements from 170 sensors in the San Bernardino area collected at 5-minute intervals over 62 days (July–August 2016).

## Data Format

### Main Data

| File | Format | Description |
|------|--------|-------------|
| `pems08.npz` | NumPy | Traffic data in compressed format (~17.7 MB) |

### NPZ Structure

| Key | Shape | Description |
|-----|-------|-------------|
| `data` | `(num_timesteps, num_sensors, num_features)` | Traffic flow data (3 features: flow, occupy, speed) |

### Graph

| File | Description |
|------|-------------|
| `distance.csv` | Pairwise sensor distances (from, to, cost in meters) |

### Output (`output/`)

| File | Description |
|------|-------------|
| `PEMSD8.dyna` | Dynamic feature matrix |
| `PEMSD8.geo` | Sensor geo-coordinates |
| `PEMSD8.rel` | Sensor relation/adjacency data |

## Example

```python
import numpy as np

data = np.load('pems08.npz', allow_pickle=True)
print(data.keys())  # ['data']

traffic = data['data']  # shape: (timesteps, 170, 3)
print(f"Shape: {traffic.shape}")
print(f"First 3 timesteps for sensor 0:\n{traffic[:3, 0, :]}")

# Load distances
import pandas as pd
dist = pd.read_csv('distance.csv')
print(dist.head())
```

## Task

Traffic flow forecasting — predict future traffic conditions (flow, occupancy, speed) given historical sensor readings and road network topology.

## Source

Caltrans PeMS, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
