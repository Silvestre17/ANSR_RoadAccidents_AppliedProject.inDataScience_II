# 🚗 ANSR Road Safety Analysis: Clustering & Time Series Forecasting 📈

<p align="center">
   <a href="http://www.ansr.pt/Pages/default.aspx">
       <img src="./img/logo-ANSR.svg" alt="ANSR" width="300">
    </a>
</p>

<p align="center">
    <!-- Project Links -->
    <a href="https://github.com/Silvestre17/ANSR_RoadSafetyAnalysis_AppliedProject.inDataScience_II"><img src="https://img.shields.io/badge/Project_Repo-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Repo"></a>
</p>

## 📝 Description

This project provides a deep-dive analysis into road safety in Portugal, using a comprehensive dataset of traffic accidents from 2010 to 2019 provided by the **ANSR (Autoridade Nacional de Segurança Rodoviária)**. The study is twofold: first, it uses geospatial clustering to identify strategic locations for speed camera installation in Lisbon; second, it employs time series forecasting to analyze and predict national accident trends, aiming to inform public awareness campaigns.

## ✨ Objectives

The project aims to deliver actionable insights for road safety improvement through two primary objectives:

1.  **Radar Placement Optimization:**
    *   Verify the influence of existing speed cameras on accident reduction in Lisbon.
    *   Use clustering algorithms to recommend strategic locations for new speed cameras.

2.  **Temporal Trend Analysis:**
    *   Analyze monthly accident data to identify critical periods and temporal patterns.
    *   Develop a predictive model to forecast future accident occurrences and support the timing of awareness campaigns.

<p align="center">
    <a href="http://www.ansr.pt/Pages/default.aspx">
        <img src="https://img.shields.io/badge/ANSR-003366?style=for-the-badge&logo=ansr&logoColor=white" alt="ANSR" />
    </a>
</p>

## 🎓 Project Context

This group project was developed for the **Projeto Aplicado para Ciência de Dados II** (*Applied Project in Data Science II*) course, as part of the 3rd year of the **[Licenciatura em Ciência de Dados](https://www.iscte-iul.pt/degree/code/0322/bachelor-degree-in-data-science)** (*Bachelor Degree in Data Science*) at **ISCTE-IUL**, during the 2023/2024 academic year.

## 🗺️ Data Sources

*   **ANSR:** The primary data source, containing detailed records of road accidents in Portugal from 2010 to 2019.
    *   **Note:** The dataset provided by ANSR cannot be shared publicly due to privacy and data protection regulations.
*   **Radares de Portugal:** A supplementary dataset providing geospatial information on existing speed cameras.
    *   **Note:** This dataset is publicly available and can be accessed [here](https://www.radaresdeportugal.com/).

## 🛠️ Technologies & Libraries

The project was implemented in **Python**, leveraging a powerful stack of libraries for data science and visualization.

<p align="center">
    <a href="https://www.python.org/">
        <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
    </a>
    <a href="https://pandas.pydata.org/">
        <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas" />
    </a>
    <a href="https://numpy.org/">
        <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy" />
    </a>
    <a href="https://matplotlib.org/">
        <img src="https://img.shields.io/badge/Matplotlib-65BAEA?style=for-the-badge&logo=matplotlib&logoColor=white" alt="Matplotlib" />
    </a>
    <a href="https://seaborn.pydata.org/">
        <img src="https://img.shields.io/badge/Seaborn-444876?style=for-the-badge&logo=seaborn&logoColor=white" alt="Seaborn" />
    </a>
</p>

**Machine Learning & Time Series:**
<p align="center">
    <a href="https://scikit-learn.org/">
        <img src="https://img.shields.io/badge/Scikit_Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn" />
    </a>
    <a href="https://pypi.org/project/pmdarima/">
        <img src="https://img.shields.io/badge/pmdarima-FFC700?style=for-the-badge&logo=python&logoColor=black" alt="pmdarima" />
    </a>
</p>

**Geospatial & Visualization:**
<p align="center">
    <a href="https://python-visualization.github.io/folium/">
        <img src="https://img.shields.io/badge/Folium-3E8E41?style=for-the-badge&logo=leaflet&logoColor=white" alt="Folium" />
    </a>
    <a href="https://powerbi.microsoft.com/">
        <img src="https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI" />
    </a>
    <a href="https://www.canva.com/">
        <img src="https://img.shields.io/badge/Canva-00C4CC?style=for-the-badge&logo=canva&logoColor=white" alt="Canva" />
    </a>
</p>

---

## ⚙️ Project Workflow (CRISP-DM)

The project was executed following the CRISP-DM methodology, tailored for each of the two main objectives.

### Objective 1: Radar Placement Analysis (Lisbon)
1.  **Data Preparation:** Merged ANSR accident data with radar locations. Cleaned and standardized GPS coordinates, and imputed missing values using **K-Nearest Neighbors (KNN)** to ensure data completeness.

2.  **Exploratory Data Analysis (EDA):** Analyzed the influence of existing radars, confirming a positive correlation with accident reduction. The analysis was focused on high-severity accidents in Lisbon.

3.  **Clustering:** Applied unsupervised learning to identify accident hotspots.
    *   **Algorithms Tested:** K-Means, OPTICS, and **DBSCAN**.
    *   **Selected Algorithm:** **DBSCAN** was chosen for its ability to identify density-based clusters of arbitrary shapes, making it ideal for geospatial data. Key parameters (`eps` = 500m, `min_samples` = 4) were tuned to find meaningful accident clusters.
    *   **Results:** Identified **16 distinct accident clusters**, with the A5 and EN6 highways showing significant concentrations.

4.  **Deployment:** Created interactive maps using **Folium**, allowing for the visualization of accident locations, radar positions, and the identified clusters. **Google Street View** was used to assess the practical viability of recommended installation sites.

### Objective 2: Temporal Trend Analysis (Portugal)
1.  **Data Preparation:** Aggregated accident data by month to create a time series dataset from 2010 to 2019.
2.  **Time Series Analysis:**
    *   **Decomposition:** Analyzed the series to identify trend, seasonality (annual), and residual components.
    *   **Stationarity Tests:** Used **KPSS** and **Augmented Dickey-Fuller** tests to confirm the series was non-stationary.
    *   **ACF/PACF Analysis:** Plotted Autocorrelation and Partial Autocorrelation functions to determine the parameters for the SARIMA model.
3.  **Modeling & Forecasting:**
    *   **SARIMA Model:** Utilized `pmdarima`'s `auto_arima` function to automatically select the optimal **SARIMA(4,0,0)(0,1,1)[12]** model.
    *   **Forecasting:** The model was trained on data from 2010-2017 and tested on 2018-2019 data. It demonstrated acceptable predictive capability and was used to forecast accident counts for 2020.
4.  **Deployment:**
    *   **Awareness Campaign:** Based on the finding that October is a consistently critical month for accidents, a sample awareness campaign, **"Por via das dúvidas, abrande: outubro crítico"**, was designed using **Canva**.
    *   **Interactive Dashboard:** A comprehensive **Power BI Dashboard** was created to allow for dynamic exploration of all datasets and findings.

## 📊 Deployment & Key Visualizations

The project resulted in several deployed artifacts for analysis and communication.

### **Power BI Dashboard** 

An interactive dashboard for exploring accident data by location, time, and severity.
<p align="center">
  <img src="./img/PowerBI_Dashboard1.png" alt="Power BI Dashboard Showcase" width="800">
  <img src="./img/PowerBI_Dashboard2.png" alt="Power BI Dashboard Showcase" width="800">
  <img src="./img/PowerBI_Dashboard3.png" alt="Power BI Dashboard Showcase" width="800">
</p>

### **Folium Map of Accident Clusters**

An interactive map visualizing accident hotspots in Lisbon, with radar locations and cluster boundaries.

<p align="center">
  <img src="./img/FoliumMapHTML.png" alt="Folium Map of Accident Clusters" width="800">
</p>

### **October Awareness Campaign Concept**

A sample campaign proposal designed to raise awareness about road safety during critical months, particularly October.

<p align="center">
  <img src="./Propostas_CampanhaANSR_outubro/CampanhaANSR_outubro_Proposta1.png" alt="Canva Campaign Proposal" width="700">
    <img src="./Propostas_CampanhaANSR_outubro/CampanhaANSR_outubro_Proposta2.png" alt="Canva Campaign Proposal" width="700">
    <img src="./Propostas_CampanhaANSR_outubro/CampanhaANSR_outubro_Proposta3.png" alt="Canva Campaign Proposal" width="700">
</p>

<br>

## 👥 Team Members (Group 5)

*   **André Silvestre** (Nº104532)
*   **Eliane Gabriel** (Nº103303)
*   **Maria João Lourenço** (Nº104716)
*   **Maria Margarida Pereira** (N°105877)
*   **Umeima Adam Mahomed** (Nº99239)

## 🇵🇹 Note

This project was developed using Portuguese from Portugal 🇵🇹.