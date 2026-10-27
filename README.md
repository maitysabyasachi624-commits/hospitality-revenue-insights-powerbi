\# 🏨 Hospitality Revenue \& Performance Insights (Power BI)



\## 📌 Project Overview

This project presents an interactive Hospitality Analytics Dashboard built in \*\*Power BI\*\* to analyze hotel performance across key business dimensions: \*\*Revenue, Occupancy %, Average Daily Rate (ADR), RevPAR, Realisation %, and Cancellation Loss\*\*.



The dashboard enables management to monitor key performance indicators, benchmark properties across cities, identify sources of revenue leakage, and drive data-backed pricing and operational decisions.



\---



\## 📸 Dashboard Preview

!\[Hospitality Dashboard](assets/dashboard\_preview.png)



\---



\## 🎯 Business Objectives

\* \*\*Monitor Performance:\*\* Track top-level KPIs including Revenue, RevPAR, ADR, and Occupancy %.

\* \*\*Analyze Demand Trends:\*\* Uncover occupancy and pricing variations across weekday vs. weekend booking cycles.

\* \*\*Property \& Category Benchmarking:\*\* Compare hotel efficiency across cities (Mumbai, Delhi, Bangalore, Hyderabad) and categories (Luxury vs. Business).

\* \*\*Identify Revenue Leakage:\*\* Diagnose revenue loss stemming from customer cancellations and platform no-shows.

\* \*\*Evaluate Booking Channels:\*\* Assess realization rates across direct hotel websites versus third-party travel platforms (OTAs).



\---



\## 📊 Core Hospitality Metrics \& DAX Calculations



| Metric | DAX Formula / Calculation | Purpose |

| :--- | :--- | :--- |

| \*\*Revenue\*\* | `SUM(fact\_bookings\[revenue\_realized])` | Total realized revenue post-cancellations. |

| \*\*Occupancy %\*\* | `DIVIDE(\[Total Succesful Bookings], \[Total Capacity], 0)` | Ratio of occupied rooms to total available capacity. |

| \*\*ADR (Avg Daily Rate)\*\* | `DIVIDE(\[Revenue], \[Total Bookings], 0)` | Average revenue generated per booked room. |

| \*\*RevPAR\*\* | `DIVIDE(\[Revenue], \[Total Capacity], 0)` | Revenue generated per available room capacity. |

| \*\*Realisation %\*\* | `1 - (\[Cancellation %] + \[No Show rate %])` | % of bookings that successfully checked out. |

| \*\*Cancellation %\*\* | `DIVIDE(\[Total cancelled bookings], \[Total Bookings])` | % of total reservations cancelled by guests. |

| \*\*DSRN\*\* | `DIVIDE(\[Total Capacity], \[No of days])` | Daily Sellable Room Nights available across hotels. |

| \*\*DURN\*\* | `DIVIDE(\[Total Checked Out], \[No of days])` | Daily Utilized Room Nights successfully completed. |



\---



\## 🏗️ Data Architecture \& Star Schema Model

The data model connects 2 Fact tables and 3 Dimension tables in a \*\*Star Schema\*\*:

\* \*\*Fact Tables:\*\*

&#x20; \* `fact\_bookings`: Transaction-level booking status, guest count, booking platform, and revenue.

&#x20; \* `fact\_aggregated\_bookings`: Daily room capacity and successful check-in records per property.

\* \*\*Dimension Tables:\*\*

&#x20; \* `dim\_date`: Calendar dimension defining week numbers and day types (Friday \& Saturday as Weekend).

&#x20; \* `dim\_hotels`: Property details, city location, and hospitality tier (Luxury vs. Business).

&#x20; \* `dim\_rooms`: Room classifications (Standard, Elite, Premium, Presidential).



\---



\## 📂 Repository Structure



```text

├── assets/

│   └── dashboard\_preview.png             # Dashboard screenshot preview

├── data/

│   ├── dim\_date.csv                      # Calendar lookup table

│   ├── dim\_hotels.csv                    # Hotel property details

│   ├── dim\_rooms.csv                     # Room type classifications

│   ├── fact\_aggregated\_bookings.csv      # Daily capacity \& check-in summaries

│   ├── fact\_bookings.csv                 # Transaction-level booking data

│   └── meta\_data\_hospitality.txt         # Dataset column definitions

├── reports\_and\_dashboard/

│   ├── Hospitality\_Revenue\_Insights.pbix # Complete Power BI report \& model

│   └── metrics-list.xlsx                 # DAX formulas \& metrics documentation

└── README.md



