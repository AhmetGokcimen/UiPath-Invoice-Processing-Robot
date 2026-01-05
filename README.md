# Invoice Processing Automation (UiPath)

This project automates invoice processing workflows by integrating XML-based currency exchange rates, performing data validation, and generating HTML reports.

## 📋 Overview

The robot performs the following operations:
1.  **Data Ingestion:** Reads invoice metadata from `Invoices.xlsx`.
2.  **API Integration:** Fetches real-time EUR/RON exchange rates from the National Bank of Romania (BNR) via HTTP Request (XML).
3.  **Data Processing:**
    * Parses XML response using Regex to extract the `EUR` rate.
    * Validates user input (Type safety & Business logic checks).
    * Normalizes numeric formats using `CultureInfo.InvariantCulture`.
    * Calculates total amounts in local currency.
4.  **Reporting:** Generates a summary HTML table and sends it via SMTP.

## ⚙️ Prerequisites

* **UiPath Studio** (Windows Legacy or Windows compatibility)
* **Microsoft Excel** (for `.xlsx` operations)
* **Internet Access** (Required for `bnr.ro` API endpoint)
* **SMTP Server Access** (Gmail or similar)

## 🔧 Configuration & Setup

Sensitive credentials are **excluded** from the source code for security.

1.  **Clone/Download** the repository.
2.  Open `Main.xaml` in UiPath Studio.
3.  Navigate to the **Variables** panel and configure the following:
    * `str_MyEmail`: Set your sender email address.
    * `str_MyPassword`: Set your App Password (SMTP).
4.  Ensure `Invoices.xlsx` is present in the root directory.

## 📦 Dependencies

* `UiPath.System.Activities`
* `UiPath.Excel.Activities`
* `UiPath.WebAPI.Activities` (For HTTP Request)
* `UiPath.Mail.Activities`

## 📝 Usage

Run the `Main.xaml` file. The process operates as an **Attended Robot**, prompting the user for invoice amounts via a dialog box until the loop is terminated or cancelled.
