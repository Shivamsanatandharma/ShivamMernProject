# D-Board
<br>
This SketchFlow App will enable student to draw diagrams and work on the project in the same time.


⚙️ Initial Setup: Virtual Environment
It is a best practice to run Python projects inside a Virtual Environment to keep dependencies (even built-in ones) isolated.

1. Create the Virtual Environment
Open your terminal at the root of this repository (build_challenges/) and run:

Bash
python -m venv venv
2. Activate the Virtual Environment

Windows:

DOS
venv\Scripts\activate
macOS and Linux:

Bash
source venv/bin/activate
(You should now see (venv) at the beginning of your terminal prompt).

🚀 Challenge 1: Producer-Consumer System
A robust, multi-threaded system demonstrating safe concurrent data transfer between threads using Python's threading.Condition (wait/notify mechanics).

Key Features: Enforces strict queue capacity limits, implements Fail-Fast custom exceptions (QueueOverflowError, QueueEmptyError), and ensures graceful thread termination without memory leaks or deadlocks.

Running the Application
Navigate into the project directory and execute the main orchestrator:

Bash
cd ProducerConsumerSystem
python main.py
Expected Output: You will see 20 sample items dynamically generated, enqueued by the Producer, and dequeued by the Consumer, accompanied by real-time queue status updates.

Running the Test Suite
This project includes Unit, Integration, and End-to-End tests utilizing unittest.mock. To run the entire suite:

Bash
python -m unittest discover -s tests
📊 Challenge 2: Sales Analytics Application
A data processing engine utilizing functional programming paradigms (equivalent to Java's Streams API). It dynamically processes multiple CSV datasets to perform aggregations, filtering, and statistical summaries.

Key Features: Implements Python native equivalents for filter(), map(), reduce(), and groupingBy(). Includes dynamic multi-file loading, row-by-row Fail-Fast data validation, and automated JSON report exporting.

Running the Application
Navigate into the project directory (assuming you are at the repository root) and execute the engine:

Bash
cd SalesAnalyticsApplication
python main.py
Expected Output: The application will load all CSVs in the data/ folder, print regional totals, categorical averages, monthly trends, and top performers, and finally save a detailed analytics_summary.json file.

Running the Test Suite
The testing suite isolates the functional map/reduce logic and uses Python's tempfile library to test File I/O exceptions safely without leaving residual files on your machine.

Bash
python -m unittest discover -s tests
🛠️ Tech Stack & Design Principles
Language: Python 3.8+

Dependencies: Zero external libraries. Built entirely with the Python Standard Library (threading, unittest, csv, json, collections, functools).

Architecture: * Strict separation of concerns (Models, Core Logic, Managers).

Domain-specific exception hierarchies for predictable failure states.

Test-Driven Development (TDD) principles applied across all modules.

🛑 Deactivating the Environment
Once you are done reviewing or testing the projects, you can exit the virtual environment by simply typing:

Bash
deactivate
