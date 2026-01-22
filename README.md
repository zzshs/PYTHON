# Financial Document Extraction and Standardization Pipeline

This repository contains a reproducible pipeline for collecting heterogeneous financial documents and converting them into a standardized, analysis-ready tabular format. The codebase is designed for settings where financial information is dispersed across PDFs, spreadsheets, word processor files, and CSVs, often with inconsistent layouts, units, and reporting periods.

The workflow is split conceptually into two stages: (1) document ingestion and preprocessing, and (2) structured metric extraction and conversion.




1. Document Ingestion and Preprocessing

The first component handles bulk ingestion of financial documents from a directory tree. It is intentionally format-agnostic and supports PDF, Excel (.xls, .xlsx), Word (.docx), and CSV files.

For each file type, the pipeline converts raw inputs into text- or image-based representations suitable for downstream parsing. PDFs are rasterized into high-resolution page images and, when possible, accompanied by extracted text. Spreadsheet, CSV, and Word files are converted into cleaned table representations with empty rows and columns removed. This stage does not attempt to interpret financial meaning; its sole purpose is to normalize diverse file formats into consistent intermediate inputs.


2. Metric Extraction and Conversion

The second component performs structured extraction of predefined financial metrics from the preprocessed document content. The extraction targets a fixed set of income and expenditure categories (e.g., revenues, fees, investment income, establishment costs, program expenditures, and totals) while allowing for variation in naming conventions and reporting structure across documents.

When documents contain multiple reporting periods, the pipeline preserves this structure by generating one observation per period. All extracted values are coerced into numeric form, with explicit handling of reporting units such as thousands, lakhs, millions, or billions. Global table-level units and local inline units are reconciled to ensure internal consistency.

The final output of this stage is a set of tidy CSV files, each corresponding to an input document, with standardized column names and numeric values suitable for econometric or descriptive analysis.








# Map_Visualization - Subnational Energy Indicator Mapping

This repository contains a reproducible Python script for visualizing
subnational variation in energy-related indicators using publicly available
tabular and geospatial data.

The code integrates country-level energy indicators with administrative
boundary data at multiple spatial levels and generates side-by-side thematic
maps to facilitate within-country comparison. Indicators are visualized using
a median-centered color scale to emphasize relative spatial disparities rather
than absolute magnitudes.
