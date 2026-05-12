# Flattened Extract Request

Request for Flattened Extract and Path Consistency in EDB Refined 

Context: 

Request Summary: 

Data Format Requirements: 

- The extract should be flattened, with nested structures resolved into a flat key-value format. 

- The extract must exclude all Personally Identifiable Information (PII) such as: 

- Name 

- Email - Phone number 

- Street address 

- Date of birth 

Example of Desired Flattened Format: { "Id": "24b597c9-0e3f-43a4-981b-b2b5fc269aty", "DataSource": "concern", "CapiId": "", "Cid": "bc18fc48-c876-40a7-b49b-586324cb6fa0", "ComplaintType": "Pen Issue - Medicine leaked", "IsAdverseEvent": true, "Product": "Mounjaro", "ProductType": "autoinjector", "Strength": "15MG/0.5ML", "BatchId": "D118800", "DeviceReturn": "yes", "ProductReplacementReason": "Product Issue", "ProductComplaintClassification": "Pen Issue - Medicine leaked", "TriggeredQuestion_1": "Medicine leaked from the needle while pen was placed against the skin", "TriggeredQuestion_2": "Is the gray plunger visible? - Yes", "Country": "US", "Source": "found_by_demographics", "OverallStatus": "SUCCESS", "RecordId": "500dl00000b9ZnkAAE", "CaseId": "500dl00000b9CMYAA2", "UID": "001dl00000nIEOWAA4", "Status": "processing", "Timestamp": "2025-10-06T13:48:45.381Z" } Path Consistency Request: Expected Path: 

Current Path Observed: 

