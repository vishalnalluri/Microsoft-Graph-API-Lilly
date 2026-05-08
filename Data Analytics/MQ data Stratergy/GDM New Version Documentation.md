# GDM New Version Documentation

GDM New Version Documentation
Architecture Diagram :


S3 setup: Create an External Location in Databricks Unity Catalog using an IAM role. This is the official, secure way to mount S3 without hardcoding credentials.
Use Auto Loader (cloud Files format) in a Databricks notebook or DLT pipeline. It watches your S3 path and ingests new files automatically into a Delta table — handles CSV, XLSX (via pandas), JSON, and Parquet.


Alternate method:
CSV / XLSX / Source Files
↓
Amazon S3
↓
Unity Catalog Storage Credential + External Location
↓
Databricks Tables / Views / Datasets
↓
Genie AI for NLQ
↓
AI/BI Dashboard


For the one genie_space


API:
POST /api/2.0/genie/spaces — guaranteed fresh space_id
Deletes the old space first via DELETE /api/2.0/genie/spaces/{id}










Fresh new Genie Space every time(not reuse)





To Create the Dashboard API
All endpoints at a glance





| Operation | Method | Endpoint |
| --- | --- | --- |
| Create
dashboard | POST | /api/2.0/lakeview/dashboards |
| Get dashboard | GET | /api/2.0/lakeview/dashboards/{id} |
| Update dashboard | PATCH | /api/2.0/lakeview/dashboards/{id} |
| Publish dashboard | POST | /api/2.0/lakeview/dashboards/{id}/published |
| Unpublish | DELETE | /api/2.0/lakeview/dashboards/{id}/published |
| Set permissions | PUT | /api/2.0/permissions/dashboards/{id} |
| Schedule refresh | POST | /api/2.0/lakeview/dashboards/{id}/schedules |
| List dashboards | GET | /api/2.0/lakeview/dashboards |
| Delete (permanent) | POST | /api/2.0/workspace/delete |
| Export as file | GET | /api/2.0/workspace/export |
