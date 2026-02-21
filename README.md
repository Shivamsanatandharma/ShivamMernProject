# D-Board
<br>
This SketchFlow App will enable student to draw diagrams and work on the project in the same time.
Sales Analytics Application
A robust, functional-programming-driven analytics engine built in Python. This application processes multiple CSV datasets to perform complex aggregations, grouping by multiple dimensions, and statistical summaries.

The project is architected to demonstrate a deep understanding of Functional Streams, Modular Design, and Robust Error Handling.

🛠️ Technical Implementation: "Streams API" in Python
The challenge requirements specified the use of Stream-like operations. This application achieves these using Python's native functional toolkit:

filter() & collect(): Used for date range and regional filtering.

map() & reduce(): Utilized via functools.reduce for calculating global revenue and transforming data objects.

groupingBy() & summarizingDouble(): Implemented using collections.defaultdict for high-performance, single-pass data aggregation and summarization.

📁 Folder Structure

Shutterstock
Explore
Plaintext
sales_analytics/
├── main.py                             # Application entry point & demonstration
├── data/
│   ├── sales_data.csv                  # Quarter 1 Dataset
│   ├── sales_data_q2.csv               # Quarter 2 Dataset
│   └── analytics_summary.json          # Auto-generated analytical report
├── exceptions/
│   ├── __init__.py
│   └── sales_exceptions.py             # Custom domain-specific exceptions
├── models/
│   ├── __init__.py
│   └── sale_record.py                  # Data model with auto-calculated attributes
├── core/
│   ├── __init__.py
│   ├── sales_data_loader.py            # Multi-file I/O & Fail-Fast validation logic
│   └── sales_analyzer.py               # Functional analytics & JSON export engine
└── tests/
    ├── __init__.py
    ├── test_unit.py                    # Isolated logic tests for aggregations
    ├── test_integration.py             # Exception handling & I/O validation tests
    └── test_e2e.py                     # Full lifecycle tests with multiple files
🚀 Key Features
Multi-File Scaling: Automatically scans and processes all .csv files within the data/ directory.

Fail-Fast Data Validation: Row-by-row validation catches malformed data (KeyErrors, ValueErrors) and reports the exact file and row number without crashing the suite.

Rich Analytics:

Total Sales by Region.

Average Sale Price by Product Category.

Top Performers (Ranking by revenue).

Chronological Monthly Sales Trends.

Data Export: Generates a structured, human-readable analytics_summary.json for external system consumption.

⚙️ Prerequisites & Execution
Python 3.8+

Zero external library dependencies: Uses only Python Standard Library (csv, functools, collections, json, datetime, glob).

1. Run the Analytics
Bash
python main.py
2. Run the Test Suite
The project includes a 3-tier testing pyramid using unittest and tempfile.

Bash
python -m unittest discover -s tests
⚠️ Exception Handling
The system implements a custom exception hierarchy to satisfy robustness requirements:

DataLoadError: Raised for file-level issues (File not found, directory access errors).

MalformedDataError: Raised when a CSV row contains invalid types (e.g., text in a quantity column) or missing headers.

📊 Sample JSON Output
The generated analytics_summary.json provides a machine-readable snapshot of the business health:
