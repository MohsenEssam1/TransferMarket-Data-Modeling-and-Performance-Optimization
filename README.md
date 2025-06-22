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

![schema](https://github.com/user-attachments/assets/a78e3a80-4e3b-4056-87d8-65b751904b8b)


# ETL Process
The data was extracted, transformed, and loaded using Python Pandas. The final processed data was saved into CSV files for further analysis.

# Converting CSV to Parquet and Avro  

This script converts CSV files into **Parquet** and **Avro** formats for better storage and performance.  

###  Steps:  
1. Reads all CSV files from the **source folder**.  
2. Ensures **target directories** for Parquet and Avro exist.  
3. Converts all columns to **string** for consistency.  
4. Saves the data as **Parquet** (columnar storage).  
5. Saves the data as **Avro** (schema-based binary format).  

### Tools Used:  
- **pandas** → Read & process CSV files  
- **pyarrow** → Convert DataFrames to Parquet  
- **fastavro** → Write Avro files  
- **os** → Handle directories & files  

### Execution:  
The script loops through CSV files, converts them, and saves the results in the respective folders.  

# Uploading to HDFS  

The dataset files (**CSV, Parquet, and Avro**) were uploaded to an **HDFS cluster** set up using Docker. The cluster ran in **pseudo-distributed mode**, ensuring a consistent and reproducible environment.  

###  Setup & Upload  
A **Hadoop container** was launched using Docker, mounting the dataset under `/data`. Files were uploaded to HDFS while measuring **write time**:  


## 🖼️ Sample Dashboard Preview

> 📌 *Visuals include transfer amounts, player positions, club analysis, timeline-based insights.*

  
  ![Players-Haland](https://github.com/user-attachments/assets/e8fb6284-9b93-47ad-a069-72dd43bb5eaa)

  ![Competitions](https://github.com/user-attachments/assets/207fd814-5c0f-45ac-85fd-ea50954b9471)


  

---

## ⚙️ Technologies Used

| Purpose              | Tools                        |
|----------------------|------------------------------|
| EDA & ETL            | Python, Pandas, Seaborn      |
| Storage              | CSV  |
| Visualization        | Power BI                     |
| Dashboard Export     | `.pbix`, PNG                  |










