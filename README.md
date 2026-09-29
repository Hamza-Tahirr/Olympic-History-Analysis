# Olympic History Analysis

Exploratory data analysis of 120 years of Olympic history, using basic bio data on athletes and medal results from Athens 1896 to Rio 2016.

## Current status

So far the repository only holds the NOC region lookup table from the dataset. The analysis itself and the main athlete file have not been added yet.

## Data

The project uses the Kaggle dataset
[120 years of Olympic history: athletes and results](https://www.kaggle.com/datasets/heesoo37/120-years-of-olympic-history-athletes-and-results).
It has two files:

| File | In this repo | Contents |
| --- | --- | --- |
| `noc_regions.csv` | Yes | Maps each National Olympic Committee (NOC) code to a region, with optional notes |
| `athlete_events.csv` | No | One row per athlete per event: ID, Name, Sex, Age, Height, Weight, Team, NOC, Games, Year, Season, City, Sport, Event, Medal |

`noc_regions.csv` lists 230 NOC codes, and 227 of them map to one of 206 regions. Historical teams point to the modern region, for example `URS` and `EUN` map to Russia, and `FRG` and `GDR` map to Germany. The `notes` column adds detail for some codes, such as "Netherlands Antilles" for `AHO` or "Hong Kong" for `HKG`.

The remaining three codes (`ROT`, `TUV`, `UNK`) have the region `NA`, which pandas reads as a missing value by default.

## Project structure

```
Olympic-History-Analysis/
├── noc_regions.csv   NOC code to region lookup
├── README.md
└── LICENSE
```

## Getting started

1. Clone the repository:

   ```bash
   git clone https://github.com/Hamza-Tahirr/Olympic-History-Analysis.git
   cd Olympic-History-Analysis
   ```

2. Download `athlete_events.csv` from the Kaggle page above and put it next to `noc_regions.csv`.

3. Load and join the two files, for example with pandas:

   ```python
   import pandas as pd

   athletes = pd.read_csv("athlete_events.csv")
   regions = pd.read_csv("noc_regions.csv")
   df = athletes.merge(regions, on="NOC", how="left")
   ```

## License

This repository is released under the [MIT License](LICENSE). The dataset itself is published on Kaggle under CC0: Public Domain.
