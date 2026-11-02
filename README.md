# Retail Business Performance and Profitability Analysis

## Project overview

This project analyzes Maven Toys retail sales and inventory data to understand revenue, gross profit, product category performance, store location performance, and inventory movement.

The work uses MySQL for data checks and calculations, Python for correlation analysis, and Power BI for the interactive dashboard.

## Project files

```text
project Retail_Business_Analysis/
├── README.md
├── retail_analysis.sql
├── Retail_Inventory_Analysis.ipynb
├── Retail_Business_Performance_Dashboard.pbix
├── Retail_Business_Performance_Dashboard.pdf
├── Final_Project_Report.pdf
└── data/
    ├── calendar.csv
    ├── data_dictionary.csv
    ├── inventory.csv
    ├── products.csv
    ├── sales.csv
    ├── stores.csv
    ├── sales_analysis.csv
    └── inventory_profit_analysis.csv
```

`Final_Project_Report.pdf` should be added after the written report is finalized. The dashboard PDF is an export of the Power BI page.

## Dataset and coverage

The analysis uses these source tables:

- **Sales:** 35,501 transaction rows
- **Products:** 35 products
- **Stores:** 50 stores
- **Inventory:** 1,593 store-product rows

The sales data covers **January 1 through February 6, 2022**, or 37 days. February is only a partial month.

## Tools used

- **MySQL Workbench:** imported and checked the data, cleaned product prices, and created analysis views.
- **Python:** used Pandas, Seaborn, and Matplotlib in the Jupyter notebook.
- **Power BI Desktop:** created the interactive dashboard.

The project brief lists Tableau. This project uses Power BI for the dashboard; confirm that Power BI is accepted if the assignment specifically requires Tableau.

## Analysis steps

1. Imported the sales, products, stores, and inventory CSV files into the `retail_business_analysis` MySQL database.
2. Checked for missing values, duplicate IDs, invalid units, and unmatched product or store records.
3. Cleaned the dollar signs from product cost and price and converted those values to numbers.
4. Created a `sales_analysis` view with revenue and gross profit for each sale.
5. Created an `inventory_profit_analysis` view with stock on hand, average daily units sold, estimated inventory days, and linked gross profit.
6. Used Python to examine the relationship between estimated inventory days and gross profit.
7. Built a Power BI dashboard with summary cards, category charts, monthly revenue, store location revenue, an inventory table, and filters.

## Main formulas

- **Revenue** = Units × Product Price
- **Gross Profit** = Units × (Product Price − Product Cost)
- **Gross Profit Margin** = Gross Profit ÷ Revenue × 100
- **Estimated Inventory Days** = Stock on Hand ÷ Average Units Sold Per Day

Estimated inventory days are based on the 37-day data period. A `NULL` estimate means no sales were recorded for that store-product combination during the period, so an average daily sales rate could not be calculated.

## Key results

### Overall sales

- **Total revenue:** $651,878.81
- **Total gross profit:** $199,311
- **Overall gross profit margin:** 30.57%

Gross profit is before operating expenses and is not the same as net profit.

### Product category results

| Product category | Revenue | Gross profit | Gross profit margin |
|---|---:|---:|---:|
| Toys | $237,440.69 | $50,242 | 21.16% |
| Electronics | $167,092.70 | $80,509 | 48.18% |
| Games | $113,874.34 | $33,033 | 29.01% |
| Sports & Outdoors | $91,289.54 | $23,576 | 25.83% |
| Art & Crafts | $42,181.54 | $11,951 | 28.33% |

Toys had the highest revenue. Electronics had the highest gross profit and gross profit margin. Toys had the lowest category margin.

### Monthly results

| Month | Sales rows | Units sold | Revenue | Gross profit |
|---|---:|---:|---:|---:|
| January 2022 | 29,547 | 38,009 | $542,554.91 | $167,126 |
| February 2022* | 5,954 | 7,710 | $109,323.90 | $32,185 |

\* February includes data only through February 6. These figures do not support a full-month comparison or a seasonal conclusion.

### Inventory and Python analysis

The Python notebook included **849 store-product rows** with both estimated inventory days and gross profit. The correlation was **-0.178**, which indicates a weak negative relationship in this sample. It does not prove that inventory levels cause changes in profit.

The inventory analysis view showed **$198,825** in linked gross profit, compared with **$199,311** in the sales analysis view. The totals differ by $486 because the views do not cover identical row sets. The sales analysis total is used for headline sales results; the inventory view is used for store-product inventory comparisons.

## Dashboard contents

The Power BI dashboard includes:

- Total revenue and gross profit cards
- Revenue and gross profit by product category
- Units sold by product category
- Revenue by month
- Revenue by store location
- Filters for product category, store location, and sale date
- An inventory table with stock, estimated inventory days, gross profit, and store ID

## Recommendations

1. Review the Toys category's lower gross profit margin while considering its high revenue.
2. Protect Electronics profitability and check that important products remain available.
3. Review high inventory-day estimates and products with stock but no recorded sales.
4. Verify physical stock and local demand before changing orders or prices.
5. Repeat the analysis with several complete months of data before making seasonal decisions.
6. Reconcile the $486 gross-profit difference between the sales and inventory analysis views before treating those totals as directly comparable.

## Limitations

- The data covers only 37 days, and February is incomplete.
- Inventory-day values are estimates based on a short period, not long-term forecasts.
- `NULL` inventory-day values mean no sales were recorded in the period; these rows may still be important when investigating slow-moving stock.
- The correlation is descriptive and does not establish cause and effect.
- Gross profit does not include operating expenses.
- The sales and inventory analysis views have a $486 difference in their gross-profit totals.

## How to open the project

- Open `retail_analysis.sql` in MySQL Workbench to review the SQL queries.
- Open `Retail_Inventory_Analysis.ipynb` in Jupyter to review the Python analysis. Keep the notebook in the main project folder and the CSV files in its `data` folder.
- Open `Retail_Business_Performance_Dashboard.pbix` in Power BI Desktop to view or edit the dashboard.
- Open the PDF files to view the exported dashboard and final written report.
