# HELFO Physiotherapists Analysis – Power BI Project

This project explores publicly available HELFO data on physiotherapists with municipal agreements ("driftstilskudd") in Norway.  
The goal was to practice **data ingestion, cleaning, DAX modeling, and dashboard design** in Power BI.

## Dataset
- **Source:** Municipal websites publishing lists of physiotherapists with agreements
- **Sample size:** ~350 physiotherapists (multiple municipalities)
- **Columns used:** First name, Last name, Kommune, Fylke, Specialty

## Methodology

### Power Query
- Combined multiple Excel files from a folder
- Cleaned rows with invalid names (`oppgitt`, numeric-only, etc.)
- Tokenized names (first word for first names, last word for surnames)

### DAX Logic
- Built reference tables of typical Norwegian first and last names
- Added rules: Nordic characters (æ, ø, å), surname suffixes (–sen, –son, –berg, etc.)
- Created classification:  
  - Likely Scandinavian  
  - Possibly Scandinavian  
  - Likely Non-Scandinavian  
  - Unclear

### Dashboard
- KPI Cards (totals and percentages)
- Stacked bar chart by kommune
- Treemap by specialty
- Filled map by fylke
- Detail QA table

## Example DAX Snippet
```DAX
Share Non-Scand % =
DIVIDE([Likely Non-Scandinavian], [Total Physios])
```

## Results (Sample)
- 65% Likely Scandinavian  
- 8% Likely Non-Scandinavian  
- 26% Possibly Scandinavian  

## Limitations
- Not a full dataset (Norway has ~3,500 physiotherapists with agreements)
- Names alone cannot define ethnicity
- This is a portfolio project, not a scientific study

## Files
- `helfophysio.pbix` – full Power BI dashboard
- `screenshots/` – sample visuals

## Reflections
This project was a valuable exercise in Power BI:
- Folder ingestion and data cleaning
- Tokenizing and classification with DAX
- Dashboard design for healthcare data
