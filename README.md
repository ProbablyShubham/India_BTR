# India BTR-1 GHG Inventory Dashboard

An interactive dashboard for exploring India's greenhouse gas inventory reported under its **First Biennial Transparency Report (BTR-1)** to the UNFCCC.

The dashboard converts India's Common Reporting Tables (CRTs) for **2005, 2020, 2021, and 2022** into an accessible analytical interface with sectoral trends, greenhouse-gas breakdowns, Sankey diagrams, key-category analysis, LULUCF removals, downloadable charts, and exportable underlying data.

## Overview

India's BTR-1 contains a detailed national greenhouse gas inventory covering:

* Energy
* Industrial Processes and Product Use (IPPU)
* Agriculture
* Land Use, Land-Use Change and Forestry (LULUCF)
* Waste

The official CRT workbooks contain substantially more detail than is practical to explore manually across multiple Excel sheets and reporting years. This project restructures the reported data into a single interactive dashboard intended for researchers, policymakers, analysts, journalists, students, climate practitioners, and anyone working with India's national GHG inventory.

The dashboard is designed to preserve the structure and reporting conventions of the official inventory rather than treating the CRTs as a generic emissions dataset.

## Dashboard

The main application is:

```text
India_BTR1_GHG_Inventory_Dashboard.html
```

It is a self-contained HTML dashboard and can be opened directly in a modern browser.

No server is required for basic use.

## Main Features

### National inventory overview

The dashboard provides headline indicators for:

* Gross national GHG emissions excluding LULUCF
* Net national emissions including LULUCF
* LULUCF removals
* Sector contributions
* Changes between reporting years
* 2005–2022 changes
* Relative sector shares

### Time-series analysis

Compare reported inventory values for:

```text
2005
2020
2021
2022
```

Views include:

* Total emissions
* Net emissions
* Sector-level trends
* Category-level trends
* Gas-level trends
* Absolute change
* Percentage change

Note that these are the inventory years reported in BTR-1 and should not be interpreted as a continuous annual time series.

### Sectoral breakdowns

Interactive exploration is available for:

* Energy
* IPPU
* Agriculture
* LULUCF
* Waste

Users can move from national totals into progressively more detailed IPCC/CRT categories.

### GHG-wise analysis

The dashboard includes analysis by greenhouse gas, including:

* CO2
* CH4
* N2O
* HFCs
* PFCs
* SF6

Where available in the CRT data, more detailed fluorinated-gas information is retained.

### Sankey diagrams

Sankey visualizations help explain the structure of the inventory through flows such as:

```text
National inventory
    ↓
Sector
    ↓
Sub-sector / category
```

Additional views show relationships between sectors and greenhouse gases.

Because LULUCF includes removals and Sankey diagrams generally represent positive flows, signed LULUCF emissions/removals are also presented separately in dedicated charts.

### Key-category analysis

The dashboard includes India's reported 2022 key-category analysis:

* Excluding LULUCF
* Including LULUCF

The interface highlights the categories contributing most strongly to the national inventory and displays cumulative shares.

India applied **IPCC Approach 1 Level Assessment** and used an **85% cumulative threshold** under the flexibility provisions reported in BTR-1.

### LULUCF analysis

Land-sector values are treated as signed emissions/removals.

This is important because categories including forest land, cropland, settlements, and harvested wood products can represent carbon removals rather than emissions.

The dashboard therefore avoids interpreting negative LULUCF values as missing data or converting them to positive emissions.

### CRT notation keys and completeness

Official inventory notation keys are retained where they occur.

These include:

| Code | Meaning            |
| ---- | ------------------ |
| `NO` | Not Occurring      |
| `NE` | Not Estimated      |
| `NA` | Not Applicable     |
| `IE` | Included Elsewhere |
| `C`  | Confidential       |

These values are **not automatically interpreted as zero**.

This distinction matters when analysing completeness, comparing categories, or aggregating inventory values.

### Data explorer

A searchable table allows users to inspect normalized CRT records directly.

Depending on the record, fields can include:

* Reporting year
* Sector
* IPCC / CRT category
* Category name
* Gas
* Reported value
* CO2-equivalent value
* Reporting notation
* Source table

This is useful for validating charts or conducting more detailed analysis outside the predefined visualizations.

## Downloads and Exports

The dashboard supports exporting analytical outputs for further use.

Available functionality includes:

* Download chart as PNG
* Export chart data as CSV
* Export normalized inventory data
* Export dashboard data as JSON
* Browser print / Save as PDF

Associated files in this repository may include:

```text
India_BTR1_GHG_Inventory_Dashboard.html
crt_summary2.csv
India_BTR1_Dashboard_Data.json
```

## Source Data

The quantitative inventory is derived from India's official BTR-1 Common Reporting Tables for:

```text
BTR1_CRT_2005_All Sectors_INDIA.xlsx
BTR1_CRT_2020_All Sectors_INDIA.xlsx
BTR1_CRT_2021_All Sectors_INDIA.xlsx
BTR1_CRT_2022_All Sectors_INDIA.xlsx
```

Additional context, definitions, methodological notes, caveats, and inventory explanations were drawn from:

```text
NID_BTR1_INDIA
BTR1_INDIA
```

The **National Inventory Document (NID)** is particularly important for interpreting methodology, uncertainty, completeness, QA/QC, key categories, notation keys, and flexibility provisions.

## Units

Inventory data may appear in several units in the source CRTs.

The dashboard generally presents national and sector-level CO2-equivalent values in:

```text
MtCO2e
```

where:

```text
1 Mt = 1,000 Gg
```

Detailed source tables may retain reported units where appropriate.

Users exporting data should verify the unit field before conducting additional calculations.

## Global Warming Potentials

India's BTR-1 inventory uses **100-year Global Warming Potentials from the IPCC Fifth Assessment Report (AR5)** for conversion to CO2-equivalent emissions.

Examples include:

| Gas      | GWP100 |
| -------- | -----: |
| CO2      |      1 |
| CH4      |     28 |
| N2O      |    265 |
| HFC-32   |    677 |
| HFC-125  |  3,170 |
| HFC-134a |  1,300 |
| SF6      | 23,500 |
| CF4      |  6,630 |
| C2F6     | 11,100 |

Users comparing this inventory with datasets using AR4, AR6, or other GWP conventions should account for methodological differences.

## Important Caveats

### Reported years are not a complete annual series

BTR-1 reports inventory data for 2005, 2020, 2021, and 2022.

A line connecting these points visually represents the change between reported inventory years and does not imply that intermediate annual inventory estimates are available.

### LULUCF requires signed interpretation

Negative values generally represent net removals.

Gross emissions excluding LULUCF and net emissions including LULUCF answer different analytical questions and should not be used interchangeably.

### Notation keys are not zeros

`NO`, `NE`, `NA`, `IE`, and `C` each have specific meanings under inventory reporting rules.

Treating them all as zero can create incorrect totals or misleading completeness assessments.

### Aggregation can create double counting

CRT tables contain hierarchical categories.

For example:

```text
Energy
└── Fuel combustion
    └── Energy industries
        └── Public electricity and heat production
            └── Electricity generation
```

Adding a parent category and its children together would double count emissions.

The dashboard uses hierarchy-aware views, but users exporting data should take care when performing independent aggregation.

### Memo items

Certain reported items, including international bunker emissions, may be reported as memo items and are not necessarily included in national inventory totals.

Their treatment should follow the official CRT structure.

### GWP basis matters

CO2-equivalent values are dependent on the GWP framework used.

Comparisons with other inventories should confirm whether AR5 GWP100 values are being used.

### Official-source discrepancies

Some narrative or summary percentage-change values in the BTR/NID may not perfectly match percentages calculated directly from the reported underlying values.

Where possible, this dashboard derives analytical indicators from the reported CRT values rather than manually reproducing summary percentages.

The original Government of India submission remains the authoritative source.

## Example Headline Results

For 2022, BTR-1 reports approximately:

```text
Gross emissions excluding LULUCF:
3,396 MtCO2e

Net emissions including LULUCF:
2,825 MtCO2e

Net LULUCF:
approximately -572 MtCO2e
```

Energy is the dominant emitting sector, while LULUCF acts as a substantial net carbon sink.

The dashboard should be used to investigate the detailed category structure underlying these headline numbers.

## Running Locally

Clone the repository:

```bash
git clone <repository-url>
cd <repository-folder>
```

Open:

```text
India_BTR1_GHG_Inventory_Dashboard.html
```

in Chrome, Firefox, Edge, Safari, or another modern browser.

Alternatively, run a simple local server:

```bash
python -m http.server 8000
```

Then navigate to:

```text
http://localhost:8000/India_BTR1_GHG_Inventory_Dashboard.html
```

## GitHub Pages

The dashboard can be hosted directly using GitHub Pages.

A simple setup is:

1. Push the repository to GitHub.
2. Open **Settings → Pages**.
3. Choose **Deploy from a branch**.
4. Select the relevant branch and repository root.
5. Save.

For a cleaner public URL, the dashboard file can be renamed:

```text
index.html
```

GitHub Pages will then load the dashboard at the root of the site.

## Repository Structure

A minimal repository may look like:

```text
.
├── README.md
├── index.html
├── crt_summary2.csv
├── India_BTR1_Dashboard_Data.json
└── source/
    ├── BTR1_CRT_2005_All Sectors_INDIA.xlsx
    ├── BTR1_CRT_2020_All Sectors_INDIA.xlsx
    ├── BTR1_CRT_2021_All Sectors_INDIA.xlsx
    ├── BTR1_CRT_2022_All Sectors_INDIA.xlsx
    ├── NID_BTR1_INDIA.txt
    └── BTR1_INDIA.txt
```

Before redistributing source files, confirm any applicable terms or conditions associated with the original documents.

## Potential Extensions

Possible future additions include:

* Additional BTR inventory years
* Comparison with India's National Communications and BUR inventories
* Recalculation tracking between submissions
* State-level emissions datasets where comparable data exist
* Activity-data dashboards
* Emission-factor explorer
* Methodology / Tier mapping
* Category-level uncertainty visualizations
* QA/QC and planned-improvement tracker
* NDC progress indicators
* Emissions-intensity indicators
* Population and GDP normalization
* Policy-to-inventory category mapping
* Cross-country CRT comparison

## Intended Use

This project is intended for:

* Climate-policy analysis
* National GHG inventory research
* Transparency-framework analysis
* Sectoral emissions research
* Academic and teaching use
* Data journalism
* NDC and mitigation analysis
* Inventory QA/QC exploration
* Climate-data visualization

It is an analytical interface to officially reported information, **not an alternative national inventory**.

## Citation

When using results from this dashboard, users should cite the original Government of India BTR-1 and National Inventory Document.

Suggested source citation:

> Ministry of Environment, Forest and Climate Change, Government of India. *India: First Biennial Transparency Report to the United Nations Framework Convention on Climate Change*. 2025.

For inventory methodology and detailed estimates, also cite India's National Inventory Document accompanying BTR-1.

If this repository itself is used substantially in research or analysis, please also reference the repository URL and version/commit used.

## Disclaimer

This dashboard is an independent analytical and visualization layer built from publicly reported Government of India BTR-1 inventory data.

It is not an official Government of India, MoEFCC, UNFCCC, or IPCC product.

Every effort has been made to preserve the structure and values of the reported dataset. Users conducting formal reporting, regulatory work, peer-reviewed research, or inventory verification should validate relevant figures against the original CRT workbooks, BTR, and National Inventory Document.

## License

```text
MIT License
```

The license applied to this repository does not necessarily alter the copyright or reuse conditions of the underlying Government of India source documents and datasets.
