# 🏔️ Siachen Glacier Snowfall Analysis (1976–2025)

Long-term snowfall trend analysis over the Siachen Glacier region using ERA5 reanalysis data via [Open-Meteo Archive API.](https://open-meteo.com/en/docs/historical-weather-api)

<p align="center">
  <img src="img/siachen glacier.jpg" width="75%" alt="Siachen Glacier">
  <br><em>Siachen Glacier</em>
</p>

## 🎯 Project Goals

- Learn data engineering & scientific analysis through real-world climate data
- Move from single-point to **spatial mean** sampling (bounding box)
- Quantify long-term snowfall change over 50 years
- Create clear, reproducible, beginner-friendly code & documentation
- Answer: *Is snowfall declining over Siachen — and by how much?*

## 📍 Study Area

**Siachen Glacier (approximate bounding box)**

- **Latitude**:  35.10°N – 35.70°N  
- **Longitude**: 76.46°E – 77.42°E

Using a bounding box instead of a single point gives a more representative glacier-scale average and reduces sampling bias.



## 🧰 Data Source

| Item              | Value                              |
|-------------------|------------------------------------|
| API               | Open-Meteo Archive API             |
| Underlying model  | ERA5 / ERA5-Land                   |
| Variable          | `snowfall_sum` (daily total)       |
| Unit              | centimeters (cm)                   |
| Period fetched    | 1976-01-01 – 2025-12-31            |
| Temporal resolution | Daily                            |
| Spatial approach  | Bounding box → spatial mean        |

## ⚙️ Methodology Summary

1. **Data Acquisition**  
   - Multiple grid cells requested via bounding box parameters  
   - Daily `snowfall_sum` retrieved

2. **Processing**  
   - Parse JSON responses  
   - Compute daily **spatial mean** across all grid cells  
   - Aggregate to annual totals

3. **Analysis**  
   - Compare 1976–2000 vs 2001–2025  
   - Calculate absolute & percentage change  
   - Fit linear trend (cm/year)

4. **Visualization**  
   - Time series with trend line  
   - Bar comparison of two 25-year periods  
   - Trend slope visualization

## 📊 Key Results

| Metric                      | Value          | Notes                              |
|-----------------------------|----------------|------------------------------------|
| Period                      | 1976–2025      | 50 full years                      |
| Mean annual snowfall (early) | ~389 cm       | 1976–2000                          |
| Mean annual snowfall (recent)| ~348 cm       | 2001–2025                          |
| **Absolute change**         | **−40.8 cm**   |                                    |
| **Percentage change**       | **−10.5%**     |                                    |
| Linear trend                | **−1.11 cm/yr**| Statistically significant decline  |

***
<p align="center">
  <img src="img/annual snowfall with rolling mean.png" width="60%" alt="Annual Snowfall with rolling mean">
  <br><em>Annual Snowfall with rolling mean (1976-2025)</em>
</p>

**Interpretation**
The annual snowfall time series shows substantial interannual variability; however, the 5-year rolling mean reveals a clear declining trend over the years.

***
<p align="center">
  <img src="img/early vs recent comparison.png" width="60%" alt="Early vs recent period comparison">
  <br><em>Mean annual snowfall: 1976–2000 vs 2001–2025</em>
</p>

**Interpretation**  
The results show a consistent long-term **decline in snowfall accumulation** over the Siachen region — approximately **10–11%** less snow per year in the most recent 25 years compared to the previous 25-year period.

***
<p align="center">
  <img src="img/linear trend in annual snowfall.png" width="75%" alt="Annual snowfall time series 1976–2025">
  <br><em>Annual snowfall totals with linear trend (1976–2025)</em>
</p>

**Interpretation**  
A linear regression fitted to the annual snowfall data from 1976 to 2025 indicates a **statistically consistent declining trend** of approximately **1.11 cm per year**. Over five decades, this corresponds to a **cumulative reduction** of roughly **40 cm**, aligning with the observed difference between early and recent periods.

## 🔁 How to Reproduce

### Prerequisites

- Python 3.10+
- [uv](https://github.com/astral-sh/uv) (recommended package manager)

### Steps

```bash
# 1. Clone
git clone https://github.com/impriyanshusah/Siachen-Snowfall-Analysis.git
cd Siachen-snowfall-analysis

# 2. Install dependencies & create virtual environment
uv sync

# 3. Start Jupyter
uv run jupyter lab    # or directly open jupyter notebook in VS Code 

# 4. Open
notebooks/siachen_snowfall_analysis.ipynb
```

## 🚀 What I Learned

- Real-world API pagination & error handling
- Spatial averaging vs single-point sampling (why bounding box matters)
- When and how to effectively use bounding-box queries
- Clean separation of raw ↔ processed data
- Writing readable, reproducible Jupyter notebooks
- Knowing when **simple & correct** > **overly complex**

## 🔮 Possible Next Steps

- Seasonal decomposition (winter vs summer/monsoon snowfall)
- Co-analysis with temperature and total precipitation
- **Snowfall Water Equivalent (SWE)** estimation (better metric for glacier mass balance — requires density assumptions)
- Statistical significance testing (Mann-Kendall, Sen’s slope, etc.)
- Cloud-native pipeline (for larger periods / more variables)

## 📬 Feedback & Contribution

Feel free to open issues, fork the repo, or submit pull requests — especially if you:

- spot errors in methodology / calculations
- want to add statistical tests or uncertainty quantification
- have ideas for better visualizations
- want to extend to other variables (temperature, precipitation, SWE, etc.)

All contributions are welcome — this project is intentionally kept simple and educational.

Happy exploring! ❄️🏔️





## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

You are free to use, modify, and share this work (even commercially), as long as you include the original copyright notice.