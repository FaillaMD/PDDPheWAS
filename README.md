# PDDPheWAS

# Action Items for the PDD PheWAS

Raw data is on Google Drive - link sent out by Michelle

Includes the following files:

Cutting_DDv2.xlsx - key describing fields and values for other files

CUTTING_DD_20160318.csv - demographic or group file

- Note: Affstat states if an ID is a case or a control (1 or 2) and Case_type states what ICD9 code justifies the ID as a case

CUTTING_ICD9_20160318.csv - ICD9 codes for each ID/visit

CUTTING_CONTROL_MATCHING_20160318.csv - matching file with cases (RUIDs) and their two matching control IDs

# Clean Dataset
1. Make Group and ICD-9 file:
    1. From the raw data, select cases that have the following ICD-9 codes (can use Case_type to match): 
    	- 299, 299.0, 299.00, 299.1, 299.01, 299.8, 299.9, 299.10, 299.11, 299.80, 299.81, 299.90, 299.91
        - Select rows from the group file where AFF_STATUS=0 for each case RUID. 
    2. Select matching controls for the case IDs based on CONTROL_MATCHING file.
        - Select rows from the group file where AFF_STATUS=1 for Control1 RUIDs and AFF_STATUS=2 for Control2 RUIDs. 
    3. Select rows from ICD9 file that match both case and control RUIDs.
2. Add Age related fields to files:
    1. AgeatICD to ICD9 file - is this the correct field name?
        - Use ConvertAge tool? I am not sure which tool you were thinking for this.
    2. Add MaxAgeatICD and MinAgeatICD to Group file - are these the correct field names?
        - Use ConvertAge tool? I am not sure which tool you were thinking for this.
4. Censor dataset:
    1. Remove any CASES that have the following ICD9 codes prior to age 2 (not including age 2 exactly):
        - 299, 299.0, 299.00, 299.1, 299.01, 299.8, 299.9, 299.10, 299.11, 299.80, 299.81, 299.90, 299.91
    2. Remove any CASES OR CONTROLS that have the following ICD9 codes at any age:
        - 330.8, 758.0, 758.39, 758.5, 758.83, 759.89
