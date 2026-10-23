**Supply Chain Performance Analytics Dashboard**

📌 Executive Summary

The Supply Chain Performance Analytics project delivers an enterprise-grade reporting solution designed to provide end-to-end visibility into logistics operations, order fulfillment pipelines, and vendor delivery efficiency.

Built using Microsoft Power BI, Power Query (M), and DAX, this dashboard enables operational leaders and logistics managers to identify fulfillment bottlenecks, evaluate delivery service level agreements (SLAs), monitor order backlog trends, and optimize overall supply chain efficiency.

📸 Executive Dashboard Preview

Executive Overview Landing Page



Replace the image placeholder above with your actual screenshot link (<img width="1536" height="942" alt="Landing page" src="https://github.com/user-attachments/assets/a93e0568-5423-417c-a5e5-4efc26bb7571" />
).

🔑 Key Features & Core Insights

Fulfillment & Delivery SLA Tracking: Real-time visibility into On-Time, Late, and Early shipment rates to optimize customer satisfaction and carrier performance.

Order Volume Analytics: Breakdown of total orders, overall volume trends, order status distribution, and fulfillment cycle times.

Performance Key Metrics: Dedicated executive KPI cards tracking total revenue, overall fulfillment efficiency percentage, late delivery counts, and order defect rates.

Interactive Multi-Level Filtering: Seamless slice-and-dice capabilities by Date, Order Status, Geographic Region, Delivery Type, and Product Categories.

Geographic & Regional Logistics Mapping: Spatial insight into shipment destinations, regional distribution density, and localized delivery delay tracking.

🛠 Tech Stack & Architecture

Business Intelligence Tool: Microsoft Power BI Desktop / Power BI Service

ETL & Data Transformation: Power Query Engine (M Language)

Calculations & Analytical Logic: Data Analysis Expressions (DAX)

Data Modeling Paradigm: Star Schema (Fact and Dimension Tables)

Visual Design: Custom UI/UX design with unified color hierarchy and responsive layout grid.

🏗 Data Model & Architecture

The analytical backend utilizes a Star-Schema topology optimized for fast DAX query processing and intuitive aggregation behavior:

                  +-------------------+
                  |   Dim_Calendar    |
                  +-------------------+
                            |
                            | (1:N)
                            v
+------------------+     +-------------------+     +------------------+
|   Dim_Product    |---->|    Fact_Orders    |<----|   Dim_Customer   |
+------------------+ (1:N)+-------------------+(1:N)+------------------+
                            ^
                            | (1:N)
                  +-------------------+
                  |   Dim_Geography   |
                  +-------------------+


🧮 Sample Key DAX Measures

1. On-Time Delivery Rate (%)

OnTime Delivery Rate = 
DIVIDE(
    CALCULATE(
        COUNTROWS('Fact_Orders'),
        'Fact_Orders'[Delivery_Status] = "On-Time"
    ),
    COUNTROWS('Fact_Orders'),
    0
)


2. Total Order Revenue

Total Revenue = 
SUMX(
    'Fact_Orders',
    'Fact_Orders'[Quantity] * 'Fact_Orders'[Unit_Price]
)


3. Late Delivery Count

Late Deliveries = 
CALCULATE(
    COUNT('Fact_Orders'[Order_ID]),
    'Fact_Orders'[Delivery_Status] = "Late"
)


🚀 Deployment & Local Setup

Prerequisites

Microsoft Power BI Desktop (Latest Version recommended)

Installation Steps

Clone the Repository:

git clone https://github.com/your-username/supply-chain-performance-analytics.git
cd supply-chain-performance-analytics


Open the Project File:

Launch Power BI Desktop.

Navigate to File -> Open and select the .pbix file located in the repository directory.

Data Source Configuration:

If prompted, update data source parameters via Transform Data -> Data Source Settings to connect to your local or cloud database/Excel files.

Apply Changes & Refresh:

Click Refresh on the Home tab to update all calculated tables, DAX measures, and dashboard visuals.

📊 Business Impact & Operational Value

Reduced Logistics Overhead: Pinpoints recurring carrier bottlenecks to enable targeted SLA negotiations.

Improved Customer SLA: Provides proactive tracking of delayed shipments before final delivery failure.

Enhanced Working Capital Efficiency: Identifies slow-moving fulfillment routes and optimizes inventory allocations.

🤝 Contributing

Contributions, feedback, and enhancement suggestions are welcome!

Fork the repository.

Create your Feature Branch (git checkout -b feature/Optimization).

Commit your changes (git commit -m 'Add performance optimizations').

Push to the branch (git push origin feature/Optimization).

Open a Pull Request.

📄 License

Distributed under the MIT License. See LICENSE for more information.
