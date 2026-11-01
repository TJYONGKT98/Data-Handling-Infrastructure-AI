# Irish Residential Mortgage Arrears -- Forecasting Trends

## 1. Project Overview

This project explores trends in Irish residential mortgage arrears and
repossessions using publicly available statistics from the Central Bank
of Ireland (CBI). It focuses on developing an **early-warning / arrears
detection approach** and analysing repossession trends.

The project considers how quarterly forecasts and early-warning
indicators could support portfolio-level monitoring. The forecast and
its uncertainty range are intended to be used as trend indicators
alongside an organisation's own loan-level information, rather than as a
substitute for individual loan assessment.

## 2. Project Objectives

The main objectives are to:

-   Examine historical residential mortgage arrears and repossession
    trends in Ireland.
-   Explore whether the available data can support an early-warning
    indicator for future arrears trends.
-   Read the next-quarter forecast and early-warning flag as inputs to a
    quarterly portfolio review, alongside an organisation's own
    loan-level data.
-   Use the forecast and its uncertainty range as trend indicators to
    monitor systemic stability, support compliance monitoring and help
    identify economic risks at an earlier stage.

**Important:** The analysis is based on aggregate published statistics.
It should not be interpreted as a borrower-level arrears decision or as
a replacement for a lender's internal credit-risk processes.

## 3. Dataset

The project uses the Central Bank of Ireland's *Residential Mortgage
Arrears and Repossession Statistics*, published through
[data.gov.ie](https://data.gov.ie/).

  -----------------------------------------------------------------------
  Item                                Description
  ----------------------------------- -----------------------------------
  Dataset file                        `moa-open-data.csv`

  Source                              Central Bank of Ireland /
                                      data.gov.ie

  Approximate size                    20,000 rows

  Data type                           Published residential mortgage
                                      arrears and repossession statistics
  -----------------------------------------------------------------------

The dataset should be obtained from the original publisher. Check the
source page for the latest release and metadata before reproducing the
analysis, as the published data may be updated.

If the dataset is not included in this repository, download
`moa-open-data.csv` from the source and upload it to the location
expected by the notebook. Update the notebook's data path if necessary.

## 4. Repository Contents

The repository currently includes the following files:

``` text
Data-Handling-Infrastructure-AI/
├── 20122703_Sprint1_Trendforecast.ipynb
├── DATA_CARD.md
├── metadata.json
└── README.md
```

The Sprint 1 notebook is the main entry point currently listed in the
repository. The EDA outputs are reported to be in
`20122703_Sprint2_EDA.ipynb`; add that notebook to the repository and
update this section with its exact filename/location if it is part of
the final submission.

## 5. Technologies and Libraries

-   **Language:** Python
-   **Development environment:** Google Colab
-   **Libraries used:**
    -   `numpy`
    -   `pandas`
    -   `scipy`
    -   `matplotlib`
    -   `seaborn`
    -   `statsmodels`
    -   `sys` (Python standard library)

The exact package versions have not yet been pinned. For a more
reproducible environment, record the Python and package versions used
for the final run and add them to a `requirements.txt` file.

## 6. Installation and Setup

No special setup has been identified beyond access to Google Colab, the
notebook and the dataset.

1.  Open [Google Colab](https://colab.research.google.com/).
2.  Download or clone this repository, or upload the relevant notebook
    to Google Colab.
3.  Obtain `moa-open-data.csv` from the source described in
    [Dataset](#3-dataset).
4.  Upload the CSV to the location referenced in the notebook, or change
    the notebook's file path to match its location.
5.  If any required library is missing, install it in the Colab
    environment. For example:

``` python
%pip install numpy pandas scipy matplotlib seaborn statsmodels
```

## 7. How to Run the Project

Start with:

[`20122703_Sprint1_Trendforecast.ipynb`](https://github.com/TJYONGKT98/Data-Handling-Infrastructure-AI/blob/main/20122703_Sprint1_Trendforecast.ipynb)

Open the notebook in Google Colab and execute the cells in order, from
the beginning. Ensure the dataset is available at the path expected by
the notebook before running the data-loading cells.

The EDA notebook is identified as `20122703_Sprint2_EDA.ipynb`. Once it
has been added to the repository, include a direct link here and run it
after the relevant data preparation steps.

## 8. Outputs

The project includes analysis and visualisation outputs in the
notebooks. The EDA outputs are located in `20122703_Sprint2_EDA.ipynb`
according to the project information supplied.

Document the exact outputs generated by the final notebook run here (for
example, charts, summary tables, forecast values, uncertainty intervals
or exported CSV files). Do not list an output unless it is actually
generated by the submitted notebook.

## 9. Reproducibility

To reproduce the analysis:

1.  Use the notebook and dataset versions included with, or linked from,
    this repository.
2.  Use Google Colab and install the required libraries.
3.  Confirm the dataset file path used by the notebook.
4.  Run all notebook cells in order.
5.  Compare the regenerated tables, charts and forecast outputs with the
    saved notebook outputs.

For stronger reproducibility, the final submission should also:

-   Record the Python and library versions used.
-   Keep data-loading paths and setup instructions clear.
-   Record the dataset source and download/access date.
-   Ensure that all required notebooks and supporting files are
    committed to the repository.
-   Record any random seeds and forecasting settings, where applicable.
-   Avoid relying on temporary files or files stored only in a personal
    Google Drive.

Because the source dataset may be updated by its publisher,
reproductions should use the same dataset release as the original
analysis where possible.

## 10. Key Findings

Add a short summary of three to five findings from the completed EDA and
forecasting work. Each finding should be supported by a table, chart or
result in the submitted notebooks.

-   **Finding 1:** \[Add a verified finding and refer to the relevant
    notebook output.\]
-   **Finding 2:** \[Add a verified finding and refer to the relevant
    notebook output.\]
-   **Finding 3:** \[Add a verified finding and refer to the relevant
    notebook output.\]

Do not fill this section with expected or hypothetical results. Use only
findings confirmed by the analysis.

## 11. Limitations

Document the limitations that apply to the completed analysis. Consider
whether:

-   The published statistics are aggregate data and do not provide the
    full detail of individual borrowers or loan-level circumstances.
-   The dataset covers a particular reporting period and may not capture
    future economic or policy changes.
-   Forecasts are estimates and are subject to uncertainty; actual
    future values may differ.
-   Changes in definitions, reporting practices or dataset releases
    could affect comparisons over time.
-   The analysis is intended as a monitoring aid and should not be
    treated as a definitive repossession or borrower-level risk
    decision.

Retain only the limitations that are relevant to the dataset and methods
actually used, and add any project-specific limitations identified
during the analysis.

## 12. Responsible Use of AI

Generative AI (Claude) was used as an assistance tool during the
project for proofreading and writing suggestions, comparing
interpretations during EDA, debugging code, suggesting code comments and
recommending possible EDA tests.

AI suggestions were reviewed against the dataset, code execution and the
project's objectives before use. The author remains responsible for the
submitted code, analysis, interpretations and conclusions.

## 13. Data and Usage Notes

The dataset is attributed to the Central Bank of Ireland and is made
available through data.gov.ie. Consult the original dataset page for its
current licence, attribution requirements and any conditions on reuse.
Do not include confidential or personal data in the repository.

------------------------------------------------------------------------

## Project Repository

[Data-Handling-Infrastructure-AI on
GitHub](https://github.com/TJYONGKT98/Data-Handling-Infrastructure-AI)
