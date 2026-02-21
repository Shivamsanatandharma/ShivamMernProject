# D-Board
<br>
This SketchFlow App will enable student to draw diagrams and work on the project in the same time.


📊 Sales Analytics Application

A Python-based sales analytics engine that processes multiple CSV datasets and performs advanced aggregations, filtering, grouping, and statistical analysis using a functional-programming approach inspired by the Streams API.

The system is designed to demonstrate modular architecture, clean data modeling, robust exception handling, and stream-style transformations using only Python’s standard library.

🚀 Features

Filter sales by date range, region, or category

Group data by multiple dimensions

Compute totals and statistical summaries

Identify top-performing salespersons

Generate monthly sales trends

Export a structured JSON summary report

Automatic processing of all CSV files in the data/ directory

Fail-fast validation for malformed rows and missing fields

🧠 Functional “Streams API” Approach in Python

Stream-like operations are implemented using Python’s functional tools:

filter() → date/region/category filtering

map() → transforming rows into domain objects

reduce() → global aggregations like revenue totals

defaultdict → grouping and summarization

Single-pass aggregation for efficiency

🗂️ Project Structure
sales_analytics/
├── main.py
├── data/
├── exceptions/
│   └── sales_exceptions.py
├── models/
│   └── sale_record.py
├── core/
│   ├── sales_data_loader.py
│   └── sales_analyzer.py
└── tests/
🧩 Core Classes
SaleRecord

Represents a single transaction with attributes:

transactionId

date

region

salesperson

productCategory

quantity

unitPrice

totalAmount

SalesDataLoader

Loads and validates CSV files

Converts rows into SaleRecord objects

Raises exceptions for file or data issues

SalesAnalyzer

Provides the main analytics operations:

getTotalSalesByRegion()

getAverageSaleByCategory()

getTopSalespersons(n)

getMonthlySalesTrend()

getSalesByDateRange()

generateSummaryReport()

All analytics methods use functional/stream-style processing.

⚠️ Exception Handling

Custom exception hierarchy ensures robust execution:

DataLoadError → file access or missing data files

MalformedDataError → invalid CSV format, types, or headers

Errors include file name and row number for easy debugging.

▶️ Running the Application
Requirements

Python 3.8+

No external dependencies

Run Analytics
python main.py
Run Tests
python -m unittest discover -s tests
📄 Sample Output

The application generates:

data/analytics_summary.json

Containing:

Global revenue

Regional performance

Top salespersons

Monthly trends

Metadata about the report
