# Tencent

## Description

Large-scale road network and trajectory dataset from Tencent Maps (tencent.com). Contains road network graphs, vehicle GPS traces, and preprocessed data for map-matching and route recovery tasks.

## Data Format

### Directory Structure

```
tencent/
├── GraphMM/          # Graph map-matching data
│   ├── road.txt       # Road network (8,533 segments)
│   ├── trace.txt      # Vehicle GPS traces (311,634 points)
│   ├── road_graph.pkl # Road graph structure
│   ├── road_graph_pt/ # PyTorch road graph
│   └── data0.5/       #
│       └── used_pkl/  # Mapping dictionaries
├── DeepMM/            # Deep map-matching data
│   ├── test.block     # Test road segments
│   ├── test.seg       # Test segment IDs
│   ├── test.time1/2   # Test timestamps
│   ├── train.block    # Training road segments
│   ├── train.seg      # Training segment IDs
│   ├── train.time1/2  # Training timestamps
│   ├── valid.block    # Validation road segments
│   ├── valid.seg      # Validation segment IDs
│   └── valid.time1/2  # Validation timestamps
├── DeepMMlogs/        # Training logs
├── DeepMMmodels/      # Trained model checkpoints
└── DeepMMsamples/     # Generated samples
```

### Road Network (`road.txt`)

Each line represents a road segment:

```
road_id start_node end_node direction road_class lane_count geometry
```

| Field | Type | Description |
|-------|------|-------------|
| `road_id` | int | Unique road segment ID |
| `start_node` | int | Start intersection node ID |
| `end_node` | int | End intersection node ID |
| `direction` | int | Direction code |
| `road_class` | int | Road class/type |
| `lane_count` | int | Number of lanes |
| `geometry` | string | Space-separated `lon lat` pairs, `;`-separated for intermediate points; `\|`-separated for full segment geometry |

### GPS Traces (`trace.txt`)

```
record_id,trace_id,user_id
timestamp,lat,lon,speed,direction,...
```

## Example

**Road network:**
```
4736	13535	1825	2	3	2	116.3414171 40.0795484,116.3420562 40.0801667|4725,13535,116.3414171 40.0795484;6135,13535,116.3414171 40.0795484;...
```

**GPS traces:**
```
#,6221427912124254782,6221427912124254782
2022/03/03 18:24:23,40.07856,116.30941,744,40.07879261945333,116.3096391218959,0,0.7528351264902587,0.7528351264902587
```

## Task

Map matching, route recovery, trajectory generation conditioned on road networks.

## Source

Tencent Maps, via [AI4DataSynth](https://github.com/AI4DataSynth/Spatial-Temporal-Trajectory-Dataset).
