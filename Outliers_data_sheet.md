# Datasheet Template

## Motivation

The dataset was created to facilitate machine learning based detection of anomalies in Pillar 3 data. For the initial model build, this has been limited to the CR6 credit risk disclosures published by UK banks. These anomalies may indicate reporting inconsistencies or emerging risk trends that warrant further analysis.
The consolidated data set was created by Fiona Galbraith from published Pillar 3 reports, which are published periodically by UK and EU banks. It was created as part of a research project by Fiona Galbraith to explore the use of unsupervised machine learning to financial regulatory data.
The dataset was compiled independently for research purposes from externally published data.
 
## Composition

The data is a subset of the published Pillar 3 documents from the following 6 UK banks:
- HSBC (https://www.hsbc.com/-/files/hsbc/investors/hsbc-results/2024/annual/pdfs/hsbc-holdings-plc/250219-pillar-3-disclosures-at-31-december-2024.pdf?download=1)
 - NatWest Group (https://www.investors.rbs.com/~/media/Files/R/RBS-IR-V2/results-center/14022025/nwg-pillar-3-report.pdf)
 - Barclays Bank Group (https://home.barclays/content/dam/home-barclays/documents/investor-relations/ResultAnnouncements/FullYear2024Results/FY24-Barclays-Bank-PLC-Pillar-3-Report.pdf)
 - Lloyds Banking Group (https://www.lloydsbankinggroup.com/assets/pdfs/investors/financial-performance/lloyds-banking-group-plc/2024/q4/2024-lbg-fy-pillar-3.pdf)
 - Santander (https://www.santander.com/en/shareholders-and-investors/financial-and-economic-information/pillar-3-disclosures-report)
 - Standard Chartered (https://www.sc.com/en/investors/financial-results/)

The CR6 tables were used as a representative subset of the published data. The CR6 comprises the AIRB Credit Risk metrics, split by exposure class. Only the subtotals for each table were used. This resulted in 55 rows of data representing the split by bank and exposure class. Exposure classes used were: Central Governments or Central Banks; Institutions; Corporates - Non-SME/other, Corporates -  SME, Corporates - Specialised Lending, Retail - Secured by real estate - Other, Retail - Secured by real estate - SME, Other Retail - Non SME, Other Retail - SME, Qualifying Revolving. 

Each row had 13 different metrics:  The data captured in each summary was: Original exposure (On balance sheet); Original exposure (Off balance sheet); Average CCF; Exposure at default (post CCF); Average Probability of Default (PD); Obligor number, Average loss given default (LGD), Average maturity, Risk Weighted Assets (RWA), RWA as a percentage of EAD, Expected loss (EL), Provisions.

The data is externally published and is not considered to be confidential.

## Collection process

The data was initially obtained by downloading the Pillar 3 results for 2024 for each of the banks in PDF format. 

Camelot was used to convert the tables in the PDF documents into excel. To limit the quantity of data as an initial trial, the data was limited to a subset of tables from within the document - the CR6 credit risk tables, and again was limited to the sub-totals for each exposure class. Only data from the year 2024 was used.

## Preprocessing/cleaning/labelling

There was some missing data, where a metric is not used in the calculation this is left blank. Where this was the case, the rows were either deleted (i.e. where a particular exposure class was not present) or a median value was input (i.e. where maturity is not used in the AIRB calculation, a value of 2.5 was used as the mid-point).

Numeric features were scaled using StandardScalar.
 
## Uses

The dataset could be scaled to include all data from the CR6 tables, and extended to all tables within the Pillar 3 data set. This would support benchmarking and trend analysis of the Pillar 3 documents, as well as potentially highlighting data quality issues.

The output from the models should not be used without human review and should only be used to highlight areas for further investigation. It should not be used as a proxy for individual bank performance or risk or as a measure of the accuracy of that bank's published data. 

## Distribution

The consolidated data set has not been publicly distributed. The dataset is derived from publicly available reports.

## Maintenance

The dataset is maintained by Fiona Galbraith and may be periodically updated as new Pillar 3 reports are published.

