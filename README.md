# ReminderEDU

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A comprehensive educational reminder and task management application built with Python, HTML, and CSS. ReminderEDU helps students and educators efficiently organize academic tasks, manage deadlines, and track assignment completion with an intelligent reminder system.

## 📋 Table of Contents

- [Application Description](#application-description)
- [Features](#features)
- [OOP Concepts Used](#oop-concepts-used)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [How to Run](#how-to-run)
- [Running Tests](#running-tests)
- [Export Report](#export-report)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)

## 🎯 Application Description

### Overview
ReminderEDU is an intelligent reminder and task management system designed specifically for educational purposes. It helps students, educators, and learners organize their tasks, manage deadlines, and stay productive with timely notifications and smart task prioritization.

### What This Application Allows Users to Do:

- **✏️ Create & Manage Reminders**: Easily add, edit, and delete academic reminders and assignments with detailed information
- **📅 Schedule Tasks**: Set specific due dates and times for assignments, projects, and study sessions
- **🎓 Subject Organization**: Categorize reminders by subject (e.g., Math, Science, English, History, etc.)
- **🔔 Smart Notifications**: Receive intelligent alerts based on urgency levels and time remaining
- **⏱️ Deadline Tracking**: View time remaining for each task with automated urgency categorization:
  - **Overdue**: Tasks past their due date
  - **Due Soon!**: Tasks due within the next hour
  - **Today**: Tasks due within 24 hours
  - **Upcoming**: Tasks due within 3 days
  - **Planned**: Tasks scheduled for later
- **📊 Task Sorting**: Automatically sort assignments by urgency to prioritize workload
- **💾 Data Persistence**: All reminders are automatically saved and loaded from persistent storage
- **🎨 User-Friendly Interface**: Clean, intuitive, responsive web interface for easy task management
- **📝 Assignment Details**: Store and display assignment name, subject, due date, due time, and time remaining

---

## ✨ Features

- 📝 **Create & Manage Reminders**: Add, edit, and delete reminders with validation
- 📅 **Schedule Tasks**: Set due dates and times with automatic deadline calculations
- 🎓 **Educational Focus**: Tailored for academic and learning environments
- 🔔 **Urgency-Based Sorting**: Smart prioritization based on deadlines
- 📊 **Time Remaining Display**: Shows how much time is left for each task
- 🎨 **User-Friendly Interface**: Clean, intuitive, and responsive design
- 💾 **Persistent Storage**: CSV-based data storage with automatic loading
- ✅ **Input Validation**: Robust error handling and data validation
- 🧪 **Comprehensive Testing**: Full unit test coverage with pytest

---

## 🏗️ OOP Concepts Used

ReminderEDU demonstrates several core Object-Oriented Programming principles:

### 1. **Abstraction**
- **Abstract Base Classes (ABC)**: 
  - `IInputSource` - Abstract interface for input sources
  - `IStorage` - Abstract interface for data persistence
- Hides implementation details while providing clear interfaces

### 2. **Inheritance**
- **Concrete Implementations**:
  - `ManualInputSource` inherits from `IInputSource`
  - `CsvStorage` inherits from `IStorage`
- Allows multiple input and storage strategies without changing core logic

### 3. **Encapsulation**
- **Private Attributes**: Uses underscore prefix (`_name`, `_subject`, `_due_datetime`, `_id`)
- **Property Decorators**: Implements getters and setters for controlled access:
  ```python
  @property
  def name(self):
      return self._name
  
  @name.setter
  def name(self, value):
      # Validation logic
  ```
- Protects data integrity and allows validation

### 4. **Polymorphism**
- **Interface Implementation**: Different input sources and storage mechanisms can be used interchangeably
- `ScheduleManager` works with any `IInputSource` or `IStorage` implementation
- Enables flexible architecture and easy extensibility

### 5. **Composition**
- `ScheduleManager` **contains** a `CsvStorage` object
- `ManualInputSource` **contains** form data
- Objects are composed of other objects to build complex behavior

### 6. **Single Responsibility Principle**
- `Assignment` - Represents a single task
- `ManualInputSource` - Handles manual input
- `CsvStorage` - Manages file I/O
- `ScheduleManager` - Orchestrates operations

---

## 🛠️ Technologies Used

| Technology | Version | Purpose |
|-----------|---------|---------|
| **Python** | 3.7+ | Backend logic, server, core functionality, and CLI |
| **Flask** | Latest | Lightweight web framework for routing and request handling |
| **CSV** | Built-in | Data persistence and storage format |
| **HTML5** | Latest | Structure and markup for web interface |
| **CSS3** | Latest | Styling and responsive user interface design |
| **pytest** | Latest | Unit testing and test automation |

### Language Distribution
- **Python**: 45.7% - Backend logic, server, and core functionality
- **CSS**: 31.6% - Styling and user interface design
- **HTML**: 22.7% - Structure and markup

### Key Libraries & Modules
- `flask` - Web framework
- `csv` - Data file handling
- `os` - File system operations
- `datetime` - Date and time operations
- `abc` - Abstract base classes for interfaces
- `pytest` - Testing framework

---

## 📁 Project Structure

```
ReminderEDU/
├── README.md                    # Project documentation
├── app.py                        # Flask application & routing
├── core_logic.py                 # Core business logic and data models
├── test_logic.py                 # Unit tests
├── requirements.txt              # Python dependencies
├── schedule.csv                  # Data storage (auto-generated)
├── static/                       # Static assets
│   ├── css/
│   │   └── style.css            # Application styling
│   └── js/
│       └── script.js             # Frontend JavaScript
└── templates/                    # HTML templates
    ├── base.html                # Base template with layout
    ├── index.html               # Main dashboard
    └── reminder_detail.html      # Individual reminder view
```

### Key Files Description

**core_logic.py** - Business Logic & Data Models
- `IInputSource` (ABC) - Abstract interface for input sources
- `IStorage` (ABC) - Abstract interface for storage mechanisms
- `Assignment` - Represents a single assignment/reminder with properties and validation
- `ManualInputSource` - Implements manual form-based input
- `CsvStorage` - Implements CSV file-based persistence
- `ScheduleManager` - Orchestrates all operations and manages the assignment collection

**app.py** - Flask Application
- Sets up Flask routes for web interface
- Manages HTTP requests and responses
- Integrates `ScheduleManager` with web endpoints
- Handles task creation and deletion through web interface

**test_logic.py** - Unit Tests
- Tests assignment validation and creation
- Tests CSV save/load functionality
- Tests manager operations (add, discard, sort)

---

## 🚀 How to Run

### Prerequisites

- **Python 3.7** or higher
- **pip** (Python package manager)
- A modern web browser (Chrome, Firefox, Safari, Edge)
- **Git** (for cloning the repository)

### Installation Steps

#### 1. Clone the Repository

```bash
git clone https://github.com/LyCheaa/ReminderEDU.git
cd ReminderEDU
```

#### 2. Create a Virtual Environment (Recommended)

```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

#### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

If `requirements.txt` doesn't exist, install manually:
```bash
pip install flask pytest
```

#### 4. Navigate to the Folder

```bash
cd ReminderEDU
```

Verify the following files are present:
- `app.py`
- `core_logic.py`
- `test_logic.py`
- `templates/` directory
- `static/` directory

#### 5. Run the Application

```bash
# Option 1: Direct Flask execution
python app.py

# Option 2: Using Flask CLI
flask run
```

You should see output similar to:
```
WARNING in app.run() This is a development server. Do not use it in production.
* Running on http://127.0.0.1:5000
* Debug mode: on
```

#### 6. Access the Application

Open your web browser and navigate to:
```
http://localhost:5000
```

You should see the ReminderEDU dashboard where you can:
- View all your reminders sorted by urgency
- Add new assignments/reminders
- Delete completed assignments
- See time remaining for each task

---

## 🧪 Running Tests

### Run All Tests

```bash
pytest test_logic.py -v
```

The `-v` flag provides verbose output showing each test result.

### Run Specific Test

```bash
# Test assignment validation
pytest test_logic.py::test_assignment_validation -v

# Test CSV save/load
pytest test_logic.py::test_csv_save_and_load -v

# Test manager discard functionality
pytest test_logic.py::test_manager_discard -v
```

### Run with Coverage Report

```bash
pip install pytest-cov
pytest test_logic.py --cov=core_logic --cov-report=html
```

This generates an HTML coverage report in `htmlcov/index.html`

### Expected Test Output

```
test_logic.py::test_assignment_validation PASSED      [ 33%]
test_logic.py::test_csv_save_and_load PASSED          [ 66%]
test_logic.py::test_manager_discard PASSED            [100%]

========================= 3 passed in 0.XX s ==========================
```

### Test Descriptions

| Test | Purpose |
|------|---------|
| `test_assignment_validation` | Verifies Assignment creation with valid data and rejects invalid date formats |
| `test_csv_save_and_load` | Ensures CSV storage correctly saves and loads assignment data |
| `test_manager_discard` | Tests the ability to delete assignments and verify persistence |

---

## 📊 Export Report

### Generating Test Reports

#### 1. Generate Coverage Report

```bash
pytest test_logic.py --cov=core_logic --cov-report=term-missing
```

Output example:
```
Name           Stmts   Miss  Cover   Missing
--------------------------------------------
core_logic.py   120     8     93%    45, 67, 89-90
--------------------------------------------
TOTAL           120     8     93%
```

#### 2. Generate HTML Coverage Report

```bash
pytest test_logic.py --cov=core_logic --cov-report=html
```

This creates an `htmlcov/` directory. Open `htmlcov/index.html` in your browser to view a detailed coverage report.

#### 3. Generate XML Report (for CI/CD)

```bash
pytest test_logic.py --junit-xml=report.xml
```

#### 4. Generate JSON Report

```bash
pytest test_logic.py --json-report --json-report-file=report.json
```

#### 5. View Test Results with Verbose Output

```bash
pytest test_logic.py -v --tb=short > test_report.txt
```

This saves a detailed report to `test_report.txt`

### Interpreting Reports

- **Coverage %**: Percentage of code executed by tests (aim for >90%)
- **Missing Lines**: Lines that tests don't execute
- **Passed/Failed**: Number of tests that passed or failed
- **Execution Time**: How long each test took to run

### CSV Data Export

The application automatically exports data to `schedule.csv` in the following format:

```csv
id,name,subject,due_date,due_time
1,Midterm Exam,Math,2026-06-15,14:00
2,Research Paper,English,2026-06-10,23:59
3,Lab Report,Science,2026-05-25,17:00
```

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Steps to Contribute

1. **Fork the repository**
   ```bash
   git clone https://github.com/LyCheaa/ReminderEDU.git
   cd ReminderEDU
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make your changes**
   - Write clean, readable code
   - Follow PEP 8 style guide
   - Add comments where necessary
   - Follow the existing code structure

4. **Add/Update Tests**
   ```bash
   pytest test_logic.py -v
   ```

5. **Commit your changes**
   ```bash
   git commit -m "Add: Brief description of your feature"
   ```

6. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Create a Pull Request**
   - Describe your changes clearly
   - Link any related issues
   - Ensure all tests pass

---

## 📄 License

This project is licensed under the **MIT License** - see the LICENSE file for details.

### MIT License Summary

```
Copyright (c) 2026 LyCheaa

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

## 🤗 Support

Have questions or encountered an issue? Here are some ways to get help:

- **Open an Issue**: [Create an issue on GitHub](https://github.com/LyCheaa/ReminderEDU/issues)
- **Check Documentation**: Review this README for troubleshooting
- **Contact Maintainer**: Reach out to the project maintainer

### Troubleshooting

| Issue | Solution |
|-------|----------|
| `ModuleNotFoundError: No module named 'flask'` | Run `pip install -r requirements.txt` |
| `Port 5000 already in use` | Run `flask run --port 5001` or kill the process using port 5000 |
| `CSV file not found` | Application auto-creates `schedule.csv` on first run |
| `Tests fail` | Ensure Python 3.7+ and pytest are installed: `pip install pytest` |

---

## 🚦 Roadmap

- [ ] Mobile app version
- [ ] Email/SMS notifications
- [ ] Recurring reminders
- [ ] Collaboration features (shared assignments)
- [ ] Dark mode UI
- [ ] Calendar integration
- [ ] Analytics dashboard enhancements
- [ ] Database migration (PostgreSQL/MongoDB)
- [ ] User authentication system
- [ ] REST API endpoints

---

## 📈 Project Statistics

- **Total Tests**: 3
- **Test Coverage**: ~93%
- **Code Lines**: 175+ (core logic)
- **Languages**: Python, HTML, CSS
- **OOP Principles Implemented**: 6

---

**Made with ❤️ by LyCheaa**

Happy reminding! 🎉
