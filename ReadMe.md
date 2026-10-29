# North Atlantic–European Weather Regimes & Swiss Climate Extremes

A compact exploratory data analysis pipeline investigating how large-scale synoptic weather patterns (North Atlantic–European weather regimes) modulate localized temperature and precipitation extremes in Zürich, Switzerland.

This project serves as a technical bridge from experimental physics (`xarray`, automated data pipelines, multidimensional signal processing) to mid-latitude atmospheric dynamics and climate research.

---

## Overview & Methodology

The atmosphere over the North Atlantic and Europe frequently organizes into **7 distinct quasi-stationary weather regimes** (categorized into cyclonic and blocked states following the classification by *Grams et al., 2017*). 

This notebook pairs two open datasets to quantify how specific regimes amplify or suppress extreme weather in Switzerland:
1. **Large-Scale Dynamics:** Dr. Christian Grams' official ERA5 weather regime lifecycle attribution catalogue (Zenodo).
2. **Local Observations:** MeteoSwiss operational climate station data for Zürich / Fluntern (`SMA`), retrieved via the Federal Open Government Data (OGD) portal.

### Core Calculations:
* **Seasonal Anomalies:** Computes daily maximum temperature anomalies (`t2m_max_anom`) relative to the WMO 1991–2020 standard climatological baseline using `xarray`.
* **Conditional Risk Ratios:** Evaluates the probability of exceeding the **95th percentile** (extreme heat/precipitation) or falling below the **5th percentile** (extreme cold) *conditional* on the active weather regime, compared against the unconditional baseline probability (5%).

---

## Key Physical Findings

Running the pipeline reveals distinct physical drivers across seasons:
* **Winter Warm Spells:** Atlantic Trough (`AT`) and Zonal (`ZO`) regimes pump mild, moist maritime air into Switzerland, driving winter maximum temperature anomalies up to **$+3.4\text{ °C}$** and increasing extreme warm/wet event risk.
* **Winter Cold Pools & Inversions:** European (`EuBL`) and Scandinavian (`ScBL`) Blocking shut off westerly flow, driving cold continental *Bise* winds and trapping Zürich under cold-air pools (**up to $2.3\times$ baseline cold-extreme risk**).
* **The Summer Blocking Flip:** While blocking patterns bring cold stagnation in winter, **Scandinavian Blocking (`ScBL`)** flips sign in summer, significantly elevating the risk of heatwave extremes (**~$1.8\times$ baseline risk**).

---

## Tech Stack & Requirements

* **Python 3.x**
* **Core Libraries:** `xarray`, `pandas`, `numpy`, `requests`, `matplotlib`
* **Data Sources:** 
  * ERA5 Weather Regime Catalogue (`wr_data_package_V1.0`)
  * MeteoSwiss Open Government Data (`ogd-smn` daily time series for Zürich/Fluntern)

---
