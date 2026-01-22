# manufacturing-powerbi-dashboard
Power BI dashboard for manufacturing KPI analysis (OEE, Availability, Yield) with synthetic production data.


Manufacturing Performance Dashboard – Power BI

Overview
This repository presents an end-to-end manufacturing performance dashboard built in Power BI, focused on analysing key production losses in an automotive electronics environment.

The project demonstrates:
- KPI design based on standard OEE methodology,
- correct handling of non-additive metrics,
- multi-level analysis (factory → line → team / machine),
- realistic synthetic data modelling,
- structured dashboard architecture and interaction logic.

The dashboard is designed to support both operational and strategic decision-making during regular management review meetings.

Dashboard Scope
The report analyses the main types of production losses:
1. Availability losses (long downtime and microstops; planned stops excluded by design)
2. Yield losses (First Pass Yield, based on scrap generation; no rework included)
3. Performance losses are intentionally not analysed due to data model limitations and are documented as a conscious simplification.

Analytical Layers
The dashboard is structured into three analytical levels:
1. Factory level: High-level overview of KPIs and trends, supporting quick orientation and prioritisation.
2. Line level: Root-cause exploration for Availability and Yield, including short-term variability, target comparison, and What-If analysis.
3. Team and Machine level (drill-through): Local benchmarking using contribution/effectiveness KPIs to identify organisational and equipment-related issues.
The analytical flow follows a clear pattern: orientation → narrowing → exploration.

Data Model
Star schema with 6 dimension tables and 4 fact tables.
Base granularity:
- shift level (team-related facts),
- machine level (equipment-related facts).

Higher aggregation levels (line, factory) derived via correct weighted logic.
Time-based KPIs handled as non-additive metrics with explicit aggregation rules.
All data are synthetic, generated in Python with AI assistance, based on realistic process rules and controlled variability.

Synthetic Data Assumptions
The synthetic dataset represents a mini-factory with:
- 3 production lines,
- 5 machines per line,
- single product across all lines,
- 24/7 operation (3 shifts per day).

Realism is introduced through:
- monthly bias per line,
- shock days and bad weeks,
- partial correlations (never deterministic),
- soft correction toward targets (no perfect execution).

The data model intentionally avoids flat or perfectly proportional behaviour.

Key Features
- Standard OEE-based KPI framework (Availability, Performance, Yield, OEE),
- Correct factory-level aggregation using planned production as weight,
- Effectiveness KPIs for local analysis,
- Consistent tooltip logic (MTD, YTD, MoM, targets),
- What-If scenarios to estimate improvement impact,
- Clean, repeatable interaction patterns across pages.

Limitations
- Synthetic data (no real production data),
- Simplified production planning and execution logic,
- No detailed downtime reason hierarchy,
- No labour constraints, material lead times, or learning curves.
All limitations are documented and reflected in dashboard design decisions.

Tools & Technologies
Power BI – data model, DAX measures, dashboard design
Python – synthetic data generation
DAX – KPI logic, non-additive aggregation, time intelligence
Figma – layout and visual design preparation

Live Report
Power BI Report: https://app.powerbi.com/view?r=eyJrIjoiNzNkMTZjMjEtNjY4Yy00Yjk4LTk1ZjEtMjU2ZWUyOGJiZjNjIiwidCI6IjNkZmU5YWI2LTgxYmYtNDkxYy1iNjcwLTAxYzgyNGEwOWUxOSJ9

Author
Aleksandra Laskowska
Data Analyst / Manufacturing Analytics
LinkedIn: www.linkedin.com/laskowskaaleksandra/

Notes
This project is part of a personal portfolio and was created for learning and demonstration purposes.
It does not represent any real factory or confidential production data.
