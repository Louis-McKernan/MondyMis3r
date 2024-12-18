# Solution Design Document: MoneyMis3r

## Objective
To create a Python-based application called MoneyMis3r that allows users to analyze banking transactions from a CSV file. The tool will:
1. Identify re-occurring charges, even if the descriptions vary.
2. Categorize different companies.
3. Retrieve additional information about companies (e.g., websites, contact details).
4. Track specific attributes, such as whether the charge was online or in-person.

---

## Functional Requirements

### Input
1. **CSV File Upload**:
   - The program will accept a CSV file containing transaction data.
   - Expected columns: `Date`, `Amount`, `Description`, `Category`, `Transaction Type` (online or in-person).

### Output
1. **Re-occurring Charges**:
   - Identify charges that occur regularly (e.g., subscriptions).
   - Tolerate variations in descriptions (e.g., Netflix, NETFLX).
2. **Categorization**:
   - Group transactions by merchant, category, and transaction type.
   - Tag merchants as "online" or "in-person" based on the transaction type.
3. **Company Information**:
   - Look up company details (e.g., website, contact info) using a public API (e.g., OpenCorporates or Clearbit).
4. **Summaries and Reports**:
   - Generate summaries showing:
     - Total spending by category.
     - Monthly breakdown of re-occurring charges.
     - Comparison of online vs. in-person transactions.

---

## Non-Functional Requirements
1. **Performance**:
   - Handle CSV files with up to 10,000 transactions efficiently.
2. **Usability**:
   - Provide a command-line interface (CLI) with clear instructions.
3. **Modularity**:
   - Design with extensibility in mind (e.g., adding new analysis features).
4. **Data Privacy**:
   - Ensure sensitive information in the CSV file remains local and is not shared externally.

---

## Architecture

### Modules
1. **File Input Module**:
   - Reads and validates the CSV file.
2. **Data Processing Module**:
   - Cleans and normalizes data (e.g., handling typos in merchant names).
3. **Recurring Charges Module**:
   - Uses pattern matching and fuzzy logic to detect re-occurring charges.
4. **Categorization Module**:
   - Assigns categories based on transaction descriptions.
5. **Company Lookup Module**:
   - Interfaces with external APIs to fetch additional company details.
6. **Reporting Module**:
   - Summarizes data and generates insights.

---

## Technologies
- **Programming Language**: Python 3.9+
- **Libraries**:
  - `pandas`: For data manipulation.
  - `fuzzywuzzy` or `rapidfuzz`: For matching re-occurring charges.
  - `requests`: For API calls.
  - `openpyxl` or `csv`: For handling CSV files.
- **APIs**:
  - OpenCorporates API or Clearbit API for company information.

---

## Workflow
1. User launches the application.
2. Application prompts user to upload a CSV file.
3. The system processes the CSV:
   - Cleans data.
   - Identifies re-occurring charges.
   - Categorizes transactions.
   - Looks up additional information about companies.
4. User views the output:
   - Summaries of transactions.
   - Details about re-occurring charges.
   - Categorization and company information.

---

## Challenges and Considerations
1. **Data Quality**:
   - Inconsistent transaction descriptions may require robust fuzzy matching.
2. **API Rate Limits**:
   - Ensure API requests are within the limits of the chosen service.
3. **Privacy**:
   - Ensure no sensitive user data is leaked when interacting with external APIs.
4. **Extensibility**:
   - Design modules to be reusable and easy to extend.

---

## Next Steps
1. Review and refine requirements.
2. Develop a prototype with basic functionality:
   - CSV upload.
   - Identification of re-occurring charges.
   - Categorization.
3. Expand features incrementally:
   - Company lookup.
   - Advanced reporting.

---

