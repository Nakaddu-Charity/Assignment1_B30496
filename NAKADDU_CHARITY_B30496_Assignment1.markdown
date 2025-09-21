# Assignment 1: Descriptive Analytics on IDA Credits to Uganda
**Name**: NAKADDU CHARITY  
**Access Number**: B30496 (S24B38/027)  
**Date**: September 21, 2025  

## 1. Introduction
This report analyzes World Bank International Development Association (IDA) credits to Uganda using the dataset `ida_credits_to_uganda_09-21-2025 (1).csv`, which contains 191 credit records from 1967 to 2025. The analysis was conducted in RStudio, with preprocessing steps including cleaning column names using `make.names`, converting date columns to `Date` format, replacing missing `Board.Approval.Date` values with `Effective.Date..Most.Recent.`, setting monetary amounts for cancelled or terminated credits to zero, and converting monetary columns to numeric format. Non-critical columns, such as `Last.Disbursement.Date` (43 missing values) and `Service.Charge.Rate` (2 missing values), contained missing data but were not used in the analysis. The report addresses three tasks: (1) a time-series analysis of disbursed amounts, (2) a summary of credit status distribution, and (3) an analysis of original principal amounts. Visualizations for each task were generated using `ggplot2` and saved as PNG files for inclusion in this report.

## 2. Task 1: Time-Series Analysis of Disbursed Amount [10 Marks]
**Figure 1: Trend of World Bank Fund Disbursements to Uganda (1967-2025)**  
[Insert `disbursement_trend.png` here: In Microsoft Word, go to Insert > Pictures > This Device, select `disbursement_trend.png` from your working directory]

The time-series plot (Figure 1) illustrates the total `Disbursed.Amount..US..` by year, aggregated from `Board.Approval.Date` and excluding credits with "Fully Cancelled" or "Terminated" status. Key findings include:  
- **Trend**: Disbursements have grown significantly from approximately $10–20 million per year in the 1960s to over $1 billion in the 2020s, reflecting increased IDA support for Uganda’s development.  
- **Patterns**:  
  - **1960s–1970s**: Small disbursements ($10–40M annually) supported foundational projects such as education (e.g., $11.26M for Education I) and road infrastructure.  
  - **1980s–1990s**: Notable spikes occurred in 1984 (~$200M, reconstruction projects) and 1990 (~$300M, economic recovery programs).  
  - **2000s–2010s**: Peaks in 2007 (~$400M, power and policy reforms) and 2010 (~$500M, health and transport sectors).  
  - **2020s**: High disbursements, including $320M for COVID-19 response and urban infrastructure projects, indicate a focus on crisis response and large-scale development.  
- **Statistics**: The mean disbursed amount per credit is approximately $48.7M, with a total of ~$9.3B disbursed across 191 credits (based on dataset summary).  
- **Implications**: The upward trend in disbursements underscores Uganda’s growing reliance on IDA funding for critical development and crisis response, necessitating careful monitoring of repayment capacity.  
**Code**: Data was aggregated using `dplyr::group_by` and `summarise` to compute annual totals, with visualization created using `ggplot2::geom_line` and `geom_point`.

## 3. Task 2: Overall Credit Status Description [10 Marks]
**Figure 2: Distribution of Credit Status for Uganda’s IDA Credits**  
[Insert `credit_status_bar.png` here: In Microsoft Word, go to Insert > Pictures > This Device, select `credit_status_bar.png` from your working directory]

The bar plot (Figure 2) displays the distribution of `Credit.Status` for Uganda’s IDA credits. Key findings from the summary table are:  
- **Summary**:  
  - Fully Repaid: 96 credits (50.3%)  
  - Repaying: 65 credits (34.0%)  
  - Disbursing: 10 credits (5.24%)  
  - Disbursing & Repaying: 8 credits (4.19%)  
  - Fully Cancelled: 4 credits (2.09%)  
  - Approved: 3 credits (1.57%)  
  - Fully Disbursed: 2 credits (1.05%)  
  - Terminated: 2 credits (1.05%)  
  - Effective: 1 credit (0.52%)  
- **Assessment**: Uganda demonstrates a strong repayment history, with 50.3% of credits fully repaid and 44.4% currently active (Repaying, Disbursing, or Disbursing & Repaying). The low percentage of cancellations and terminations (3.14% combined) suggests reliable project implementation.  
- **Patterns**: Older credits (pre-2000) are predominantly repaid, while newer credits focus on modern priorities such as digital infrastructure and climate resilience.  
**Code**: The distribution was calculated using `dplyr::count` with percentage calculations, and visualized using `ggplot2::geom_bar` with the "Paired" color palette for clarity.

## 4. Task 3: Original Principal Amount Analysis [10 Marks]
**Figure 3: Original Principal Amounts Borrowed by Uganda (1967-2025)**  
[Insert `principal_amount_bar.png` here: In Microsoft Word, go to Insert > Pictures > This Device, select `principal_amount_bar.png` from your working directory]

The bar plot (Figure 3) shows the total `Original.Principal.Amount..US..` by year, aggregated from `Board.Approval.Date` and excluding cancelled/terminated credits. Key findings include:  
- **Total Borrowed**: $11,774,030,380 across 191 credits.  
- **Patterns**:  
  - **1960s–1970s**: Small loans ($5–20M annually) for agriculture, education, and infrastructure (e.g., beef ranching, education projects).  
  - **1980s–1990s**: Increased borrowing ($50–100M, e.g., economic recovery programs).  
  - **2000s–2010s**: Significant peaks in 2007 (~$400M, power and policy) and 2010 (~$500M, health and transport).  
  - **2020s**: Large loans exceeding $1B annually, supporting urban development, electricity, and COVID-19 response (e.g., $518M for urban projects).  
  - **Sectoral Shift**: Early credits focused on agriculture and roads, while recent credits support multi-sectoral and climate-focused projects.  
- **Statistics**: The mean principal amount per credit is ~$61.6M, with a maximum of $518M (from dataset summary).  
- **Implications**: The increasing scale of borrowing reflects ambitious development goals but raises concerns about long-term debt sustainability.  
**Code**: Data was aggregated using `dplyr::group_by` and `summarise`, with visualization created using `ggplot2::geom_bar`.

## 5. Conclusion
Uganda’s IDA credits demonstrate a strong repayment history, with 50.3% of credits fully repaid and only 3.14% cancelled or terminated. However, the total borrowed amount of $11.77 billion, with recent increases in loan sizes, highlights growing financial commitments for large-scale projects such as COVID-19 response, urban development, and climate resilience. Effective fiscal management is essential to ensure debt sustainability while meeting development objectives.  
**Source**: World Bank IDA Credits (https://www.worldbank.org/en/data/ida-credits).