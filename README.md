# MFDev Scraper SDK

A lightweight Python SDK for web scraping and data processing.  
It provides robust HTTP request handling, data cleaning utilities, and convenient export helpers for CSV and Excel formats.

## Features

- 🚀 **HTTP Requests with Retry Logic**  
  Reliable GET/POST requests with configurable retries, custom error handling, and browser impersonation support (via `curl_cffi`).

- 🛡️ **Custom Exceptions**  
  Clear and descriptive errors for configuration issues, HTTP status mismatches, max retries exceeded, invalid dictionaries, and file I/O errors.

- 🧹 **Data Cleaning**  
  Utility to remove duplicates from lists of dictionaries, with strict or lenient validation modes.

- 📊 **Data Export**  
  Export your data directly to CSV or Excel with built-in helpers.

---

## Installation

You can install directly from source:

```bash
pip install -e .
```

Or once published to PyPI:

```bash
pip install mfdev-scraper
```

---

## Usage

### Basic Example

```python
from mfdev_scraper_sdk import MFDevScraper

scraper = MFDevScraper()

# Perform a GET request
response = scraper.request_mfdev(
    method="GET",
    url="https://httpbin.org/get"
)
print(response.text)

# Clean duplicate records
records = [
    {"id": 1, "name": "Alice"},
    {"id": 1, "name": "Duplicate"},
    {"id": 2, "name": "Bob"}
]
cleaned = scraper.clean_duplicates_dict(records)
print(cleaned)

# Export to CSV
csv_path = scraper.generate_csv(cleaned, "output.csv")
print(f"CSV saved at: {csv_path}")

# Export to Excel
excel_path = scraper.generate_excel(cleaned, "output.xlsx")
print(f"Excel saved at: {excel_path}")
```

---

## Custom Errors

The SDK exposes several custom exceptions you can catch:

- `ConfigurationError`
- `RequestError`
- `HTTPStatusError`
- `MaxRetriesExceeded`
- `InvalidResponseError`
- `DataValidationError`
- `MissingFieldError`
- `NotADictError`
- `FileIOError`
- `CSVWriteError`
- `ExcelWriteError`

---

## Development

Clone the repository and install dependencies:

```bash
git clone https://github.com/yourusername/mfdev-scraper.git
cd mfdev-scraper
pip install -e .
pip install pytest
```

Run tests:

```bash
pytest -q
```

---

## License

This project is licensed under the MIT License.

---

## Author

**Miguel Fernandez**  
Homepage: [https://mfdev.vercel.app](https://mfdev.vercel.app)
