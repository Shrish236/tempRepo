# GDBYantra - 

This repository contains scripts for automating regression tests for SecureIoT projects. The main script compiles all tests, executes them, collects the results, and sends an email with the results in an Excel file. The script also has the capability to send the results to Splunk for further analysis.

## Prerequisites

Before running the script, ensure you have the following libraries installed:

- `re`
- `pandas`
- `openpyxl`
- `pygdbmi`
- `datetime`
- `json`
- `os`
- `requests`
- `random`
- `time`
- `smtplib`
- `ssl`
- `email`
- `collections`
- `makeall`

You can install the required libraries using `pip`:

```bash
pip install pandas openpyxl pygdbmi requests
```

## Configuration

### secureiot_automation_config.json

Create a `secureiot_automation_config.json` file in the root directory with the following structure:

```json
{
    "chip_name": "YourChipName",
    "document_root": "/path/to/documents",
    "file_type": "YourFileType",
    "board_name": "YourBoardName",
    "email_id": ["example1@example.com", "example2@example.com"],
    "splunk_enable": "1",
    "splunk_token": "your-splunk-token",
    "splunk_url": "https://your-splunk-instance.com:8088/services/collector/event"
}
```

## Running the Script

To run the script, simply execute:

```bash
python your_script.py
```

The script will perform the following steps:

1. **Compile All Tests**: Calls the `makeall` module to compile all tests.
2. **Read Configuration**: Reads the configuration from `secureiot_automation_config.json`.
3. **Read Test Data**: Reads test names and IDs from an Excel file.
4. **Execute Tests**: Runs each test using GDB and collects the results.
5. **Generate Results**: Generates an Excel file with the test results.
6. **Send Email**: Sends an email with the test results.
7. **Send Data to Splunk**: Sends the test results to Splunk if enabled.

## Email Configuration

The script uses Gmail to send the email. Ensure you have allowed less secure apps to access your Gmail account or use an app-specific password.

Modify the email configuration in the script:

```python
smtp_server = "smtp.gmail.com"
sender_email = "your-email@gmail.com"
password = "your-email-password"
```

## Example Results

The email sent by the script will contain a summary table and an attached Excel file with detailed results. The summary table includes:

- Project
- Board
- Part ID
- Number of Tests
- Number of Passed Tests
- Number of Failed Tests
- Execution Time

## Splunk Integration

If Splunk integration is enabled, the script will send the test results to the specified Splunk HEC endpoint. Ensure the HEC token and URL are correctly configured in the `secureiot_automation_config.json` file.

## Cleanup

The script will remove the `Results.xlsx` file after sending the email.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

---

Feel free to customize this README file further to better suit your needs.
