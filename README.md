# ✈️ IndiGo 6E: Enterprise Aviation Analytics & Operations Command Suite

[![Power BI](https://img.shields.io/badge/Power_BI-Desktop_%26_Service-F2C811?logo=powerbi&logoColor=black&style=for-the-badge)](https://powerbi.microsoft.com/)
[![Snowflake](https://img.shields.io/badge/Snowflake-Data_Warehouse-29B5E8?logo=snowflake&logoColor=white&style=for-the-badge)](https://www.snowflake.com/)
[![AWS S3](https://img.shields.io/badge/AWS-S3_Data_Lake-569A31?logo=amazons3&logoColor=white&style=for-the-badge)](https://aws.amazon.com/s3/)
[![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white&style=for-the-badge)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App_Framework-FF4B4B?logo=streamlit&logoColor=white&style=for-the-badge)](https://streamlit.io/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-Machine_Learning-F7931E?logo=scikitlearn&logoColor=white&style=for-the-badge)](https://scikit-learn.org/)
[![SQL](https://img.shields.io/badge/SQL-Advanced_Data_Modeling-CC292B?logo=microsoftsqlserver&logoColor=white&style=for-the-badge)]()
[![DAX](https://img.shields.io/badge/DAX-Time_Intelligence_%26_Measures-001F5B?style=for-the-badge)]()

> **A mission-critical enterprise intelligence ecosystem built for InterGlobe Aviation Limited (IndiGo 6E) — India's largest carrier.**  
> Seamlessly integrates **AWS S3 data lakes**, an enterprise **Snowflake Star-Schema warehouse**, in-database **Snowflake Cortex AI**, an executive **15+ page Power BI operational suite**, and full-stack **Machine Learning and Agentic AI applications**.

---

## 📑 Table of Contents

- [Executive Summary](#-executive-summary)
- [Enterprise Architecture](#-enterprise-architecture)
- [Dataset Scale & Star Schema Design](#-dataset-scale--star-schema-design)
- [Power BI Enterprise Analytics Suite](#-power-bi-enterprise-analytics-suite)
- [Cloud Warehousing & Snowflake Cortex AI](#-cloud-warehousing--snowflake-cortex-ai)
- [Full-Stack AI / ML Applications](#-full-stack-ai--ml-applications)
  - [1. IndiGo 6E AI Copilot (Generative AI)](#1-indigo-6e-ai-copilot-generative-ai)
  - [2. Autonomous Crew FDTL Safety Agent (Agentic AI)](#2-autonomous-crew-fdtl-safety-agent-agentic-ai)
  - [3. Catering Waste Optimizer (Predictive ML)](#3-catering-waste-optimizer-predictive-ml)
- [Project Directory Structure](#-project-directory-structure)
- [Installation & Getting Started](#-installation--getting-started)
- [Quantifiable Business Impact & ROI](#-quantifiable-business-impact--roi)
- [Author & License](#-author--license)

---

## 🌐 Executive Summary

IndiGo operates over **2,000+ daily flights across 138 global destinations**, transporting over 100 million passengers annually. Managing this scale requires real-time coordination across **flight dispatch, crew rostering, air cargo, catering procurement, and global ground handling vendor SLAs**.

This repository delivers an end-to-end analytics platform that transforms raw operational logs into strategic decision intelligence:
- **Cloud Engineering:** Ingests and stages high-frequency aviation data via **AWS S3**, transformed into an optimized Star-Schema data warehouse on **Snowflake**.
- **In-Database AI:** Employs **Snowflake Cortex AI** SQL functions (`COMPLETE`, `CLASSIFY_TEXT`) for zero-latency cancellation classification and ground handler assessment.
- **Business Intelligence:** Delivers **15+ Power BI operational pages** with 40+ complex DAX measures, geospatial mapping, and compensation waterfall analysis.
- **Predictive & Agentic AI:** Integrates custom full-stack Python web applications utilizing **Random Forest regression** for catering demand forecasting, an **Agentic AI** system enforcing DGCA pilot fatigue compliance, and an **LLM-powered conversational copilot**.

---

## 🏛️ Enterprise Architecture

```
┌─────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   DATA INGESTION & LAKE                                     │
│  34 Enterprise CSV Datasets (Flight Ops, Crew Rosters, Cargo AWBs, Catering, 138 Stations)   │
│                                           │                                                 │
│                                   ▼ [AWS S3 Staging]                                        │
│                        s3://indigo-dw-operations-lake/                                      │
└───────────────────────────────────────────┬─────────────────────────────────────────────────┘
                                            │
                                            ▼
┌─────────────────────────────────────────────────────────────────────────────────────────────┐
│                           SNOWFLAKE ENTERPRISE CLOUD DATA WAREHOUSE                         │
│   Database: INDIGO_DW | Schema: OPERATIONS | Warehouse: INDIGO_WH                           │
│                                                                                             │
│  ┌───────────────────────┐   ┌──────────────────────┐   ┌────────────────────────────────┐  │
│  │ FACT TABLES           │   │ DIMENSION TABLES     │   │ SNOWFLAKE CORTEX AI            │  │
│  │ • FACT_FLIGHT_OPS     │   │ • DIM_PILOT          │   │ • CORTEX.COMPLETE()            │  │
│  │ • FACT_CREW_DUTY      │   │ • DIM_CABIN_CREW     │   │ • CORTEX.CLASSIFY_TEXT()       │  │
│  │ • FACT_CARGO          │   │ • DIM_FLEET          │   │ • CORTEX.SENTIMENT()           │  │
│  │ • FACT_CATERING       │   │ • DIM_AIRPORTS (138) │   │ (In-database LLM Analytics)    │  │
│  │ • FACT_GROUND_HANDLER │   │ • DIM_BLUCHIP_TIER   │   │                                │  │
│  └───────────────────────┘   └──────────────────────┘   └────────────────────────────────┘  │
└───────────────────────┬─────────────────────────────────────────────┬───────────────────────┘
                        │                                             │
                        ▼                                             ▼
┌──────────────────────────────────────────────┐  ┌───────────────────────────────────────────┐
│           POWER BI ANALYTICS SUITE           │  │     FULL-STACK AI / ML APPLICATIONS       │
│    DirectQuery & Star-Schema Data Model      │  │        Streamlit + Python Engine          │
│                                              │  │                                           │
│  • Flight Operations & On-Time Perf (OTP)   │  │  🤖 IndiGo 6E AI Copilot (LLM-Powered)   │
│  • Crew Workforce & Salary Waterfalls        │  │     Natural language conversational Q&A   │
│  • 6E CarGo & Freighter Yield Analytics      │  │                                           │
│  • In-Flight Catering Economics              │  │  🛡️ Crew FDTL Safety Agent (Agentic AI)  │
│  • 138-Station Ground Handler SLA Benchmark  │  │     Autonomous DGCA CAR 7J-I monitoring   │
│  • Fleet Utilization & Order Book            │  │                                           │
│  • BluChip Loyalty Customer Frequency        │  │  🍽️ Catering Waste Optimizer (ML)         │
│                                              │  │     Random Forest demand forecasting      │
└──────────────────────────────────────────────┘  └───────────────────────────────────────────┘
```

---

## 📊 Dataset Scale & Star Schema Design

The warehouse unifies **34 relational datasets** into an enterprise Star Schema, handling millions of records with sub-second query performance:

| Table Name | Type | Row Count | Attributes | Primary Business Focus |
|---|---|---|---|---|
| `FACT_FLIGHT_DAILY_OPERATIONS` | Fact | **723,308** | 79 Columns | Route delays, passenger load factors, OTP %, ancillary revenue |
| `FACT_CREW_DUTY` | Fact | **723,400** | 55 Columns | Duty hours, flight hours, layover hotel costs, FDTL flags |
| `FACT_CARGO_ALIGNED` | Fact | **173,729** | 63 Columns | Air Waybill (AWB), chargeable weight, freight yield, belly vs freighter |
| `FACT_CATERING_ENHANCED` | Fact | **4,000,000+** | 85 Columns | Uplift count, IndiGoStretch premium meals, meal waste % |
| `FACT_GROUND_HANDLERS` | Fact | **138** | 23 Columns | Turnaround SLAs, baggage delivery times, ISAGO safety ratings |
| `DIM_PILOT` | Dimension | **400+** | 72 Columns | Captain/FO licensing, fleet type, monthly basic pay, CTC breakdown |
| `DIM_CABIN_CREW` | Dimension | **2,000+** | 54 Columns | Crew basing, overtime slabs, forex entitlements, training academy |
| `DIM_FLEET` | Dimension | **400+** | 27 Columns | A320neo, A321neo, ATR 72-600, B777-300ER, MSN, aircraft age |
| `DIM_FLEET_ORDER_BOOK` | Dimension | **1,000+** | 15 Columns | Firm orders, XLR delivery pipeline, engine specifications |

---

## 📈 Power BI Enterprise Analytics Suite

The Power BI dashboard provides a **comprehensive command center** designed for executive leadership (CEO, COO, VP Airport Operations, Head of Crew Scheduling, and Commercial Directorate).

### 1. Flight Daily Operations & On-Time Performance (OTP)
* **Real-Time Punctuality:** Analyzes OTP % across 723K+ flights segmented by Domestic vs International routes, departure hour time-bands, and aircraft families.
* **Commercial Yield Tracking:** Interactive decomposition of Total Flight Revenue into Base Ticket Revenue and Optional Ancillaries (Seat Select, Fast Forward, 6E Eats, Excess Baggage).

### 2. Crew Workforce, Basing & Compensation Waterfalls
* **Pilot & Cabin Crew Salary Waterfalls:** Custom financial waterfall visuals tracking Gross Compensation down to Basic Pay, Flying Hour Allowance, Domestic/International Layover Per Diems, Night Flying, and Standby Allowances.
* **Crew Layover Optimization:** Cost-per-layover tracking across major operating bases (DEL, BOM, BLR, HYD, CCU, MAA) against contract hotel rates and shuttle expenses.

### 3. 6E CarGo & Freighter Yield Logistics
* **Volumetric vs Actual Weight Efficiency:** Monitors freight yield (INR/kg) across belly-hold capacity on passenger aircraft vs dedicated Airbus A321P2F freighters.
* **Commodity Breakdown:** Tracks high-value electronics, pharmaceuticals, perishables, and dangerous goods (DG) compliance across bonded customs hubs.

### 4. In-Flight Catering Economics & Menu Margin Analysis
* **IndiGoStretch & Buy-on-Board (BOB) Profitability:** Compares meal procurement costs against sales revenue across distinct flight duration sectors.
* **Uplift Waste Tracking:** Identifies flights with chronic over-catering to reduce disposal and carbon emissions.

### 5. Airport Ground Handling Operations & Vendor SLA Management
* **138-Station GPS Geospatial Map:** Custom-coded bubble map rendering every domestic and international station with precise latitude/longitude coordinates, sized by turnaround SLA target.
* **Agile vs Third-Party Benchmark:** Ranked horizontal clustered bar charts contrasting in-house subsidiary **Agile Airport Services (31m turnaround, 22m last-bag SLA across 96 Indian stations)** against **34 international third-party handlers (45–60m turnaround at DXB, LHR, IST, SIN, BKK)**.
* **Executive Scorecard Matrix:** Multi-tier station drill-down showing handler parent group, ISAGO Level 4 safety audit status, deicing capabilities, and local billing currencies.

---

## ❄️ Cloud Warehousing & Snowflake Cortex AI

All transactional datasets are staged via AWS S3 and loaded into Snowflake using optimized multi-cluster virtual warehouses. **Snowflake Cortex AI** is executed directly inside SQL DDLs and views for in-database intelligence:

### Automated Cancellation Root-Cause Categorization
```sql
CREATE OR REPLACE VIEW INDIGO_DW.OPERATIONS.V_CANCELLATION_AI_CLASSIFIED AS
SELECT
    FLIGHT_NUMBER,
    FLIGHT_DATE,
    ORIGIN_IATA || ' -> ' || DESTINATION_IATA AS ROUTE,
    CANCELLATION_REASON,
    SNOWFLAKE.CORTEX.CLASSIFY_TEXT(
        CANCELLATION_REASON,
        ARRAY_CONSTRUCT(
            'Weather / Low Visibility (CAT III)',
            'Technical / AOG Maintenance',
            'ATC Air Traffic Slot Restriction',
            'Crew FDTL Flight Duty Expiry',
            'Airport Infrastructure Congestion',
            'Commercial Consolidation'
        )
    ):label::VARCHAR AS AI_STANDARDIZED_REASON,
    SNOWFLAKE.CORTEX.CLASSIFY_TEXT(
        CANCELLATION_REASON,
        ARRAY_CONSTRUCT('Weather', 'Technical', 'ATC', 'Crew', 'Airport', 'Commercial')
    ):score::FLOAT AS CONFIDENCE_SCORE
FROM INDIGO_DW.OPERATIONS.FACT_FLIGHT_DAILY_OPERATIONS
WHERE IS_CANCELLED = 'True';
```

### In-Database Ground Handler Vendor Assessment
```sql
CREATE OR REPLACE VIEW INDIGO_DW.OPERATIONS.V_GROUND_HANDLER_AI_ASSESSMENT AS
SELECT
    AIRPORT_IATA,
    GROUND_HANDLER,
    HANDLING_MODEL,
    TURNAROUND_SLA_TARGET_MINUTES,
    BAGGAGE_DELIVERY_SLA_FIRST_BAG_MIN,
    RAMP_SAFETY_AUDIT_RATING,
    SNOWFLAKE.CORTEX.COMPLETE(
        'mistral-large2',
        CONCAT(
            'You are IndiGo VP Ground Operations. Evaluate this ground handler in 2 sentences. ',
            'Station: ', AIRPORT_IATA, ', Handler: ', GROUND_HANDLER,
            ', Model: ', HANDLING_MODEL, ', Turnaround SLA: ', TURNAROUND_SLA_TARGET_MINUTES, ' min',
            ', First Bag SLA: ', BAGGAGE_DELIVERY_SLA_FIRST_BAG_MIN, ' min',
            ', Safety Certification: ', RAMP_SAFETY_AUDIT_RATING,
            '. Benchmark: Agile Airport Services (31 min turnaround, 8 min first bag, ISAGO certified).'
        )
    ) AS AI_EXECUTIVE_ASSESSMENT
FROM INDIGO_DW.OPERATIONS.FACT_GROUND_HANDLERS;
```

---

## 🤖 Full-Stack AI / ML Applications

Beyond business intelligence dashboards, this project deploys **three dedicated full-stack web applications** built with Python, scikit-learn, and Streamlit.

### 1. IndiGo 6E AI Copilot (Generative AI)
* **What it does:** An executive natural-language analytics assistant. Business users ask free-form operational questions in plain English and receive instant data-backed answers with dynamically generated Plotly charts.
* **Sample Queries Handled:**
  - *"What was our average on-time performance on metro routes last month?"*
  - *"Compare revenue contribution between saver fares and IndiGoStretch business seats."*
  - *"Which international ground handlers have turnaround SLAs exceeding 50 minutes?"*
* **Architecture:** Streamlit frontend + dynamic conversational prompt engineering + real-time statistical aggregation across 100K+ cached flight records.

### 2. Autonomous Crew FDTL Safety Agent (Agentic AI)
* **What it does:** An autonomous compliance monitor that enforces **DGCA Civil Aviation Requirements (CAR Section 7, Series J, Part I)** regarding Flight Duty Time Limitations (FDTL).
* **The Agentic Loop:**
  - **Perceive:** Scans 723,400+ crew duty logs across all 400+ pilots and 2,000+ cabin crew.
  - **Reason:** Evaluates rolling duty windows:
    - *24-Hour Duty Hours* (Limit: 12 hrs)
    - *7-Day Flight Hours* (Limit: 30 hrs)
    - *30-Day Cumulative Hours* (Limit: 100 hrs)
  - **Act:** Triggers color-coded **CRITICAL** (limit exceeded) and **WARNING** (approaching 85% threshold) alerts, auto-generating an executive safety briefing for crew dispatchers to prevent regulatory groundings and fines.

### 3. Catering Waste Optimizer (Predictive ML)
* **What it does:** Solves the airline industry's persistent over-catering problem (where airlines routinely discard 15–20% of loaded perishable fresh food).
* **Algorithm & Modeling:**
  - Employs a **Random Forest Regressor** trained on 200,000+ sector flight records.
  - **Key Features:** Passenger booking count, route group distance, flight duration, departure hour time-band, meal window type (breakfast/lunch/dinner), and historical participation rates.
  - **Results:** Achieves high demand prediction accuracy, allowing catering managers to load optimal buffer quantities. Reduces food wastage by an estimated **15–20%**, translating to tens of crores in procurement savings.

---

## 📁 Project Directory Structure

```
IndiGo-Aviation-Analytics-Suite/
│
├── AI_Apps/                                    # Full-Stack AI/ML Python Applications
│   ├── indigo_copilot.py                       # GenAI Conversational Copilot (Streamlit)
│   ├── catering_optimizer.py                   # Random Forest Catering Demand Predictor
│   │
│   ├── agents/                                 # Agentic AI Autonomous Systems
│   │   └── crew_safety_agent.py                # 24/7 DGCA FDTL Compliance Monitor
│   │
│   └── models/                                 # Serialized ML Models & Artifacts
│       ├── catering_rf_model.pkl
│       └── catering_encoders.pkl
│
├── SQL/                                        # Cloud Data Warehouse DDLs & Queries
│   ├── indigo_snowflake_star_schema.sql        # Star-Schema DDL & S3 COPY INTO
│   ├── snowflake_cortex_ai_views.sql           # Cortex COMPLETE & CLASSIFY_TEXT queries
│   └── update_fact_ground_handler_snowflake.sql# 138-Station GPS Data Pipeline
│
├── PowerBI/                                    # Business Intelligence Assets
│   ├── IndiGo_6E_Operations_Master.pbix        # Master 15-Page Power BI File
│   └── DAX_Measures_Library.dax                # Complete DAX Formula Repository
│
├── Data_Dictionary/                            # Enterprise Metadata Documentation
│   ├── IndiGo_Star_Schema_Dictionary.md
│   └── DGCA_FDTL_Compliance_Rules.md
│
├── requirements.txt                            # Python Package Dependencies
└── README.md                                   # Project Documentation
```

---

## 🚀 Installation & Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/IndiGo-Aviation-Analytics-Suite.git
cd IndiGo-Aviation-Analytics-Suite
```

### 2. Set Up Python Environment
```bash
python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt
```

### 3. Launch the AI Applications

**Launch the IndiGo 6E AI Copilot:**
```bash
streamlit run AI_Apps/indigo_copilot.py --server.port 8501
```

**Launch the Autonomous Crew FDTL Safety Agent:**
```bash
streamlit run AI_Apps/agents/crew_safety_agent.py --server.port 8502
```

**Launch the Catering Waste Optimizer:**
```bash
streamlit run AI_Apps/catering_optimizer.py --server.port 8503
```

### 4. Power BI Setup
1. Open `PowerBI/IndiGo_6E_Operations_Master.pbix` in **Power BI Desktop**.
2. Update the Snowflake connection parameters under **Transform Data ➔ Data Source Settings** to point to your `INDIGO_DW.OPERATIONS` warehouse.
3. Click **Apply Changes** to refresh visuals and DAX calculations.

---

## 💼 Quantifiable Business Impact & ROI

| Domain | Operational Problem | Platform Solution | Projected Business Impact |
|---|---|---|---|
| **Catering Operations** | 15–20% perishable food discarded per sector | Random Forest meal demand predictive loading | **INR 50–75 Cr annual savings** in food procurement |
| **Crew Scheduling** | Manual audits risking DGCA fatigue breaches | 24/7 Agentic AI proactive warning system | **100% DGCA CAR 7J-I compliance**; prevents aircraft grounding |
| **Ground Handling** | Unmonitored overseas third-party turnaround delays | 138-station SLA benchmark & GPS tracking | Identifies **15–30 min turnaround gaps** for vendor renegotiation |
| **Operations Management** | Siloed Excel reports delaying daily decisions | Snowflake Cortex AI + Power BI Command Center | **Sub-second executive decision-making** via real-time analytics |

---

## 👤 Author & Acknowledgments

* **Project Architect:** Data Analytics & AI Specialist
* **Domain Context:** Modeled after real-world operations, financial disclosures, and scheduling guidelines of **InterGlobe Aviation Limited (IndiGo 6E)**.
* **Regulations Reference:** Directorate General of Civil Aviation (DGCA) India — Civil Aviation Requirements (CAR Section 7, Series J, Part I).
