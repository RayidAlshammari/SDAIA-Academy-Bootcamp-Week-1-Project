# CSV Profiler
**Version:** 1.0.2

**Week 1 Project - SDAIA Academy Bootcamp**

A comprehensive CSV analysis tool that provides statistical profiling with both CLI and GUI interfaces.

## Project Overview

This tool analyzes CSV files and generates detailed statistical reports including data types, missing values, and statistics for both numeric and text columns.

## Project Structure

```
bootcamp/
├── app.py                    # Streamlit web interface (simple & inline)
├── src/csv_profiler/
│   ├── io.py                 # CSV file reading
│   ├── profiling.py          # Core analysis (6 functions)
│   ├── render.py             # Report formatting
│   └── cli.py                # CLI interface
├── data/                     # Sample CSV files
├── outputs/                  # Generated reports
├── requirements.txt          # Dependencies
└── pyproject.toml           # Package config
```

## Data Flow

```
Entry Points:
  - CLI (Typer)      ─┐
  - GUI (Streamlit)  ─┤
                     └──→ [IO → Profiling → Render]
                                           │
                           ┌───────────────┴──────────┐
                           │                          │
                  CLI: Save files         GUI: Display & Download
```

## Core Functions

The project contains 6 core functions in `profiling.py`:

1. **`is_missing(value)`** - Detects missing values (empty, "na", "null", etc.)
2. **`try_float(value)`** - Safely converts values to float
3. **`infer_type(values)`** - Determines column type (number/text)
4. **`numeric_stats(values)`** - Calculates min, max, mean for numeric columns
5. **`text_stats(values)`** - Counts top values for text columns
6. **`profile_csv(rows)`** - Main profiling function that orchestrates the analysis

## Features

- Automatic data type detection (numeric/text)
- Missing value detection with multiple patterns
- Statistical analysis per column type
- Dual interfaces: CLI and Web GUI
- Export formats: JSON and Markdown

## Installation

Install required dependencies:

```bash
pip install -r requirements.txt
```

For development install (makes `csv-profiler` command available):

```bash
pip install -e .
```

## Usage

### CLI Commands

**Simple and easy:**
```bash
# Basic analysis (run from bootcamp directory)
csv-profiler profile data/saudi_shopping_with_missing.csv

# Show results in terminal
csv-profiler profile data/saudi_shopping_with_missing.csv --show

# Custom output and name
csv-profiler profile data/saudi_shopping_with_missing.csv -o my_reports -n analysis

# Using absolute path (analyze any file on your computer)
csv-profiler profile /Users/yourname/Documents/mydata.csv

# Show version
csv-profiler version
```

**💡 Tip:** You can use either relative paths (when in project directory) or absolute paths (from anywhere on your computer)!

**Quick reference:**
- `csv_file` - Path to CSV file (absolute or relative)
- `-o, --output` - Output directory (default: outputs)
- `-n, --name` - Report name (default: report)
- `-s, --show` - Display results in terminal
- `--help` - Show help

### Web Interface (Streamlit)

```bash
streamlit run app.py
```

Opens web interface at `http://localhost:8501`

**GUI Features:**
1. Upload CSV file via sidebar
2. Preview first 10 rows
3. Click "Generate Profile" button
4. View results in interactive tables

## Output

**CLI Output:**
- Saves `report.json` and `report.md` to specified output directory
- Optional verbose table displayed in terminal

**GUI Output:**
- Interactive display of profile results
- Downloadable JSON and Markdown reports
- Real-time preview of data

---

**Author:** SDAIA Academy Bootcamp Student : Rayid Alshammari

**Project:** Week 1 Project
