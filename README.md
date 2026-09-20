# ☀️ Solar PV Plant Performance & Efficiency Analytics

### 📊 Power BI | Solar Energy | Data Analytics

An interactive Power BI analytics platform designed to analyze solar photovoltaic (PV) plant performance, energy generation, weather conditions, and operational efficiency.

The project transforms plant-level solar, inverter, and meteorological data into interactive dashboards that help explore energy generation patterns, plant performance, environmental conditions, and key factors influencing solar energy output.

---

## 🚀 Project Highlights

- 📈 Solar energy generation and performance analysis
- ☀️ Solar irradiance and weather analysis
- 🌡️ Panel and ambient temperature monitoring
- 🏭 Plant-wise performance comparison
- ⚡ Installed capacity and energy generation analysis
- 🔍 Key factors influencing energy generation
- 📊 Interactive Power BI dashboards
- 🧮 DAX-based analytical measures
\# ☀️ Solar PV Plant Performance \& Efficiency Analytics Using Power BI



\## 📌 Project Overview



This project focuses on analyzing the performance and efficiency of solar photovoltaic (PV) plants using Power BI.



The dashboard combines solar power generation, irradiance, temperature, wind and plant metadata to identify performance variations, compare solar plants and understand the factors affecting energy generation.



\---



\## 🎯 Problem Statement



To analyze and evaluate the performance of solar PV plants using power generation, irradiance, temperature and environmental data in order to identify performance variations, determine factors affecting energy efficiency and provide actionable insights.



\---



\## 🎯 Objectives



\- Analyze solar energy generation across photovoltaic plants

\- Compare plant-wise and state-wise performance

\- Study the relationship between irradiance and energy generation

\- Analyze panel and ambient temperature variations

\- Compare fixed and tracker-based structures

\- Evaluate capacity utilization

\- Identify factors influencing solar energy generation

\- Provide data-driven insights for solar plant performance analysis



\---



\## 🛠️ Tools \& Technologies



\- \*\*Power BI\*\*

\- \*\*DAX\*\*

\- \*\*Python\*\*

\- \*\*Pandas\*\*

\- \*\*Microsoft Excel\*\*

\- \*\*Data Modeling\*\*

\- \*\*Data Visualization\*\*



\---



\## 📂 Dataset



The project uses the \*\*BR-PVGen\*\* photovoltaic generation dataset.



\### Dataset Details



\- \*\*Data period:\*\* March 2024 – June 2025

\- \*\*Time resolution:\*\* 15 minutes

\- \*\*Number of PV plants:\*\* 51

\- \*\*Generation data:\*\* AC power, DC power and reactive power

\- \*\*Meteorological data:\*\* GHI, GRI, POA irradiance, temperature, wind and precipitation

\- \*\*Plant metadata:\*\* installed capacity, number of panels, panel efficiency, structure type and bifacial information



\### Dataset Source



BR-PVGen photovoltaic generation dataset:



https://zenodo.org/records/21511487



\---



\## 🧹 Data Preparation



The raw dataset was processed before visualization.



\### Data Cleaning



\- Combined multiple inverter data files

\- Combined meteorological data files

\- Converted datetime fields into a consistent format

\- Converted numerical fields into appropriate data types

\- Handled missing and invalid records

\- Removed invalid negative power values

\- Prepared plant metadata for analysis



\### Tools Used for Preparation



Python and Pandas were used for data preprocessing and cleaning.



\---



\## 🗂️ Data Model



A star-schema-based Power BI data model was developed.



\### Main Tables



\- `Dim\_Plant`

\- `Dim\_DateTime`

\- `Cleaned\_Inverter\_Data`

\- `Cleaned\_Meteorological\_Data`



The dimension tables are used to filter and analyze the inverter and meteorological data.



\---



\## 📊 Dashboard Pages



The Power BI report contains five analytical pages.



\### 1️⃣ Solar Plant Overview



Provides an overall view of solar plant performance using:



\- KPI cards

\- Plant-wise energy generation

\- Energy and power trends

\- Irradiance trends

\- Plant and date filters



\### 2️⃣ Solar Energy Generation Analysis



Focuses on energy generation patterns using:



\- Total energy generation

\- Energy generation trend

\- Monthly generation analysis

\- State-wise generation

\- Plant performance comparison

\- Azure Maps visualization



\### 3️⃣ Solar Resource \& Weather Analysis



Analyzes environmental conditions affecting solar generation:



\- Irradiance distribution

\- Irradiance vs energy generation

\- State-wise installed capacity

\- Panel vs ambient temperature

\- Wind speed trend



\### 4️⃣ Plant Performance \& Efficiency Analysis



Evaluates plant performance using:



\- Total energy generated

\- Average panel temperature

\- Energy generation by structure type

\- Installed capacity vs energy generation

\- Plant-wise generation

\- Installed capacity by structure type

\- Peak capacity utilization



\### 5️⃣ Advanced Solar Plant Insights \& Recommendations



Provides advanced analytical insights using:



\- Best performing plant

\- Top 10 performing plants

\- Energy generation decomposition

\- Key influencers

\- Plant performance analysis

\- Factors influencing energy generation



\---



\## 📸 Dashboard Preview



\### Page 1 — Solar Plant Overview



!\[Page 1](Screenshots/Page1\_Overview.png)



\### Page 2 — Solar Energy Generation Analysis



!\[Page 2](Screenshots/Page2\_Energy\_Generation.png)



\### Page 3 — Solar Resource \& Weather Analysis



!\[Page 3](Screenshots/Page3\_Weather\_Analysis.png)



\### Page 4 — Plant Performance \& Efficiency Analysis



!\[Page 4](Screenshots/Page4\_Performance\_Efficiency.png)



\### Page 5 — Advanced Solar Plant Insights \& Recommendations



!\[Page 5](Screenshots/Page5\_Advanced\_Insights.png)



\---



\## 📐 Key DAX Measures



Important DAX measures used in the project include:



\- Total AC Power (kW)

\- Energy Generation (MWh)

\- Peak AC Power (MW)

\- Peak Capacity Utilization (%)

\- Best Performing Plant



These measures support KPI calculations, plant comparisons and advanced analysis.



\---



\## 🔍 Key Analytical Insights



The dashboard enables analysis of:



\- Differences in energy generation between solar plants

\- State-wise generation patterns

\- Relationship between solar irradiance and energy generation

\- Temperature variations across the dataset

\- Performance differences between fixed and tracker structures

\- Installed capacity and energy generation relationships

\- Plant capacity utilization

\- Factors associated with higher energy generation



\---



\## 🚀 Future Improvements



Potential future enhancements include:



\- Real-time solar plant monitoring

\- Automated Power BI data refresh

\- Predictive energy generation models

\- Machine learning-based performance prediction

\- Solar plant anomaly detection

\- Weather-based generation forecasting

\- Automated performance alerts



\---



\## 👩‍💻 Author



\*\*Derfini C T\*\*



Electronics \& Communication Engineering



\### Project Focus



\*\*Power BI | Data Analytics | DAX | Python | Solar Energy Analytics\*\*



\---



\## 📜 License



This project is created for educational and portfolio purposes.



The underlying BR-PVGen dataset is provided under its respective dataset license.

