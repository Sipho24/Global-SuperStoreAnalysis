# Global SuperStore Executive Dashboard
A PowerBI dashboard built for a national retail company to help executives monitor sales performance, profitability, customer behavior, and regional performance across 2011-2014.

Built as part of the **AnalystLab Africa Data Analytics Internship** (Week 2).

## Project Overview:
Metric Value

Dataset | Global Superstore (51,290 rows, 24 columns) |
| Date range | January 2011 - December 2014 |
| Total Sales | $12,642,502 |
| Total Profit | $1,467,457 |
| Profit Margin | 11.6% |
| Countries | 147 |
| Markets | 7 (APAC, Africa, Canada, EMEA, EU, LATAM, US) |
| Product Categories | 3 (Furniture, Office Supplies, Technology) |
| Sub-Categories | 17 |
| Customers | 1,590 |

##Tools Used 
Tool Purpose

| **Microsoft Power BI Desktop** | Data cleaning (Power Query), data modelling, dashboard development |
| **DAX** | Calculated measures and columns |
| **Power Query** | Data transformation and type conversion |

##Data Preparation
Before building the dashboard, the raw dataset was audited and cleaned in Power Query. Key steps:

| Issue | Action Taken | Rows Affected |
|---|---|---|
| Order Date and Ship Date stored as text (DD-MM-YYYY) | Converted to Date type using Locale: English (United Kingdom) | 51,290 |
| US Postal Codes lost leading zeros | Converted to Text; padded to 5 digits (or excluded from model) | 449 |
| Product Name had trailing and double spaces | Trimmed whitespace; replaced double spaces with single | 48 |
| Non-standard discount values in LATAM (0.002, 0.202, etc.) | Rounded to 2 decimal places | 629 |
No duplicate rows were found. The only column with missing values was Postal Code (80.5% null, US only), which was excluded from the dashboard model as it is not pivotal to the analysis.

## Dashboard Features
### KPI Cards (5)
KPI | Measure | Value |
|---|---|---|
| Total Sales | `SUM([Sales])` | $12,642,502 |
| Total Profit | `SUM([Profit])` | $1,467,457 |
| Total Orders | `DISTINCTCOUNT([Order ID])` | 25,035 |
| Avg Sales per Order | `DIVIDE([Total Sales], [Total Orders])` | $505.11 |
| Profit Margin | `DIVIDE([Total Profit], [Total Sales])` | 11.6% |

### Visualisation
1 | Bar chart | Sales by Sub-Category | Which products drive revenue |
| 2 | Bar chart | Profit by Market | Which markets are profitable vs losing (red/green) |
| 3 | Column chart | Sales by Category | Revenue split across 3 categories |
| 4 | Column chart | Profit by Category (drill-down) | Profit with drill to sub-category level |
| 5 | Line chart | Sales & Profit Trend | Monthly trend over 4 years |
| 6 | Donut chart | Sales by Segment | Consumer / Corporate / Home Office split |
| 7| Matrix | Category x Sub-Category | Sales, Profit, Margin with heat-map colouring |

### Slicers (4)
Year, Market, Category, Order Priority

## Key DAX Measures

Total Sales = SUM('Global_Superstore2'[Sales])
Total Profit = SUM('Global_Superstore2'[Profit])
Total Orders = DISTINCTCOUNT('Global_Superstore2'[Order ID])
Avg Sales per Order = DIVIDE([Total Sales], [Total Orders], 0)
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
