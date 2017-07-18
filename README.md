# PDDPheWAS

# Action Items for the PDD PheWAS

Raw data is on Google Drive - link sent out by Michelle

Includes the following files:

Cutting_DDv2.xlsx - key describing fields and values for other files

CUTTING_DD_20160318.csv - demographic or group file

	Note: Affstat states if an ID is a case or a control (1 or 2) and Case_type states what ICD9 code justifies the ID as a case

CUTTING_ICD9_20160318.csv - ICD9 codes for each ID/visit

CUTTING_CONTROL_MATCHING_20160318.csv - matching file with cases (RUIDs) and their two matching control IDs

1. Make Group and ICD-9 file:
    A. From the raw data, select cases that have the following ICD-9 codes (can use Case_type to match):
        299, 299.0, 299.00, 299.1, 299.01, 299.8, 299.9, 299.10, 299.11, 299.80, 299.81, 299.90, 299.91
    B. Select matching controls for the case IDs based on CONTROL_MATCHING file.
    C. Select rows from ICD9 file that match both case and control RUIDs.
2. Add Age related fields to files:
    A. AgeatICD to ICD9 file - is this the correct field name?
        i. Use ConvertAge tool? I am not sure which tool you were thinking for this.
    B. Add MaxAgeatICD and MinAgeatICD to Group file - are these the correct field names?
        i. Use ConvertAge tool? I am not sure which tool you were thinking for this.
4. Censor dataset
    A. Remove any CASES that have the following ICD9 codes prior to age 2 (not including age 2 exactly):
        299, 299.0, 299.00, 299.1, 299.01, 299.8, 299.9, 299.10, 299.11, 299.80, 299.81, 299.90, 299.91
    B. Remove any CASES OR CONTROLS that have the following ICD9 codes at any age:
        330.8, 758.0, 758.39, 758.5, 758.83, 759.89
