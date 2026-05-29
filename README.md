# Nassau Candy Distributor: Profitability Intelligence Dashboard

An end-to-end business intelligence solution built to transform raw transaction records into a strategic, decision-ready analytics system.

---

## 1. Title of the Project
**Nassau Candy Distributor — Profitability Intelligence Dashboard**
A comprehensive two-year business intelligence solution built in Power BI to expose product-level, division-level, and geographic profitability patterns across Nassau Candy Distributor's full product portfolio — enabling data-driven pricing, portfolio, and distribution decisions.

## 2. Short Description of the Dashboard
The Nassau Candy Distributor Profitability Intelligence Dashboard is a six-page interactive Power BI report built on 10,194 transaction records spanning January 2024 to December 2025. It answers the organization's core analytical challenge: understanding where profit is genuinely generated and where revenue volume masks poor or negative margin performance. 

The dashboard provides a unified analytical workspace featuring a persistent left-side slicer panel (covering date range, year, quarter, division, region, ship mode, gross margin threshold, and product search) synced across six thematically distinct report pages.

## 3. Data Overview
The source dataset consists of `Nassau_Candy_Distributor.xlsx`, containing 10,194 rows of individual order-line transactions covering two full fiscal years (January 3, 2024 — December 31, 2025). 

The dataset tracks 15 unique SKUs across 3 divisions, 4 regions, and 5 manufacturing factories. While the overall blended gross margin appears healthy at 65.91%, this metric masks a massive product-level variance ranging from 7.7% to 80.0%—the exact problem this dashboard is engineered to expose.

### Division Breakdown
| Division | Revenue | Gross Profit | Margin % | Revenue Share | Core Characteristics |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Chocolate** | $131,692.90 | $88,824.62 | 67.4% | 92.9% | 5 Wonka Bar variants; the operational backbone of the business. |
| **Other** | $9,663.25 | $4,333.45 | 44.8% | 6.8% | Chronically dragged down by severe underperformance in specific SKUs. |
| **Sugar** | $427.48 | $284.73 | 66.6% | 0.3% | High margin potential but suffering from negligible volume. |

## 4. Tech Stack and Methodology Used
The analytics pipeline was built end-to-end using the Microsoft ecosystem, ensuring data reproducibility and dynamic execution:

* **Microsoft Excel**: Used for Exploratory Data Analysis (EDA), initial data profiling, column inspection, and outlier detection.
* **Power Query (M Language)**: Handled the ETL pipeline, including cleaning data, enforcing strict data types, creating reference dimensions (e.g., `FactoryRef`), standardizing text casing, and flagging data quality anomalies.
* **Data Modelling**: Implemented a robust **Star Schema relationship model** with many-to-one relationships linking the core transaction log to an official `DateTable` and a `FactoryRef` dimension mapping table to guarantee precise cross-filtering and accurate data aggregation.
* **DAX (Data Analysis Expressions)**: Engineered over 20 dynamic, filter-aware KPI measures and time-intelligence calculations (YoY trends, year-to-date tracking, running totals, and conditional classification logic).
* **Power BI Desktop**: Handled user interface design, report authoring, synced multi-page slicing, bookmark states, conditional formatting, and data visualization utilizing a custom dark navy theme.

## 5. Features

### Business Problem
Despite a strong overall blended gross margin of 65.9%, management lacked granular visibility into portfolio health. The business could not distinguish which individual products drove true profit versus empty revenue volume, whether divisional margins were uniformly healthy, which factories were running dilutive cost structures, and whether geographic growth represented true market expansion or structural over-dependency.

### Goal of the Dashboard
The primary goal is to provide immediate visual answers to core business-critical questions:
* What are the exact headline KPIs (revenue, profit, and margins) across the two-year period?
* Which products fall into strategic operational categories (Stars, Cash Cows, Drains, or Niche)?
* Which specific product lines drive 80% of the company's gross profit (Pareto concentration)?
* Where are the margin risk zones across factories and geographic shipping channels?

### List of Measures/Columns Created
* **Power Query Calculated Columns**: `Gross Margin Pct`, `Days to Ship`, `Year`, `Month Number`, `Month Name`, `Short Month`, `Year-Month`, `Quarter`, `Quarter Full`, and `Ship Date Flag`.
* **Key DAX Measures**: `Total Revenue`, `Total Gross Profit`, `Total Cost`, `Total Units`, `Total Orders`, `Gross Margin %`, `Profit/Cost/Revenue per Unit`, `Revenue YTD`, `Revenue YoY Display`, `GP PY`, `GP YoY %`, `Cumulative GP %`, `Revenue/Profit Contribution %`, `Product Profit Rank`, `Margin Risk Flag`, `Recommended Action`, and `Product Quadrant`.

### Key Visuals and Their Uses (Page-by-Page)
* **Page 1: Executive Overview**
    * *6 Headline KPI Cards*: Immediate tracking of top-line metrics ($141.8K Revenue, 65.9% Blended Margin).
    * *Monthly Revenue vs. Gross Profit (Bar + Line Combo)*: Illustrates performance over time, seasonal spikes (Q4), and verifies margin stability.
    * *Quarterly Revenue 2024 vs. 2025 (Clustered Bar)*: Visualizes the +44.6% YoY growth trajectory quarter-over-quarter.
    * *Division & Factory Summaries (Donut Charts)*: Instantly exposes massive structural concentration across product categories and manufacturing facilities.
    * *Geographic Decomposition Tree*: Allows executives to drill deep from Country $\rightarrow$ State $\rightarrow$ City.
* **Page 2: Product Profitability Deep-Dive**
    * *Ranked Gross Margin % (Horizontal Bar)*: Ranks all 15 SKUs to immediately isolate structural losers (e.g., *Kazookles* at 7.7%).
    * *GP vs. Revenue Comparison (Grouped Horizontal Bar)*: The visual gap between product bars identifies unit cost inefficiencies.
    * *Revenue vs. Margin Scatter (Bubble Chart with Quadrant Shading)*: Automatically segments products into *Stars, Cash Cows, Drains,* or *Niche* categories based on bubble size (Gross Profit).
    * *YoY Revenue Growth (Area Chart)*: Visualizes individual product growth trajectories over both fiscal years.
* **Page 3: Division Performance Dashboard**
    * *Division Revenue vs. GP (Clustered Bar) & Overall Margin Gauge*: High-level summary visuals showing cross-divisional margins.
    * *Division × Region Heatmap (Matrix)*: Pinpoints geographic margin variation (e.g., highlighting Sugar in the Gulf vs. Other in the Gulf).
    * *Product Risk & Contribution Table*: A single matrix displaying revenue/profit contribution shares, absolute margins, risk flags, and dynamic strategic actions.
* **Page 4: Cost Diagnostics & Margin Risk Map**
    * *Unit Economics Cards*: Baselines the portfolio's weighted unit performance ($1.25 cost, $3.67 revenue, $2.42 profit per unit).
    * *Total Cost vs. Total Revenue Scatter*: Identifies lines dangerously hugging the diagonal cost boundary line.
    * *Factory × Division × Margin Table*: Maps the absolute manufacturing-to-margin pipeline to uncover supplier-driven margin leakage.
    * *Cost & GP by Ship Mode (Clustered Bar)*: Proves ship modes are not margin drivers due to identical margin ratios (~66%) across channels.
* **Page 5: Pareto & Profit Concentration**
    * *Gross Profit & Revenue Pareto Charts (Combo Bar + Line)*: Plots cumulative value concentration against a dashed 80% reference line to mathematically isolate portfolio risk.
    * *Concentration KPI Cards*: Quantifies dependencies (e.g., showing that the top product holds a 20.72% profit share while the bottom 10 products represent just 4.94%).
* **Page 6: Geographic & Logistics Analysis**
    * *US Revenue Choropleth Map*: Geographic density map showing market dominance (California leading at 19.7% of US sales).
    * *Factory Location Pin Map*: Scales visual coordinates based on manufacturing revenue footprint.
    * *Full State Profitability Table*: A sortable, granular geographical ledger for deep-dive regional analysis.

### Business Impact and Insights
* **Margin-Neutral Scaling**: Confirmed that the business successfully achieved a massive 44.6% YoY revenue scaling phase ($57.9K to $83.8K) while protecting a completely stable 65.9% gross margin.
* **Extreme Pareto Vulnerability**: Uncovered that **just 5 Chocolate products generate 95.1% of all company gross profit**. This extreme concentration makes the organization highly vulnerable to any supply chain or pricing disruption within the core Chocolate line.
* **Bottom-Line Margin Drags**: Isolated *Kazookles* as a significant portfolio liability, generating a mere 7.7% margin and contributing only 0.10% of total profit while draining operational overhead.
* **Critical Supplier Deficits**: Identified that *The Other Factory (Tennessee)* is severely inefficient, operating at an unviable 11.9% blended margin across its production lines.
* **High-Value Untapped Segments**: Exposed that the *Sugar Division* maintains the portfolio's highest margin potential (e.g., *Everlasting Gobstopper* at 80% margin), yet generates under $500 in total revenue due to severe distribution or supply constraints.

## 6. Recommendations and Conclusion

### Strategic Recommendations
1.  **Immediate Portfolio Correction (STOP)**: Discontinue *Kazookles* immediately or implement an aggressive price hike to hit a mandatory 40% margin floor. Simultaneously, audit and renegotiate the contract with *The Other Factory (Tennessee)* to slash unit production costs.
2.  **Supply Chain Protection (PROTECT)**: Secure long-term supply agreements and dedicate premium logistics infrastructure to the core Chocolate operations (*Lot's O' Nuts* and *Wicked Choccy's*) to insulate the organization's primary profit engine.
3.  **Market Expansion (GROW)**: Focus commercial distribution, marketing investments, and sales targets heavily on the *Sugar Division* to scale its high-margin SKUs. Additionally, expand regional distribution networks in the underperforming Gulf territory.
4.  **Data Quality Governance**: Resolve the systemic logging error causing anomalous "future ship dates" extending out to 2030 in order to restore integrity to logistics and shipping lead-time KPIs.

### Conclusion
The Nassau Candy Distributor Profitability Intelligence Dashboard successfully transforms over 10,000 raw transaction logs into an actionable, executive-ready analytics system. It highlights that the company's strong performance is heavily propped up by a core group of 5 Chocolate variants, while hiding localized value destruction and major untouched revenue opportunities in the Sugar line. By enacting the targeted, data-backed interventions surfaced by this dashboard, management can de-risk its supply chain, eliminate margin-dilutive channels, and capture highly lucrative revenue streams.

<img width="1500" height="611" alt="Dashboard screenshot" src="https://github.com/user-attachments/assets/d5b28c0f-bee9-4c05-9bb9-98dbb6ee4d0c" />

<img width="1500" height="611" alt="Dashboard screenshot Pg6" src="https://github.com/user-attachments/assets/3e9f5773-019f-4d1b-abda-c3f3a20cb9f8" />
