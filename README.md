# D-Board
<br>
This SketchFlow App will enable student to draw diagrams and work on the project in the same time.


📊 Sales Analytics Application
A robust, functional-programming-driven analytics engine built in Python. This application processes CSV files containing sales data to perform complex aggregations, grouping by multiple dimensions, and statistical summaries. 



The project is architected to strictly adhere to the challenge requirements, demonstrating a deep understanding of **Functional Streams**, **Modular Design**, and **Robust Error Handling** without relying on heavy external libraries like Pandas.

## 🛠️ Technical Implementation: "Streams API" in Python

The challenge specifies the use of Java-style Stream operations. This application achieves these elegantly using Python's native functional toolkit:
* **`filter()` & `collect()`**: Handled via Python's built-in `filter()` and list comprehensions to isolate specific date ranges.
* **`map()` & `reduce()`**: Utilized via `map()` and `functools.reduce()` for calculating global revenue and transforming data objects.
* **`groupingBy()` & `summarizingDouble()`**: Implemented using `collections.defaultdict` for high-performance, single-pass data aggregation and summarization across dimensions like Region, Category, and Month.

## 📁 Folder Structure

```text
sales_analytics/
├── main.py                             # Application entry point & demonstration
├── data/
│   ├── sales_data.csv                  # Sample Sales Dataset
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
│   └── sales_analyzer.py               # Functional analytics engine
└── tests/
    ├── __init__.py
    ├── test_unit.py                    # Tests isolated map/reduce/filter logic
    ├── test_integration.py             # Tests specific custom exception triggers
    └── test_e2e.py                     # Full lifecycle tests with multiple files

```

## 🚀 Key Features

* **Dynamic Data Loading**: Scans the `data/` directory and aggregates data from multiple `.csv` files automatically.
* **Fail-Fast Data Validation**: Row-by-row validation catches malformed data (missing columns, invalid types) and reports the exact file and row number.
* **Rich Analytics Engine**:
* `getTotalSalesByRegion()`: Calculates revenue grouped by region.
* `getAverageSaleByCategory()`: Computes average transaction values per product category.
* `getTopSalespersons(n)`: Identifies the highest-performing staff dynamically.
* `getMonthlySalesTrend()`: Groups data chronologically to track performance over time.
* `getSalesByDateRange()`: Filters the dataset between two specific dates.


* **Automated Reporting**: Generates a structured, human-readable `analytics_summary.json` for external system consumption.

## ⚙️ Prerequisites & Execution

* **Python 3.8+**
* **Zero external dependencies**: Built entirely using the Python Standard Library (`csv`, `functools`, `collections`, `json`, `datetime`, `glob`).

### 1. Run the Analytics

To execute the application and generate the reports:

```bash
python main.py

```

### 2. Run the Test Suite

The project includes a comprehensive 3-tier testing pyramid (Unit, Integration, End-to-End) utilizing `unittest` and `tempfile` to ensure isolated, reproducible testing.

```bash
python -m unittest discover -s tests

```

## ⚠️ Exception Handling

The system implements a custom exception hierarchy to ensure the application fails gracefully and provides actionable debugging information:

1. **`DataLoadError`**: Raised for file-level issues (e.g., File not found, directory access errors).
2. **`MalformedDataError`**: Raised when a CSV row contains invalid types (e.g., text in a numerical quantity column) or missing data.

```

```
