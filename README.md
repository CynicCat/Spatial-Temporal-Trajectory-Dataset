# Spatial-Temporal Trajectory Dataset

A curated collection of 19 spatial-temporal trajectory and mobility datasets for research in trajectory modeling, location prediction, and spatio-temporal point processes.

## Dataset Overview

| # | Dataset | Type | Records | Format | Task |
|---|---------|------|---------|--------|------|
| 1 | [COVID19](COVID19/) | Spatio-temporal events | 1,450 seq | Pickle | Point process modeling |
| 2 | [Citibike](Citibike/) | Bike trips | 2,440 seq | Pickle | Mobility prediction |
| 3 | [Crime](Crime/) | Categorical events | 3,000 seq | Pickle | Marked point process |
| 4 | [Earthquake](Earthquake/) | Seismic events | 950 seq | Pickle | Spatio-temporal prediction |
| 5 | [Independent](Independent/) | Point process | 5,000 seq | Pickle | General STPP |
| 6 | [Geolife Trajectories](Geolife%20Trajectories/) | GPS trajectories | 18,670 traj | PLT text | Trajectory classification |
| 7 | [Brightkite](brightkite/) | LBSN check-ins | 4.7M | TXT | Location prediction |
| 8 | [Foursquare](foursquare/) | LBSN check-ins + POI | 33.3M | TXT | Venue recommendation |
| 9 | [Gowalla](gowalla/) | LBSN check-ins | 6.4M | TXT | Mobility modeling |
| 10 | [AgentMove](agentmove/) | Multi-city check-ins | 3.1M | CSV/JSON/NPZ | Cross-city transfer |
| 11 | [Chengdu](chengdu/) | Taxi trajectories | 181K | CSV | Travel time estimation |
| 12 | [Porto](porto/) | Taxi trajectories | 1.7M | CSV | Trajectory similarity |
| 13 | [LIMP](limp/) | Mobility + intent | 960K | CSV | Intent-aware prediction |
| 14 | [METR-LA](metr_la/) | Traffic speed | 207 sensors | HDF5 | Traffic forecasting |
| 15 | [PEMS08](pems08/) | Traffic flow | 170 sensors | NPZ | Traffic forecasting |
| 16 | [PEMS-Bay](pems_bay/) | Traffic speed | 325 sensors | HDF5 | Traffic forecasting |
| 17 | [Tencent](tencent/) | Road network + GPS | 320K | TXT | Map matching |
| 18 | [Source](source/) | Transfer source domain | 33.6M | CSV/TXT | Cross-city pretraining |
| 19 | [Target](target/) | Transfer target domain | 53.2M | CSV | Domain adaptation |

## Data Categories

### Spatio-Temporal Point Processes
[COVID19](COVID19/) · [Citibike](Citibike/) · [Crime](Crime/) · [Earthquake](Earthquake/) · [Independent](Independent/)

### LBSN Check-ins
[Brightkite](brightkite/) · [Foursquare](foursquare/) · [Gowalla](gowalla/) · [AgentMove](agentmove/)

### Trajectories
[Geolife Trajectories](Geolife%20Trajectories/) · [Chengdu](chengdu/) · [Porto](porto/)

### Traffic
[METR-LA](metr_la/) · [PEMS08](pems08/) · [PEMS-Bay](pems_bay/) · [Tencent](tencent/)

### Mobility & Transfer Learning
[LIMP](limp/) · [Source](source/) · [Target](target/)

## Quick Start

Each dataset directory contains:
- **README.md** — detailed format description
- **`example/`** — sample data files showing the exact format

## License

Datasets are provided for research purposes. Refer to original sources for specific licenses.

## Citation

If you use these datasets, please cite both the original dataset sources and this repository:

```bibtex
@misc{ai4datasynth2024,
  title     = {Spatial-Temporal Trajectory Dataset},
  author    = {AI4DataSynth},
  year      = {2024},
  publisher = {GitHub},
  url       = {https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset}
}
```
