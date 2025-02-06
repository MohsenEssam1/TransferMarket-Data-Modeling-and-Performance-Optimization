# TransferMarket-Data-Modeling-and-Performance-Optimization
# Project Overview
This project models the [Transfermarket dataset](https://www.kaggle.com/datasets/davidcariboo/player-scores) as a star schema and then implements the model on HDFS in CSV, Avro and Parquet formats using different compression algorithms and compares between formats in terms of size, write speed and read speed.

# Design the Star Schema
- **Fact Tables:**
  - `appearance_fact`: Stores player appearances in games.
  - `game_events_fact`: Captures game events such as:
    - Goals
    - Assists
    - Cards
  - `game_club_fact`: Represents club participation in games.
  - `transfer_fact`: Records player transfers between clubs.

- **Dimension Tables:**
  - `club`: Contains club details.
  - `competition`: Lists competitions.
  - `games`: Stores game metadata.
  - `player`: Includes player information.
  - `game_lineups`: Holds player lineups.
  - Event-related dimensions:
    - `substitutions`
    - `cards`
    - `goals`
    - `shootout`
    - `assist`

# ETL Process
The data was extracted, transformed, and loaded using Python Pandas. The final processed data was saved into CSV files for further analysis.

