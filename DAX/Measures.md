\# 📐 DAX Measures



This document contains the main DAX measures used in the Solar PV Plant Performance \& Efficiency Analytics project.



\---



\## 1. Total AC Power (kW)



Calculates total active AC power and converts the value from watts to kilowatts.



```DAX

Total AC Power (kW) =

DIVIDE(

&#x20;   SUM(Cleaned\_Inverter\_Data\[total\_active\_power\_w]),

&#x20;   1000

)





\## 2. Energy Generation (MWh)



Calculates energy generation from 15-minute active-power measurements.



Energy Generation (MWh) =

DIVIDE(

&#x20;   SUM(Cleaned\_Inverter\_Data\[total\_active\_power\_w]),

&#x20;   1000

) \* 0.25 / 1000



\## 3. Peak AC Power (MW)



Calculates the maximum aggregated AC power observed across the available datetime values.



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

\## 4. Peak Capacity Utilization (%)



Calculates peak AC power relative to the total installed nominal capacity.

Peak Capacity Utilization (%) =

DIVIDE(

&#x20;   \[Peak AC Power (MW)],

&#x20;   SUM(Dim\_Plant\[nominal\_power\_mw])

) \* 100



\## 5. Best Performing Plant



Identifies the solar plant with the highest energy generation within the current filter context.



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







