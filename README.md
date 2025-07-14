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
