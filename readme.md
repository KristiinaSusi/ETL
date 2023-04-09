### Data

###### Metadata about air quality:

[Eesti välisõhu kvaliteet](http://airviro.klab.ee/)

| Attr  | example value | unit    | Description                 |
| ----- | ------------- | ------- | --------------------------- |
| SO2   | 0,23          | µg/m³ | Vääveldioksiid            |
| NO2   | 0,02          | µg/m³ | Lämmastikdioksiid          |
| CO    | 0,24          | mg/m³  | Süsinikoksiid              |
| O3    | 70,05         | µg/m³ | Osoon                       |
| PM10  | 8,55          | µg/m³ | Peened osakesed             |
| PM2.5 | 4,72          | µg/m³ | Eriti peened osakesed       |
| TEMP  | 9,72          | C       | Temperatuur                 |
| WD10  | 204,40        | deg     | Tuule suund 10 m kõrgusel  |
| WS10  | 1,56          | m/s     | Tuule kiirus 10 m kõrgusel |


* Using python script extact data from [http://airviro.klab.ee/]() (`fetch_air.ipynb`).
* Using Openrefine transform columns into correct format (use `data_tranform_steps_air.json`)
* Using Openrefine I exported the data to csv and added the averages using Python (the first way described in add_columns_air_data.ipynb), since OpenRefine provides me with a SQL create a table statement I will once again upload it to OpenRefine to get that and then create a database table.
(CREATE TABLE air2022 (
DateTime TIMESTAMP NULL,
SO2 NUMERIC NULL,
SO2_average NUMERIC NULL,
Hourly_average_SO2 NUMERIC NULL,
Daily_average_SO2 NUMERIC NULL,
Monthly_average_SO2 NUMERIC NULL,
NO2 NUMERIC NULL,
NO2_average NUMERIC NULL,
Hourly_average_NO2 NUMERIC NULL,
Daily_average_NO2 NUMERIC NULL,
Monthly_average_NO2 NUMERIC NULL,
CO NUMERIC NULL,
CO_average NUMERIC NULL,
Hourly_average_CO NUMERIC NULL,
Daily_average_CO NUMERIC NULL,
Monthly_average_CO NUMERIC NULL,
O3 NUMERIC NULL,
O3_average NUMERIC NULL,
Hourly_average_O3 NUMERIC NULL,
Daily_average_O3 NUMERIC NULL,
Monthly_average_O3 NUMERIC NULL,
PM10 NUMERIC NULL,
PM10_average NUMERIC NULL,
Hourly_average_PM10 NUMERIC NULL,
Daily_average_PM10 NUMERIC NULL,
Monthly_average_PM10 NUMERIC NULL,
PM2_5 NUMERIC NULL,
PM2_5_average NUMERIC NULL,
Hourly_average_PM2_5 NUMERIC NULL,
Daily_average_PM2_5 NUMERIC NULL,
Monthly_average_PM2_5 NUMERIC NULL,
TEMP NUMERIC NULL,
TEMP_average NUMERIC NULL,
Hourly_average_TEMP NUMERIC NULL,
Daily_average_TEMP NUMERIC NULL,
Monthly_average_TEMP NUMERIC NULL,
WD10 NUMERIC NULL,
WD10_average NUMERIC NULL,
Hourly_average_WD10 NUMERIC NULL,
Daily_average_WD10 NUMERIC NULL,
Monthly_average_WD10 NUMERIC NULL,
WS10 NUMERIC NULL,
WS10_average NUMERIC NULL,
Hourly_average_WS10 NUMERIC NULL,
Daily_average_WS10 NUMERIC NULL,
Monthly_average_WS10 NUMERIC NULL
);))
* Use Openrefine export to SQL.
* I used SAP SQL Anywhere, used the create table statement provided in the exported file 
(CREATE TABLE air_2022_csv_sql (
DateTime TIMESTAMP NULL,
SO2 NUMERIC NULL,
NO2 NUMERIC NULL,
CO NUMERIC NULL,
O3 NUMERIC NULL,
PM10 NUMERIC NULL,
PM2_5 NUMERIC NULL,
TEMP NUMERIC NULL,
WD10 NUMERIC NULL,
WS10 NUMERIC NULL
);) 
and imported the data.

###### Metadata about electricity:

Downloaded from [http://energia.ee](), need to log in and can only be accessed by the contract owner.

| Attr  | example value | unit    | Description                 |
| ----- | ------------- | ------- | --------------------------- |
| Elec  | 2,42          |  kWh    | tunnis kulunud elekter      |
| Price | 70,03         | €/MWh   | Börsi hetke hind            |

* Downloaded file to be fixed with Openrefine (use `data_transform_steps_el.json`)
* Use Openrefine export to SQL.