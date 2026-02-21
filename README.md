# D-Board
<br>
This SketchFlow App will enable student to draw diagrams and work on the project in the same time.

# Producer-Consumer System

A highly robust, multi-threaded Producer-Consumer system built in Python. This project demonstrates safe concurrent data transfer between threads, strict resource management, and state synchronization using standard `wait/notify` concurrency mechanics.

This project was built with a strong focus on **Problem Decomposition**, **Critical Thinking** (explicit error handling and edge-case management), and **Code Quality**.

## 🚀 Features & Rule Enforcement

* **Strict Capacity Limits:** The shared queue strictly enforces a maximum capacity of 10 items.
* **Thread Synchronization:** * The **Producer** thread safely blocks (waits) when the queue reaches maximum capacity.
  * The **Consumer** thread safely blocks (waits) when the queue is entirely empty.
* **Fail-Fast Exception Handling:** Custom domain-specific exceptions (`QueueOverflowError`, `QueueEmptyError`, `QueueClosedError`) are implemented to handle timeouts and state violations predictably, avoiding infinite hangs or silent data corruption.
* **Graceful Termination:** The system safely broadcasts termination signals (`notify_all()`) to ensure blocked threads wake up and exit cleanly once all data is processed or upon manual interruption (Ctrl+C).
* **Data Persistence:** Automatically formats timestamps for readability and saves the final safely transferred data into a structured `output.json` file.
* **Zero External Dependencies:** Built entirely using Python's standard library (`threading`, `unittest`, `time`, `json`, `datetime`).

## 📁 Project Structure

The codebase is strictly modularized to separate data structures, core threading logic, error handling, and orchestration.

```text
ProducerConsumerSystem/
├── main.py                             # Entry point and demonstration script
├── output.json                         # Generated after a successful run
├── exceptions/
│   ├── __init__.py
│   └── transfer_exceptions.py          # Custom hierarchy for precise error handling
├── models/
│   ├── __init__.py
│   └── item.py                         # Data container (id, data, formatted timestamp)
├── core/
│   ├── __init__.py
│   ├── shared_queue.py                 # Thread-safe queue utilizing condition variables
│   ├── producer.py                     # Source data ingestion thread
│   └── consumer.py                     # Destination data extraction thread
├── managers/
│   ├── __init__.py
│   └── data_transfer_manager.py        # High-level orchestrator for the system
└── tests/
    ├── __init__.py
    ├── test_unit.py                    # Isolated logic and exception tests via Mocks
    ├── test_integration.py             # Thread synchronization tests (wait/notify)
    └── test_e2e.py                     # Black-box lifecycle tests via the Manager

⚙️ Prerequisites & Installation

•	Python 3.13+ is required.
•	No external packages or libraries are required (pip install is not necessary).
Clone or extract the repository, and navigate to the root folder:

Bash
cd ProducerConsumerSystem

💻 Usage

To execute the main demonstration program, run:

Bash
python main.py

Expected Behavior: The script will generate 20 sample items and begin transferring them. Because the queue capacity is 10, you will see the Producer fill the queue and pause, while the Consumer processes the items. The terminal will output real-time queue status updates (e.g., Queue Status: 5/10 items.).
Once all items are processed, the system will shut down gracefully and save the final transferred data to output.json with human-readable timestamps.


🧪 Testing

The system includes a comprehensive, 3-tier testing pyramid to guarantee stability.
To run the entire test suite (Unit, Integration, and End-to-End), execute the following command from the root directory:

Bash
python -m unittest discover -s tests


🏗️ Design Decisions & Architecture

1.	threading.Condition over simple Lock: While a standard Lock provides mutual exclusion, Condition variables provide the exact wait(), notify(), and notify_all() methods required for threads to efficiently communicate changes in the queue's state without aggressive, CPU-heavy polling.
2.	Custom Exception Hierarchy: Standard Python exceptions lack domain context. By creating explicit errors like QueueClosedError, the threads know exactly why an operation failed and how to recover or shut down safely.
3.	Manager Pattern: The DataTransferManager abstracts the complexities of thread management (start(), join(), and cleanup) away from the main application layer, ensuring the high-level API remains clean and misuse-resistant.

