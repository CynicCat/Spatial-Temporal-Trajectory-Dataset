# Porto

## Description

Porto taxi trajectory dataset. Contains GPS trajectories of taxis operating in Porto, Portugal. Includes preprocessed data for multiple trajectory modeling baselines (DeepTTE, MulTTTE, TrajBERT, TrajCL).

## Data Format

### Raw Data

| File | Records | Description |
|------|---------|-------------|
| `porto.csv` | 1,704,760 | Raw taxi trajectory records |

### Data Schema

```
TAXI_ID,TIMESTAMP,POLYLINE,NUM_POINT
```

| Field | Type | Description |
|-------|------|-------------|
| `TAXI_ID` | string/int | Taxi identifier |
| `TIMESTAMP` | int | Unix timestamp (seconds) of the first GPS point |
| `POLYLINE` | string (JSON array) | Array of `[longitude, latitude]` pairs |
| `NUM_POINT` | int | Number of GPS points in the trajectory |

### Baseline Preprocessed Data

| Directory | Baseline | Contents |
|-----------|----------|----------|
| `DeepTTE/` | DeepTTE | Train/val/test splits (`porto_DeepTTE_*.txt`) |
| `MulTTTE/` | MulTTTE | Road network graph (`network-porto/`) |
| `TrajBERT/` | TrajBERT | Preprocessed trajectory data |
| `TrajCL/` | TrajCL | 20,200 trajectory similarity matrices with augmentations |

### TrajCL Data

The `TrajCL/` directory contains trajectory similarity data for contrastive learning:

| File | Description |
|------|-------------|
| `porto_20200_newsimi_raw.pkl` | Raw similarity matrix (52,862 KB) |
| `porto_20200_newsimi_distort_0.1–0.5.pkl` | Distortion-augmented similarity |
| `porto_20200_newsimi_downsampling_0.1–0.5.pkl` | Downsampling-augmented similarity |
| `porto_20200_traj_simi_dict_*.pkl` | Similarity dictionaries (Frechet, EDR, EDwP, Hausdorff) |
| `porto_20200_cell100_embdim256_embs.pkl` | Learned trajectory embeddings |

## Example

```python
import pandas as pd
import json

df = pd.read_csv('porto.csv')
row = df.iloc[0]

print(f"Taxi ID: {row['TAXI_ID']}")
print(f"Start time: {row['TIMESTAMP']}")
print(f"Points: {row['NUM_POINT']}")

# Parse polyline
polyline = json.loads(row['POLYLINE'])
print(f"First 3 GPS points: {polyline[:3]}")
# [[-8.610291, 41.140746], [-8.6103, 41.140755], ...]
```

## Task

Travel time estimation, trajectory similarity learning, contrastive trajectory representation, and route modeling.

## Source

Porto taxi GPS data (Kaggle ECML/PKDD 2015), via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
