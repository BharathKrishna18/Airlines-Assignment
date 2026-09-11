# ASG Airlines – End-to-End Data Engineering Case Study

## 1. Project Overview

This project implements an end-to-end data engineering pipeline for airline flight data.

The pipeline includes:
- Data ingestion
- Data quality checks
- Data cleaning and transformation
- Flight duration calculation
- Overnight flight identification
- Anomaly detection
- MySQL data storage
- SQL-based KPI analysis
- Power BI dashboard

## 2. Dataset

The input dataset is:

`UseCase - Airlines.xlsx`

Main fields:
- flight_id
- airline
- source
- destination
- departure_time
- arrival_time

## 3. Data Processing

Python and Pandas were used for data processing.

The cleaning process includes:
- Standardizing column names
- Removing duplicate records
- Trimming text fields
- Converting date/time fields
- Handling missing essential values
- Handling overnight flights
- Calculating flight duration
- Creating anomaly flags

## 4. Flight Duration and Overnight Handling

Flight duration was calculated using the departure and arrival timestamps.

When the arrival time was earlier than the departure time, the arrival was treated as occurring on the following day.

The following fields were created:
- duration
- duration_minutes
- overnight_flight
- anomaly_flag

## 5. Data Storage

The cleaned dataset was stored in MySQL.

Database:

`airlines_db`

Table:

`airlines_cleaned`

Final retained records:

**966**

## 6. KPI Analysis

The following KPIs were calculated:

| KPI | Result |
|---|---:|
| Total Flights | 966 |
| Average Duration | 164.42 minutes |
| Overnight Flights | 118 |
| Anomalies | 0 |
| Shortest Flight | 30 minutes |
| Longest Flight | 300 minutes |

SQL queries used for KPI analysis are available in:

`sql/kpi_queries.sql`

## 7. Power BI Dashboard

The Power BI dashboard contains the following pages:

### Overview
- Total flights
- Average duration
- Overnight flights
- Anomalies
- Flight distribution by airline
- Top 10 routes

### Duration Analysis
- Average flight duration by airline
- Flight duration distribution
- Longest flight duration
- Shortest flight duration

### Route Analysis
- Top 10 routes by flight count
- Average flight duration by route
- Flight count by source airport
- Airline filter
- Source airport filter

### Airline Trends
- Flight count by airline
- Average flight duration by airline
- Overnight flight percentage by airline

### Delay & Anomaly
- Total anomalies
- Flight-level details

## 8. Tools and Technologies

- Python
- Pandas
- MySQL
- SQL
- Power BI
- Microsoft Excel

## 9. Project Structure

```text
Python Assignment/
│
├── data/
│   ├── raw/
│   │   └── UseCase - Airlines.xlsx
│   └── processed/
│       └── airlines_cleaned.csv
│
├── sql/
│   └── kpi_queries.sql
│
├── cleaning.py
├── ASG_Airlines_Dashboard.pbix
└── README.md

10. Assumptions
Arrival times earlier than departure times were treated as next-day arrivals.
Flight duration was calculated from the available departure and arrival timestamps.
Records missing essential flight information were removed.
Anomaly checks were applied after the transformation process.
11. Limitations

The supplied dataset does not contain a dedicated delay field. Therefore, detailed delay analysis could not be performed.

The anomaly analysis is based on the defined data-quality and duration checks.