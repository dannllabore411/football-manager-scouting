# 📊 FM24 Scouting & Player Performance Analysis
This standalone data science project explores player performance data exported from *Football Manager 2024 (FM24)* to assist with transfer scouting. The notebook identifies high-performing players from the Bulgarian First League based on key in-game statistics, enabling data-driven shortlisting of transfer targets.

## 🔎 Data Sources
- **Player Search Export (HTML)**: Exported directly from FM24’s Player Search screen, containing player attributes and match stats.
- **Role-to-Position Mapping (CSV)**: A manually curated file (`role_pos.csv`) that maps FM-specific roles (e.g., Ball-Playing Defender, Deep-Lying Forward) to generalized position groups (`CB`, `CM`, `ST`, etc.).

## ⚙️ Pipeline Overview
### 1. Data Extraction & Cleaning  
**Skills Demonstrated**: *Web data parsing, text cleaning, type conversion, percentage handling, missing value imputation*
- Parsed raw player data from an HTML table.
- Cleaned monetary values, heights, distances, and percentages.
- Converted appropriate columns to numeric values and standardized missing/placeholder values.
### 2. Role Mapping  
**Skills Demonstrated**: *Data merging, categorical mapping*
- Mapped each player’s “Best Role” from FM24 to a broader positional group using `role_pos.csv`.
- Dropped redundant FM-specific columns (e.g., "Inf", "Best Role", "Best Duty").
### 3. Feature Engineering  
**Skills Demonstrated**: *Domain-based feature construction, conditional logic, normalization*
Derived new metrics designed to evaluate position-specific performance:
- **Goalkeepers**: `Save%`, `xGP/90`, `Shots/Conc`
- **Defenders**: `FoulPrev`, `DDAs`, `Hdr/90`, `Tck%`, `HDAs`
- **Midfielders/Wingers**: `Drbs/90`, `Pas%`, `ChQL`, `xAst/90`, `PrPas/90`
- **Attackers**: `xG/Shot`, `Conv%`, `S/90`, `xGOP/90`
These features are calculated per 90 minutes and designed to reflect in-game role effectiveness.
### 4. Scouting Output  
**Skills Demonstrated**: *Exploratory data analysis*
- The final output is a cleaned and enriched dataframe of FM24 players, suitable for manual filtering or future modeling/scoring.

## ▶️ How to Run
1. Export a custom Player Search view from FM24 and save it as an `.html` file.
2. Place the HTML file and `role_pos.csv` in the working directory.
3. Run the notebook (`fm24_old.ipynb`) in a Python environment with the following packages:
   pip install pandas numpy scipy
4. Outputs are printed directly in the notebook.

## 📁 Outputs
- A `pandas.DataFrame` containing player info and advanced metrics.
- Outputs are printed directly in the notebook.
- No files are written to disk at this stage.

## 🚧 Future Work
- **Scoring System**: Incorporate weighted role-based scores to rank players automatically.
- **Streamlit App**: Add filters and visualizations for a more interactive scouting dashboard.
- **Multi-league Integration**: Expand the view to include other leagues and simulate global scouting.
