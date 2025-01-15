
# Data File Processor

This Python application processes CSV files, converts them to JSON format, and organizes the output based on specified schemas. It supports multiple datasets and is configurable using environment variables.

---

## Features

- Converts CSV files to line-delimited JSON files.
- Maps columns based on dataset-specific schemas.
- Processes multiple datasets automatically.
- Organizes output files into directories by dataset.
- Flexible configuration using environment variables.

---

## Prerequisites

- Python 3.7 or higher
- Required Python packages:
  - `pandas`
  - `python-dotenv`

---

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set Up Environment Variables**:
   - Create a `.env` file in the project directory.
   - Add the following variables:
     ```
     SRC_BASE_DIR=<path_to_source_directory>
     TGT_BASE_DIR=<path_to_target_directory>
     ```

4. **Set Up Schema File**:
   - Place a `schemas.json` file in the source directory.
   - Example `schemas.json` format:
     ```json
     {
         "dataset_name": [
             {"column_name": "column1", "column_position": 1},
             {"column_name": "column2", "column_position": 2}
         ]
     }
     ```

---

## Usage

### Running the Application

To process all datasets defined in `schemas.json`, run:

```bash
python app.py
```

To process specific datasets, provide their names as a JSON array:

```bash
python app.py '["dataset1", "dataset2"]'
```

---

## How It Works

1. **Schema Mapping**:
   - Reads the schema file (`schemas.json`) and maps column names for each dataset.

2. **CSV Processing**:
   - Reads all `part-*` CSV files in the dataset directory.
   - Uses the schema to map columns to their respective positions.

3. **JSON Conversion**:
   - Converts processed data into line-delimited JSON files.
   - Saves JSON files in the target directory under the dataset's folder.

---

### Example Directory Structure

#### Source Directory (`SRC_BASE_DIR`)
```
SRC_BASE_DIR/
├── schemas.json
├── dataset1/
│   ├── part-0000.csv
│   ├── part-0001.csv
├── dataset2/
│   ├── part-0000.csv
```

#### Target Directory (`TGT_BASE_DIR` after processing)
```
TGT_BASE_DIR/
├── dataset1/
│   ├── part-0000.json
│   ├── part-0001.json
├── dataset2/
│   ├── part-0000.json
```

---

## Error Handling

- Logs a warning if no files are found for a dataset.
- Skips datasets with invalid schemas while continuing to process others.

---

## Development

### Testing

Run the script with test datasets to ensure functionality:

```bash
python app.py '["test_dataset"]'
```

### Extending

To add new features or modify behavior:
- **`read_csv`**: Customize the way CSV files are read and preprocessed.
- **`to_json`**: Update the JSON output format as needed.
- **`file_converter`**: Adjust how files are processed.

---

## Contributing

We welcome contributions! To contribute:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes.
4. Submit a pull request.

---

## Contact

For questions, issues, or suggestions, please contact [ahm.rashad.95@gmail.com](mailto:ahm.rashad.95@gmail).
