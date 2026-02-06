# Sales Analytics - Automated Data Pipeline

An end-to-end automated sales analytics system that processes online superstore data through a cloud-based pipeline. This project demonstrates modern data engineering practices including cloud storage, ETL automation, database management, interactive visualization, and executive reporting.

## Overview

This project transforms raw sales data into actionable business insights using an automated pipeline. Data flows from AWS S3 cloud storage through Alteryx ETL workflows, gets stored in a MySQL database, and feeds into both interactive Tableau dashboards and formatted SSRS reports for different stakeholder needs.

## Data Source

The Superstore dataset contains sales transactions from an online retail business between 2014 and 2017, including:
- Order details (dates, shipping information, customer data)
- Product information (categories, sub-categories, names)
- Financial metrics (sales revenue, profit, discounts)
- Geographic data (regions, states, cities)
- Customer segments (Consumer, Corporate, Home Office)

## Architecture

**Data Flow:**
```
AWS S3 (Raw Data Storage) 
    ↓
Alteryx Designer (ETL Processing)
    ↓
MySQL Database (Data Warehouse)
    ↓
├─→ Tableau (Interactive Dashboard)
└─→ SSRS (Executive Reports)
```

## Technologies Used

- **AWS S3** - Cloud data storage with versioning and lifecycle management
- **Alteryx Designer** - ETL workflow automation for data cleaning and transformation
- **MySQL** - Relational database for processed data storage
- **Tableau** - Interactive data visualization and dashboard creation
- **SSRS** - Paginated reporting for executive summaries
- **Excel** - Initial data exploration and validation

## Pipeline Components

### 1. Cloud Storage (AWS S3)
- Organized bucket structure separating raw and processed data
- Enabled versioning for data lineage tracking
- Lifecycle policies for cost optimization
- Tagged resources for project organization

### 2. ETL Workflow (Alteryx)
The Alteryx workflow performs:
- **Data Integration:** Combines orders, returns, and regional manager data
- **Data Cleaning:** Handles null values, removes duplicates, standardizes formats
- **Business Logic:** Calculates profit margins, flags returned orders, tracks processing time
- **Multi-format Output:** Exports to both MySQL database and CSV files

Key transformations:
- Left join orders with returns to identify returned items
- Join with regional data to add manager information
- Calculate profit margin: (Profit / Sales) × 100
- Calculate order processing time in days

### 3. Database (MySQL)
- Structured schema designed for analytical queries
- Optimized for dashboard and report consumption
- Supports historical trend analysis
- Enables complex SQL aggregations

### 4. Visualization (Tableau)
Interactive dashboard featuring:
- KPI cards showing total sales, profit, orders, and growth rates
- Regional performance breakdown
- Daily sales trends
- Top performing sub-categories
- Detailed order-level data table
- Dynamic filters for date ranges and regions

### 5. Reporting (SSRS)
Executive summary reports with:
- High-level KPI overview
- Regional sales breakdown
- Product performance analysis
- Formatted for print and email distribution

## Key Insights

- **Total Revenue:** $2.3M in sales over the analysis period
- **Regional Performance:** Central region leads with $501K, followed by East ($679K), West ($726K), and South ($392K)
- **Product Categories:** Office supplies and technology show strong performance
- **Top Sub-Categories:** Accessories ($7.4K), Binders ($8.6K), and Paper ($4.2K) generate highest revenue
- **Profit Analysis:** Overall profit of $286K with healthy margins across most categories

## Project Structure
```
sales-analytics-pipeline/
├── data/
│   ├── raw/                    # Original CSV files (also in S3)
│   └── processed/              # Alteryx output files
├── alteryx/
│   └── Sales_ETL_Pipeline.yxmd # ETL workflow
├── sql/
│   ├── schema.sql              # Database structure
│   └── queries.sql             # Analysis queries
├── tableau/
│   └── sales_dashboard.twbx    # Interactive dashboard
├── ssrs/
│   └── executive_report.rdl    # SSRS report template
├── screenshots/                # Project documentation images
└── README.md
```

## Setup Instructions

### Prerequisites
- AWS account with S3 access
- Alteryx Designer (trial version available)
- MySQL Server 8.0+
- Tableau Desktop
- SQL Server Reporting Services

### Configuration Steps

1. **AWS S3 Setup**
   - Create S3 bucket: `sales-dashboard-pipeline-2025`
   - Upload raw CSV files to `raw-data/` folder
   - Configure IAM credentials for Alteryx access

2. **Database Setup**
```sql
   CREATE DATABASE sales_analytics;
```

3. **Run Alteryx Workflow**
   - Open `Sales_ETL_Pipeline.yxmd`
   - Update S3 connection credentials
   - Update MySQL connection settings
   - Run workflow to populate database

4. **Tableau Dashboard**
   - Open dashboard file
   - Update MySQL data source connection
   - Refresh data

5. **SSRS Reports**
   - Deploy report to SSRS server
   - Configure MySQL connection
   - Set up scheduled delivery if needed

## Features

✅ Automated data pipeline from cloud to insights  
✅ Multi-source data integration (orders, returns, regional data)  
✅ Data quality checks and transformations  
✅ Scalable cloud storage architecture  
✅ Real-time interactive dashboards  
✅ Professional formatted reports for executives  
✅ Complete data lineage and version control  

## Business Value

This pipeline enables:
- **Faster Decision Making:** Automated daily refreshes eliminate manual data processing
- **Data Consistency:** Single source of truth across all reporting tools
- **Scalability:** Cloud architecture handles growing data volumes
- **Accessibility:** Both interactive exploration (Tableau) and static reports (SSRS) for different user needs
- **Cost Optimization:** S3 lifecycle policies reduce storage costs over time

## Future Enhancements

- Implement automated scheduling for workflow execution
- Add real-time streaming data capabilities
- Integrate predictive analytics for sales forecasting
- Create mobile-responsive dashboard versions
- Add data quality monitoring and alerting

## Contact

For questions or collaboration opportunities, feel free to reach out.

---

**Note:** This project demonstrates skills in cloud architecture, ETL automation, database design, and business intelligence - core competencies for modern data analytics roles.
