# GDM New Version Documentation

**GDM New Version Documentation**

**\
Architecture Diagram :**

**\**
<img src="/tmp/docx_aok64hp2/media/media/image1.png" style="width:6.3279in;height:3.52226in" />

1.  **S3 setup:** Create an External Location in Databricks Unity Catalog using an IAM role. This is the official, secure way to mount S3 without hardcoding credentials**.**

2.  **Use Auto Loader** (cloud Files format) in a Databricks notebook or DLT pipeline. It watches your S3 path and ingests new files automatically into a Delta table — handles CSV, XLSX (via pandas), JSON, and Parquet.

<img src="/tmp/docx_aok64hp2/media/media/image2.png" style="width:6.5in;height:3.98264in" />

3.  

4.  **Alternate method:**

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

****

**For the one genie_space**<img src="/tmp/docx_aok64hp2/media/media/image3.png" style="width:6.5in;height:3.82639in" />

> **API:**

**POST** /api/2.0/genie/spaces — guaranteed fresh space_id

**Deletes** the old space first via DELETE /api/2.0/genie/spaces/{id}

> **Fresh new Genie Space every time(not reuse)**

<img src="/tmp/docx_aok64hp2/media/media/image4.png" style="width:6.5in;height:4.21319in" />

**To Create the Dashboard API**

All endpoints at a glance

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 23%" />
<col style="width: 58%" />
</colgroup>
<thead>
<tr>
<th>Operation</th>
<th>Method</th>
<th>Endpoint</th>
</tr>
</thead>
<tbody>
<tr>
<td><p>Create</p>
<p>dashboard</p></td>
<td>POST</td>
<td>/api/2.0/lakeview/dashboards</td>
</tr>
<tr>
<td>Get dashboard</td>
<td>GET</td>
<td>/api/2.0/lakeview/dashboards/{id}</td>
</tr>
<tr>
<td>Update dashboard</td>
<td>PATCH</td>
<td>/api/2.0/lakeview/dashboards/{id}</td>
</tr>
<tr>
<td>Publish dashboard</td>
<td>POST</td>
<td>/api/2.0/lakeview/dashboards/{id}/published</td>
</tr>
<tr>
<td>Unpublish</td>
<td>DELETE</td>
<td>/api/2.0/lakeview/dashboards/{id}/published</td>
</tr>
<tr>
<td>Set permissions</td>
<td>PUT</td>
<td>/api/2.0/permissions/dashboards/{id}</td>
</tr>
<tr>
<td>Schedule refresh</td>
<td>POST</td>
<td>/api/2.0/lakeview/dashboards/{id}/schedules</td>
</tr>
<tr>
<td>List dashboards</td>
<td>GET</td>
<td>/api/2.0/lakeview/dashboards</td>
</tr>
<tr>
<td>Delete (permanent)</td>
<td>POST</td>
<td>/api/2.0/workspace/delete</td>
</tr>
<tr>
<td>Export as file</td>
<td>GET</td>
<td>/api/2.0/workspace/export</td>
</tr>
</tbody>
</table>

<img src="/tmp/docx_aok64hp2/media/media/image5.png" style="width:6.5in;height:4.60069in" />
