# 👨‍🎓 Volunteer-Led Digital Skills for Sustainable Production - SDG 8 and 12

<img width="1344" height="768" alt="VDT SUSTAINABLE PRODUCTION" src="https://github.com/user-attachments/assets/06f17a80-3330-497d-88ce-4f449fc6ec1f" />

This project is a complete data-driven platform designed to mobilize, manage, and measure the impact of a large-scale Volunteer Digital Trainer (VDT) workforce.
## Project Overview

This project is a complete data-driven platform designed to mobilize, manage, and measure the impact of a large-scale Volunteer Digital Trainer (VDT) workforce. The system's purpose is to deploy these volunteers to train Micro, Small, and Medium Enterprises (MSMEs) in sustainable production practices and digital literacy.
The platform functions as the central nervous system for the initiative, capturing field data via a simple API and aggregating it into high-level, verifiable KPIs for project managers, investors, and bodies like the UN. It is a direct implementation of the UN 2026 Thematic Review on Volunteerism (IVY 2026) and Sustainable Production (SDG 12).

## Problem Solved (SDG 12: Responsible Consumption and Production)

The Challenge: MSMEs are the backbone of Nigeria's economy but are often excluded from the sustainable and digital transition. They lack the training and tools to track waste, optimize resources, or prove their supply chain ethics. This leads to high inefficiency, environmental impact, and an inability to compete in a global market that demands sustainability.
The Solution: This platform provides a scalable, cost-effective solution. It mobilizes a volunteer workforce (SDG 17) and equips them with a simple data submission tool. This transforms anecdotal field reports into structured, verifiable data, allowing us to measure the exact impact of digital skills training on waste reduction and economic efficiency at a national scale.

## Architectural Highlights & Main Function Points

This project is architected as a Data-Driven Feedback Loop:
Data Ingestion (The Field): A simple, secure POST endpoint (/api/volunteer_report) allows hundreds of VDTs to submit standardized reports from their mobile devices, detailing an MSME's progress.
Data Persistence (The Core): A SQLAlchemy ORM and SQLite (or PostgreSQL in production) database logs every submission with a timestamp. The database schema is Metrics-First, designed specifically to capture the project's core KPIs.
Data Aggregation (The Engine): The Pandas library is used on the backend to query the entire database and perform complex aggregations in real-time, calculating the project-wide averages for all metrics.
Data Reporting (The Dashboard): A GET endpoint (/api/kpi_dashboard) serves the aggregated, verifiable metrics as a clean JSON object, ready to be consumed by a web dashboard or UN report.

## Key Impact & Verifiable Metrics
This platform moves beyond anecdotal success to provide live, measurable KPIs on the project's impact. Based on data aggregated by the system, the project is tracking the following metrics against its targets:
| KPI (Verifiable Metric) | Project Target | Current Aggregated Result | Strategic Alignment |
| :--- | :--- | :--- | :--- |
| **Average Cost Reduction** | 15% |12.74% | SDG 8 (Economic Growth) |
| **Average Waste Decrease** | 10% | 10.50% | SDG 12 (Sustainable Production) | 
| **Digital Tool Adoption Rate** | 60% | 75.00% | SDG 9 (Innovation/Infrastructure) | 
| **Total MSMEs Engaged** | 500 (Pilot) | 4 | Project Scaling | 
| **Total Volunteers Active** | 200 (Pilot) | 3 | Project Scaling | 

## Deployment / API Usage (Execution Instructions)
The system is a standard Flask web server and can be deployed on any modern cloud platform.
| Environment | Requirement | Command |
| :--- | :--- | :--- |
| **Setup** | Install dependencies | `pip install Flask SQLAlchemy pandas` | 
| **Run** | Execute the application | `python app.py` | 
The app.py script will automatically initialize a new vdt_reports.db file with dummy data for immediate testing.

## API Endpoint 1: Submit a Report (VDT)
## POST request to submit a new report from a volunteer
curl -X POST [http://127.0.0.1:5000/api/volunteer_report](http://127.0.0.1:5000/api/volunteer_report) \
-H "Content-Type: application/json" \
-d '{
    "volunteer_id": "VDT-010",
    "msme_name": "Kano Weavers Hub",
    "cost_reduction": 14.2,
    "waste_decrease": 8.5,
    "digital_score": 1
}'


## API Endpoint 2: View KPI Dashboard (Manager)

## GET request to retrieve the aggregated metrics
curl -X GET [http://127.0.0.1:5000/api/kpi_dashboard](http://127.0.0.1:5000/api/kpi_dashboard)


## Methodology/Technology Stack
The technology stack was chosen for rapid deployment, scalability, and powerful data analysis.
| Component | Technology | Role / Methodology |
| :--- | :--- | :--- |
| **Web Server / API** | Flask (Python) | Handles all HTTP requests for data ingestion (POST) and reporting (GET) | 
| **Persistence Layer** | SQLAlchemy ORM | Defines the Python-native database schema and manages all transactions safely. |
| **Data Reporting** | Pandas Library | Used as the core engine for the /api/kpi_dashboard. It queries the entire SQL database into a DataFrame to perform rapid, complex aggregations (like mean(), nunique(), and drop_duplicates) |
| **Data Storage** | SQLite | A lightweight, file-based database used for development. Can be seamlessly swapped for PostgreSQL in production. |
The app.py script will automatically initialize a new vdt_reports.db file with dummy data for immediate testing.

Sylvanus Olufemi Orodiran [https://www.linkedin.com/in/sylvanus-olufemi-orodiran]
*Active Member: Nigeria Computer Society (NCS ID: 18077)*
