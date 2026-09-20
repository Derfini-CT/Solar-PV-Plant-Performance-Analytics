\# ☀️ Solar PV Plant Performance \& Efficiency Analytics



\## 1. Project Overview



This project presents an interactive Power BI dashboard for analyzing the performance, energy generation, weather conditions, and operational characteristics of solar photovoltaic (PV) plants.



The analysis uses the BR-PVGen dataset, which contains photovoltaic generation, inverter, meteorological, and plant metadata from solar PV plants in Brazil.



Power BI was used to transform the raw data into an interactive analytical dashboard containing multiple pages, KPIs, charts, maps, and advanced analytical visuals.



The project focuses on understanding solar energy generation patterns, comparing plant performance, analyzing environmental conditions, and identifying factors associated with energy generation.







\---



\## 2. Problem Statement



Solar PV plants generate large amounts of operational and environmental data from inverters, sensors, and monitoring systems.



Analyzing this data manually can make it difficult to:



\- Monitor energy generation trends

\- Compare the performance of different solar plants

\- Understand the relationship between irradiance and power generation

\- Analyze the effect of temperature and weather conditions

\- Compare installed capacity with actual generation

\- Identify important factors influencing plant performance



Therefore, this project uses Power BI to convert raw solar PV data into an interactive dashboard that supports performance analysis and data-driven insights.





\---



\## 3. Project Objectives



The main objectives of this project are:



\- Analyze solar PV energy generation across different plants.

\- Monitor AC power and energy generation trends.

\- Compare the performance of individual solar PV plants.

\- Analyze solar irradiance and weather conditions.

\- Study the relationship between irradiance and energy generation.

\- Compare installed capacity with actual energy generation.

\- Analyze the effect of panel and ambient temperature.

\- Evaluate peak capacity utilization.

\- Identify factors associated with energy generation.

\- Present the results through an interactive Power BI dashboard.





\---



\## 4. Tools \& Technologies



\### Data Analysis and Visualization



\- Microsoft Power BI

\- Power Query

\- DAX

\- Microsoft Excel



\### Data Processing



\- Python

\- Pandas



\### Development and Documentation



\- Git

\- GitHub

\- Markdown



\### Dataset



\- BR-PVGen Brazilian Photovoltaic Power Generation Dataset

\- Zenodo





\---



\## 5. Dataset Details



\### Dataset Name



BR-PVGen — Brazilian Photovoltaic Power Generation Dataset



\### Source



Zenodo:



https://zenodo.org/records/21511487



\### Dataset Coverage



| Attribute | Details |

|---|---|

| Data period | March 26, 2024 – June 9, 2025 |

| Sampling interval | 15 minutes |

| Number of PV plants | 51 |

| Location | Brazil |

| Main data types | Inverter, meteorological, and plant metadata |



\### Inverter Data



The inverter dataset contains electrical measurements including:



\- Datetime

\- Inverter ID

\- Plant ID

\- Total active power

\- Total DC power

\- Total reactive power



\### Meteorological Data



The meteorological dataset contains environmental measurements including:



\- GHI irradiance

\- GRI irradiance

\- POA irradiance

\- Ambient temperature

\- Panel temperature

\- Precipitation

\- Wind speed

\- Wind direction

\- Tracker albedo index



\### Plant Metadata



Plant-level metadata includes:



\- Brazilian federative unit

\- Plant ID

\- Nominal power

\- Number of panels

\- Panel area

\- Panel bifaciality coefficient

\- Panel efficiency

\- Panel temperature coefficient

\- Structure type





\---



\## 6. Data Preparation \& Cleaning



The raw BR-PVGen data was prepared before importing it into Power BI.



\### Data Preparation Steps



1\. Collected the inverter and meteorological CSV files.

2\. Combined the corresponding CSV files into consolidated datasets.

3\. Removed unnecessary or duplicate records where applicable.

4\. Standardized column names for easier analysis.

5\. Converted datetime columns into a consistent Date/Time format.

6\. Verified numerical columns such as power, irradiance, temperature, and capacity.

7\. Checked for missing and invalid values.

8\. Created a separate plant metadata table.

9\. Created a Date/Time dimension for time-based analysis.

10\. Loaded the cleaned datasets into Power BI.



\### Cleaned Tables



The Power BI model uses the following main tables:



\- `Cleaned\_Inverter\_Data`

\- `Cleaned\_Meteorological\_Data`

\- `Dim\_Plant`

\- `Dim\_DateTime`



The cleaned datasets provide a structured foundation for creating relationships, DAX measures, KPIs, and dashboard visualizations.







\---



\## 7. Data Model \& Relationships



The Power BI data model follows a dimensional structure where plant and datetime tables act as dimensions connected to the operational datasets.



\### Main Tables



\- `Dim\_Plant`

\- `Dim\_DateTime`

\- `Cleaned\_Inverter\_Data`

\- `Cleaned\_Meteorological\_Data`



\### Relationships



The following relationships were created:



```text

Dim\_Plant\[ps\_id]

&#x20;       │

&#x20;       ├──────────────► Cleaned\_Inverter\_Data\[ps\_id]

&#x20;       │

&#x20;       └──────────────► Cleaned\_Meteorological\_Data\[ps\_id]





Dim\_DateTime\[datetime]

&#x20;       │

&#x20;       ├──────────────► Cleaned\_Inverter\_Data\[datetime]

&#x20;       │

&#x20;       └──────────────► Cleaned\_Meteorological\_Data\[datetime]



\---



\## 8. DAX Measures



The project uses DAX measures to calculate important performance indicators and support the Power BI visuals.



\### Total AC Power (kW)



```DAX

Total AC Power (kW) =

DIVIDE(

&#x20;   SUM(Cleaned\_Inverter\_Data\[total\_active\_power\_w]),

&#x20;   1000

)





Energy Generation (MWh) =

DIVIDE(

&#x20;   SUM(Cleaned\_Inverter\_Data\[total\_active\_power\_w]),

&#x20;   1000

) \* 0.25 / 1000





Peak AC Power (MW) =

DIVIDE(

&#x20;   MAXX(

&#x20;       VALUES(Dim\_DateTime\[datetime]),

&#x20;       CALCULATE(

&#x20;           SUM(Cleaned\_Inverter\_Data\[total\_active\_power\_w])

&#x20;       )

&#x20;   ),

&#x20;   1000000

)





Peak Capacity Utilization (%) =

DIVIDE(

&#x20;   \[Peak AC Power (MW)],

&#x20;   SUM(Dim\_Plant\[nominal\_power\_mw])

) \* 100





Best Performing Plant =

VAR PlantTable =

&#x20;   ADDCOLUMNS(

&#x20;       VALUES(Dim\_Plant\[ps\_id]),

&#x20;       "PlantEnergy", \[Energy Generation (MWh)]

&#x20;   )

VAR TopPlant =

&#x20;   TOPN(

&#x20;       1,

&#x20;       PlantTable,

&#x20;       \[PlantEnergy],

&#x20;       DESC

&#x20;   )

RETURN

&#x20;   CONCATENATEX(

&#x20;       TopPlant,

&#x20;       Dim\_Plant\[ps\_id],

&#x20;       ", "

&#x20;   )





\---



\## 9. Power BI Dashboard Pages



The Power BI solution contains five analytical dashboard pages.



\### Page 1 — Solar Plant Overview



This page provides a high-level overview of solar PV plant performance.



Key elements include:



\- Date, state, and solar plant slicers

\- Installed capacity KPI

\- Total AC power KPI

\- Average irradiance KPI

\- Average panel temperature KPI

\- Plant-wise energy generation

\- Energy and power trends

\- Irradiance trend



The page is designed to provide a quick overview of the overall solar plant performance.



\### Page 2 — Solar Energy Generation Analysis



This page focuses on energy production and plant-level generation patterns.



Key elements include:



\- Total energy generation KPI

\- Energy generation trend

\- Monthly energy generation

\- State-wise plant visualization

\- Plant performance comparison



The page helps analyze how energy generation varies across time, states, and individual plants.



\### Page 3 — Solar Resource \& Weather Analysis



This page focuses on environmental conditions affecting solar PV performance.



Key elements include:



\- Irradiance distribution

\- Irradiance versus energy generation analysis

\- State-wise installed capacity

\- Panel versus ambient temperature

\- Wind speed trend



The page helps investigate the relationship between solar resources, weather conditions, and energy generation.



\### Page 4 — Plant Performance \& Efficiency Analysis



This page focuses on comparing plant performance and installed capacity.



Key elements include:



\- Total energy generated

\- Average panel temperature

\- Energy generation by structure type

\- Installed capacity versus energy generation

\- Plant-wise energy generation

\- Installed capacity by structure type

\- Peak capacity utilization



The page provides a detailed view of plant-level performance and capacity utilization.



\### Page 5 — Advanced Solar Plant Insights \& Recommendations



This page provides advanced analytical views for identifying patterns and factors associated with energy generation.



Key elements include:



\- Best performing plant

\- Top 10 performing solar plants

\- Energy generation decomposition tree

\- Key Influencers analysis



The decomposition tree allows energy generation to be explored through dimensions such as state, structure type, and solar plant.



The Key Influencers visual is used to examine how plant characteristics such as nominal capacity, structure type, panel efficiency, number of panels, and bifacial configuration are associated with energy generation.





\---



\## 10. Key Analytical Insights



The dashboard provides several analytical insights into solar PV plant performance.



\### Energy Generation



The dashboard enables comparison of total and plant-wise energy generation across the available dataset period.



\### Plant Performance



Plant-level analysis helps identify differences in energy generation among the 51 PV plants.



\### Solar Irradiance



Irradiance analysis helps examine how solar resource availability varies across time and locations.



\### Temperature Analysis



Panel and ambient temperature trends provide additional environmental context for understanding PV plant operating conditions.



\### Installed Capacity



Comparing installed nominal capacity with energy generation provides a view of how plants with different capacities contribute to overall generation.



\### Capacity Utilization



Peak capacity utilization provides an indication of the relationship between observed peak AC output and installed plant capacity.



\### Advanced Analysis



The decomposition tree and Key Influencers visuals provide additional ways to explore the dimensions and plant characteristics associated with energy generation.



\---



\## 11. Future Improvements



The project can be extended with additional analytical and predictive capabilities.



Possible future improvements include:



\- Solar power generation forecasting using machine learning.

\- Weather-based generation prediction.

\- Real-time solar plant monitoring.

\- Automated data refresh pipelines.

\- Anomaly and fault detection for inverter performance.

\- Performance ratio analysis.

\- Plant-level efficiency benchmarking.

\- Integration with live weather APIs.

\- Automated alerts for abnormal generation conditions.

\- Deployment of the dashboard through Power BI Service.



\---



\## 12. Project Repository



This GitHub repository contains the project documentation, DAX documentation, dataset information, and dashboard screenshots.



The large raw CSV files and Power BI `.pbix` file are excluded from the repository to keep the repository lightweight.



\### Repository Structure



```text

Solar-PV-Plant-Performance-Analytics

│

├── README.md

│

├── Screenshots/

│   ├── Page1\_Overview.png

│   ├── Page2\_Energy\_Generation.png

│   ├── Page3\_Weather\_Analysis.png

│   ├── Page4\_Performance\_Efficiency.png

│   └── Page5\_Advanced\_Insights.png

│

├── DAX/

│   └── Measures.md

│

├── Dataset/

│   └── Dataset\_Source.md

│

└── Documentation/

&#x20;   └── Project\_Documentation.md

