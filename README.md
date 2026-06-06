# Training Trajectories Datasets

This repository contains preprocessed datasets used in the paper *Unsupervised Concept Drift 
Monitoring Using Training Paths of IPLNA*.

## Contents

Each dataset is provided as a zipped folder containing preprocessed Parquet files. Each Parquet 
file represents a single measurement window of a signal, resampled and normalised, ready for 
direct use in the training trajectory framework.

### Datasets

| Folder | Description | Source |
|--------|-------------|--------|
| `mass_spring_damper/` | Simulated MISO mechanical system with four damping coefficients ($k \in \{1.1, 1.5, 2, 3\}$) | Generated |
| `ball_bearing_degradation/` | Simulated gradual bearing degradation with five fault types (ball spin, inner race, outer race, cage, normal) | Generated |
| `cwru/` | Case Western Reserve University bearing fault dataset, 12k Drive End, 1797 rpm, 706 time series of 2048 samples | [CWRU Bearing Data Center](https://engineering.case.edu/bearingdatacenter) |
| `femto/` | FEMTO-ST PRONOSTIA accelerated bearing life tests | [NASA Prognostics Data Repository](https://www.nasa.gov/intelligent-systems-division/discovery-and-systems-health/pcoe/pcoe-data-set-repository/) |

## Format

Each Parquet file contains a single measurement window with the following structure:
- Rows: time samples
- Columns: signal channels (or lagged features, depending on the dataset)
- Filename encodes metadata (e.g. condition label, bearing ID, window index)

## Usage

```python
import pandas as pd

df = pd.read_parquet('path/to/file.parquet')
```

## Citation

If you use these datasets, please cite the original sources where applicable (see paper for 
full references) and this repository.
