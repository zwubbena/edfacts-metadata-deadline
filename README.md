# EDFacts Metadata Deadline Calculator

A Python-based interactive tool for calculating internal metadata submission deadlines based on federal due dates for EDFacts file specifications.

## Overview

This application implements the **5-Week Federal Deadline Preparation Rule** to ensure adequate processing time for metadata submissions requiring federal review. The tool provides an interactive interface in Google Colab for users to input federal due dates and automatically calculates the corresponding internal submission deadlines.

## Business Rule: 5-Week Federal Deadline Preparation Rule

### Rule Statement

All required submissions must be initiated on or before the first business day preceding a 5-week period before the federal deadline.

### Calculation Method

1. Identify the federal deadline date
1. Calculate the date that is exactly 5 weeks (35 calendar days) before the federal deadline
1. Identify the first business day immediately before this 5-week mark
1. This identified date is the latest allowable submission/initiation date

### Example

- **Federal Deadline:** Monday, March 31, 2025
- **5 weeks before deadline:** Monday, February 24, 2025
- **First business day before the 5-week period:** Friday, February 21, 2025
- **Required submission date:** On or before Friday, February 21, 2025

### Business Day Definition

- Monday through Friday
- Excluding federal holidays
- Excluding weekends

## Features

- **Interactive Interface**: User-friendly input fields for each EDFacts file specification
- **Automatic Calculation**: Computes internal deadlines based on the 5-week rule
- **Business Day Handling**: Accounts for weekends and holidays using numpy’s business day functions
- **Visual Output**: Displays results in a styled table format
- **PDF Generation**: Creates a downloadable PDF report of all calculated deadlines
- **Error Handling**: Gracefully handles invalid date formats

## Supported EDFacts File Specifications

The tool supports the following file specifications:

- FS002 - Children with Disabilities (IDEA) School Age
- FS089 - Children with Disabilities (IDEA) Early Childhood
- FS009 - Children with Disabilities (IDEA) Exiting Special Education
- FS005 - Children with Disabilities (IDEA) Removal to Interim Alternative Educational Setting
- FS006 - Children with Disabilities (IDEA) Suspensions/Expulsions
- FS007 - Children with Disabilities (IDEA) Reasons for Unilateral Removal
- FS088 - Children with Disabilities (IDEA) Disciplinary Removals
- FS143 - Children with Disabilities (IDEA) Total Disciplinary Removals
- FS144 - Educational Services During Expulsion

## Installation

### Prerequisites

- Python 3.x
- Google Colab environment (recommended) or Jupyter Notebook

### Required Libraries

Install the required dependencies:

```bash
!pip install fpdf
```

The following libraries are typically pre-installed in Google Colab:

- `datetime`
- `numpy`
- `pandas`
- `ipywidgets`
- `IPython`

## Usage

1. **Run the Installation**
   
   ```python
   !pip install fpdf
   ```
1. **Execute the Code**
- Copy and paste the entire code into a Google Colab cell
- Run the cell to display the interactive interface
1. **Input Federal Due Dates**
- Enter dates in MM/DD/YYYY format for each file specification
- Leave fields blank for specifications without deadlines
1. **Calculate Deadlines**
- Click the “Calculate Deadlines” button
- View results in the displayed table
1. **Download PDF Report**
- After calculation, a PDF file named `metadata_deadlines.pdf` is generated
- Check the file panel on the left side of Colab to download

## Code Structure

### Main Components

1. **`calculate_internal_metadata_deadline(federal_due_date_str)`**
- Core function that implements the 5-week rule
- Takes a date string in MM/DD/YYYY format
- Returns the calculated internal deadline
- Handles invalid date formats gracefully
1. **Interactive Widgets**
- Text input fields for each file specification
- Submit button to trigger calculations
- Output widget for displaying results
1. **`on_button_click(b)`**
- Event handler for the submit button
- Collects all input dates
- Calculates deadlines for each specification
- Displays results in a styled table
- Generates PDF report
1. **PDF Generation**
- Creates a formatted PDF document
- Includes all file specifications and their deadlines
- Saves to `metadata_deadlines.pdf`

## Example Output

|File Specification                                       |Federal Due Date|Internal Metadata Deadline|
|---------------------------------------------------------|----------------|--------------------------|
|FS002 - Children with Disabilities (IDEA) School Age     |03/31/2025      |02/21/2025                |
|FS089 - Children with Disabilities (IDEA) Early Childhood|04/15/2025      |03/07/2025                |
|…                                                        |…               |…                         |

## Error Handling

- Invalid date formats return “No date entered”
- Empty fields are handled gracefully
- Business day calculations automatically adjust for weekends

## Technical Details

### Date Calculation Logic

```python
federal_due_date = datetime.strptime(federal_due_date_str, "%m/%d/%Y")
five_weeks_prior = federal_due_date - timedelta(weeks=5)
one_day = np.busday_offset(five_weeks_prior.date(), -1, roll='backward')
```

### Business Day Offset

- Uses `numpy.busday_offset` with `roll='backward'` parameter
- Ensures the result is always a valid business day

## Purpose

This tool ensures compliance with federal submission requirements by:

- Providing consistent deadline calculations
- Eliminating manual calculation errors
- Maintaining adequate review periods
- Creating audit trails through PDF reports

## Support

For questions or issues related to:

- **Technical problems**: Check that all dependencies are installed correctly
- **Business rule clarification**: Refer to the rule statement section above
- **Date format issues**: Ensure dates are entered in MM/DD/YYYY format

## License

This tool is designed for internal use in managing EDFacts submissions. Please refer to your organization’s policies regarding data handling and submission procedures.

-----

**Note**: This calculator is specifically designed for EDFacts metadata submissions and implements the organization’s 5-Week Federal Deadline Preparation Rule. Always verify calculated dates against official submission calendars.








# 📊 EDFacts Metadata Deadline Calculator

This interactive Google Colab tool helps users calculate internal metadata submission deadlines for EDFacts File Specifications (FS) based on federal due dates. It follows the internal rule:

> 🗓️ **Internal Deadline = One business day prior to five weeks before the federal deadline**

---

## 🚀 Features

- 9 pre-labeled File Specification (FS) rows
- Compact date input fields (MM/DD/YYYY format)
- Left-aligned results table rendered in Colab
- Automatically calculates internal metadata deadlines
- Generates a downloadable PDF with bolded labels for clarity

---

## 📦 Requirements

This tool runs in **Google Colab** and installs dependencies automatically. No setup required.

---

## ▶️ How to Use

1. Open the notebook in https://colab.research.google.com/.
2. Enter federal due dates for any of the 9 FS rows.
3. Click **"Calculate Deadlines"**.
4. View the results in a formatted table.
5. Download the generated `metadata_deadlines.pdf` from the file panel on the left.

---

## 🧮 Calculation Logic

For each FS entry:
- Subtract 5 weeks from the federal due date.
- Go back one business day (excluding weekends).
- Output the result as the internal metadata deadline.

---

## 📄 PDF Output

The PDF includes:
- Each FS name
- **Bolded** labels for:
  - Federal Due Date
  - Internal Metadata Deadline

---

## 🛠️ Built With

- Python 3
- NumPy
- Pandas
- ipywidgets
- FPDF (for PDF generation)

---

## 📬 Feedback

Feel free to open an issue or submit a pull request if you have suggestions or improvements!
