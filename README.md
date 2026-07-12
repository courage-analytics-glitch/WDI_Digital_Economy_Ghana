# Ghana's Digital Economy: A Comparative Analysis

Capstone project for the AnalystLab Africa Data Analytics Internship (Batch B, May-July 2026).

## Objective

Measure Ghana's digital economy against 5 regional peers using World Bank World Development Indicators (WDI) data, and identify where Ghana leads or lags on connectivity, digital finance, digital trade, and the relationship between infrastructure and adoption.

## Data Source

World Bank World Development Indicators (WDI), bulk CSV download: https://datatopics.worldbank.org/world-development-indicators/

Raw files are not included in this repository due to file size. Download `WDI_CSV.zip` from the link above to reproduce.

## Indicators Used

- Individuals using the Internet (% of population)
- Mobile cellular subscriptions (per 100 people)
- Fixed broadband subscriptions (per 100 people)
- Secure Internet servers (per 1 million people)
- Account ownership at a financial institution or mobile-money-service provider (% age 15+)
- ICT service exports (% of service exports)
- GDP per capita (current US$)
- Population, total

## Countries Compared

Ghana, Nigeria, Kenya, Cote d'Ivoire, Senegal, South Africa, Sub-Saharan Africa (aggregate), World (aggregate).

## Repository Contents

- `WDI_Digital_Economy_Ghana.pbix` - Power BI dashboard file. Contains the full data cleaning pipeline (Power Query) and all DAX measures.
- `WDI_Digital_Economy_Ghana_Report.pdf` - full report: findings, correlation and trend analysis, dashboard documentation, insights, recommendations.
- `WDI_Digital_Economy_Cleaned.xlsx` - reference copy of the cleaned dataset.
- Dashboard screenshots.

## Data Cleaning (Power Query, inside the .pbix)

All cleaning was performed in Power BI's Power Query Editor, not in an external script:

- Filtered the WDI master CSV down to 10 target indicator codes.
- Unpivoted year columns into a Year/Value pair (wide to long format).
- Fixed data types (Year as whole number, Value as decimal).
- Removed blank/null values and filtered to the 2000-2024 window.
- Merged in Region and Income Group from the WDI country metadata file.
- Renamed indicators to short, dashboard-friendly labels via Replace Values.

## DAX Measures (inside the .pbix)

- Latest Internet Users, Latest Broadband, Latest Mobile Money, Latest ICT Exports (Ghana, 2024)
- IsComparator (calculated column, flags the 6 comparator countries)
- Broadband-Internet Correlation (Pearson correlation, calculated manually via SUMX since DAX has no built-in covariance function)

## Power BI Dashboard

**KPI cards:** Internet Users, Broadband, Mobile Money, ICT Exports (Ghana, 2024), and a Broadband-Internet Correlation coefficient card.

**Charts:**
- Internet Users trend line, 2000-2024
- Fixed Broadband Subscriptions, 2024 snapshot (bar)
- Financial/Mobile Money Account Ownership, 2024 snapshot (bar)
- ICT Service Exports, 2024 snapshot (bar)
- Broadband vs Internet Users scatter plot with trend line
- ICT Service Exports trend, 2000-2024
- GDP per Capita trend, 2000-2024
- Filled world map, Internet Users by country, 2024

**Slicers:** Year (filters every visual), Region and Income Group (scoped to the world map only, by design — Ghana's comparator set spans a single region and income band, so a global slicer that could exclude Ghana would work against the dashboard's purpose).

## Key Findings

1. Ghana leads its comparator group on internet adoption (72.2% in 2024).
2. Ghana ranks second on mobile money and financial account ownership (81.2%), behind Kenya.
3. Ghana has the weakest fixed broadband infrastructure in the comparator group (0.66 per 100 people).
4. Ghana's ICT service exports are the lowest in the group (1.4% of total service exports), and this gap is structural, not recent — the 2000-2024 trend shows it has persisted the entire period.
5. Broadband and internet use are only moderately correlated across the group (r = 0.49); Ghana is an outlier, low broadband, high internet use, confirming its growth is mobile-driven.
6. Ghana's digital indicators outperform what its GDP per capita trend alone would predict.

Full findings, methodology, correlation analysis, and recommendations are in the PDF report.

## Author

Richard Courage Cobbinah. Data analytics professional, Tema, Ghana. LinkedIn: courage-cobbinah-56531255. Kaggle: SetorCourage. GitHub: courage-analytics-glitch.

#AnalystLabAfrica
