# Electric-car-population

### Objective
Analyze the distribution and adoption of battery electric vehicles (BEVs) and plug-in hybrid electric vehicles (PHEVs) across various cities in the United States.

### Problem Statement
Assess the current status and trends of electric vehicle adoption in different US cities, focusing on BEVs and PHEVs.
Identify factors influencing adoption rates and provide insights for promoting sustainable transportation solutions

### Data Source
- The data use for this analysis is the 'electric_car_dataset' which contain vital information  about the population of battery electric vehicle  and plug hybrid  electric vehicle


### Tools used 
- Mysql - Data Analysis
- Power Bi - Creating Report

### Data analysis
- MySQL is employed for exploratory data analysis to extract essential insights and determine the adoption rates of both electric vehicles and plug-in hybrid electric vehicles.
- The electric car dataset is in CSV format and imported into MySQL. Each column is carefully examined to ensure data accuracy, including verifying the correct data types and checking for 
 missing values. Additionally, the column names are reviewed for accuracy and consistency
- MySQL is utilized to query the database and address key questions derived from the dataset.use project;
select * from electric_vehicle ;

 - Total number of car in the dateset
```mysql
SELECT  DISTINCT(count(car_id)) FROM  electric_vehicle ;
```

- The average electric range of the cars
``` mysql
SELECT  count(*), avg(electric_range)FROM  electric_vehicle;
```

- Total bev vehicle and the %total bev(battery electric vehicle )
``` mysql
SELECT  count(*), sum(Census_Tract), (Electric_Vehicle_Type) FROM  electric_vehicle 
WHERE Electric_Vehicle_Type  LIKE  "%Battery Electric Vehicle (BEV)%"
GROUP BY  Electric_Vehicle_Type;
```
 
- Percentage of bev( battery electic vehicle )
``` mysql
SELECT   sum(Census_Tract) /( SELECT  sum(Census_Tract) FROM  electric_vehicle)* 100  AS  result  FROM  electric_vehicle 
WHERE  electric_vehicle_type LIKE   "%Battery Electric Vehicle (BEV)%";
```

- Total PHEV  Plug-in Hybrid Electric Vehicle (PHEV)
```mysql
SELECT count(*),sum(Census_Tract), (Electric_Vehicle_Type) FROM  electric_vehicle 
WHERE Electric_Vehicle_Type  NOT  LIKE "%Battery Electric Vehicle (BEV)%"
GROUP BY Electric_Vehicle_Type;
```

- Percentage of  Plug-in Hybrid Electric Vehicle (PHEV)
``` mysql
SELECT  sum(Census_Tract) /( select sum(Census_Tract) FROM   electric_vehicle)*100  AS result  FROM  electric_vehicle 
WHERE electric_vehicle_type  NOT LIKE   "%Battery Electric Vehicle (BEV)%";
```

- TOTAL  VEHICLE BY MODEL YEAR 2010
```mysql
SELECT count(*),sum(Census_Tract) FROM ELECTRIC_VEHICLE 
WHERE  MODELYEAR >= 2010;
```

- TOP VEHICLE BY MAKE
``` mysql
SELECT  COUNT(*), MAKE  FROM ELECTRIC_VEHICLE
GROUP BY MAKE 
ORDER BY COUNT(*) DESC;
```

- TOP VEHICLE BY MODEL AND MAKE
``` mysql
SELECT  COUNT(*), MODEL , MAKE  FROM ELECTRIC_VEHICLE 
GROUP BY MODEL, MAKE  
ORDER BY  COUNT(*) DESC;
```

- TOP 5 VEHICLE BY MAKE  AND STATE
```mysql
SELECT COUNT(*) , MAKE , STATE  FROM ELECTRIC_VEHICLE 
GROUP BY MAKE, STATE
ORDER BY COUNT(*) DESC  LIMIT 5;
```

- BOTTOM  5 VEHICLE BY STATE AND MAKE
```mysql
SELECT COUNT(*) , MAKE , STATE  FROM ELECTRIC_VEHICLE 
GROUP BY MAKE, STATE
ORDER BY COUNT(*) ASC  LIMIT 5;
```


- YEAR WITH THE HIGEST population  OF VEHICLE
``` mysql
SELECT  COUNT(*), MODELYEAR FROM ELECTRIC_VEHICLE 
GROUP BY MODELYEAR
ORDER BY COUNT(*) DESC;
```

- YEAR WITH THE HIGEST population OF BEV VEHICLE
```mysql
SELECT COUNT(*), MODELYEAR FROM ELECTRIC_VEHICLE
WHERE  ELECTRIC_VEHICLE_TYPE LIKE "%(BEV)%"
GROUP BY MODELYEAR
ORDER BY COUNT(*) DESC;
```

- YEAR WITH THE HIGEST population  OF PHEV  VEHICLE
```mysql
SELECT COUNT(*),sum(Census_Tract), MODELYEAR FROM ELECTRIC_VEHICLE
WHERE  ELECTRIC_VEHICLE_TYPE   LIKE "%(PHEV)%"
GROUP BY MODELYEAR
ORDER BY COUNT(*) DESC;
```

- CAR WITH THE HIGEST ELECTRIC RANGE
```mysql
SELECT   MAKE,  SUM(ELECTRIC_RANGE) FROM ELECTRIC_VEHICLE
WHERE  ELECTRIC_VEHICLE_TYPE LIKE "%(BEV)%"
GROUP BY MAKE ;
```

- CITY WITH THE HIGEST NUMBER OF population  OF BEV   CAR
```mysql
 SELECT  COUNT(*), CITY, MAKE   FROM ELECTRIC_VEHICLE
 WHERE  ELECTRIC_VEHICLE_TYPE LIKE "%(BEV)%"
 GROUP BY CITY, MAKE 
 ORDER BY COUNT(*) DESC ;
```
 
 - CITY WITH THE HIGEST NUMBER populaytion OF PHEV   CAR
``` mysql
 SELECT  COUNT(*), CITY, MAKE   FROM ELECTRIC_VEHICLE
 WHERE  ELECTRIC_VEHICLE_TYPE LIKE "%(PHEV)%"
 GROUP BY CITY, MAKE 
 ORDER BY COUNT(*) DESC;
```


### Power Bi
- Load data into Power BI Desktop, dataset is a csv file.
- Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- It was observed that in none of the columns errors & empty values were presented
- in the report view a canvans backgroud is imported into the report view.
 - Data modeling 
- calculating some key important metric or quick measure 
- creating  visual card for  total bev and total phbev
- create quick measure for bev percentage  and phbev percentage
- creating  graph such as pie chart, line chart to show the trend  and bar chart 
- Data modeling with  sales data table
- calculation of key matric with virtuel card

 











