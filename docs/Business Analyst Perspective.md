# Business Analyst Perspective
![A diagram of a document AI-generated content may be incorrect.](<images/Business Analyst Perspective/image1.png>)


{width="6.5in" height="4.585416666666666in"}

**Business Analyst Perspective: Complaint Submission Dashboard**

**Version 2**

------------------------------------------------------------------------

**🔹 1. Objective**

To design a data-driven solution that enables the Attorney General's Office to **monitor**, **analyze**, and **respond** efficiently to reported patient abuse and neglect complaints, using insights derived from the online complaint form.

------------------------------------------------------------------------

**🔹 2. Data Modeling**

**✅ Entities Identified from the Form:**

  ----------------------------------------------------------------------------
  **Entity**        **Description**
  ----------------- ----------------------------------------------------------
  **Complainant**   The person submitting the complaint

  **Victim**        The patient who suffered the abuse/neglect

  **Facility**      The residential care institution where incident occurred

  **Incident**      Details about the reported abuse/neglect

  **Reporting**     Status of reports to Police, APS, ISDH

  **Attachments**   Supporting documentation status
  ----------------------------------------------------------------------------

**✅ Recommended Fields for the Dataset (Normalized):**

  ---------------------------------------------------------------------------------------------------------------------
  **Table**              **Key Fields**
  ---------------------- ----------------------------------------------------------------------------------------------
  **Complainant_Info**   Complainant_ID, Name, Contact Info, Address

  **Facility_Info**      Facility_ID, Name, Address, County

  **Incident_Details**   Incident_ID, Victim_Name, Incident_Date, Description, Complainant_ID, Facility_ID

  **Report_Status**      Incident_ID, Reported_to_Police, Reported_to_ISDH, Reported_to_APS, Supporting_Docs_Uploaded
  ---------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

**🔹 3. Business Questions to Answer**

  --------------------------------------------------------------------------------------------------------
  **Question**                                                  **Insight**
  ------------------------------------------------------------- ------------------------------------------
  📍 Where are the most complaints coming from (county-wise)?   Identify high-risk regions or facilities

  🏥 Which care facilities are most frequently reported?        Spot potential problem facilities

  🕒 Are cases increasing over time?                            Monitor trends and seasonality

  🚓 Are complaints being reported to authorities?              Track underreporting trends

  📎 Are supporting documents being uploaded?                   Assess completeness of reports
  --------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

**🔹 4. Power BI Dashboard Design**

**📊 Visual Layer (Suggested Reports)**

  -------------------------------------------------------------------------------------------------------
  **Report Section**               **Visual**                   **Purpose**
  -------------------------------- ---------------------------- -----------------------------------------
  **Geographic Hotspots**          Map (Choropleth or bubble)   Visualize complaints by county or zip

  **Facility Report Frequency**    Bar Chart                    Top facilities with repeated complaints

  **Trend Analysis**               Line/Area Chart              Complaints over months/quarters

  **Authority Reporting Status**   Pie/Donut Charts             \% reported to Police, APS, ISDH

  **Document Completeness**        Bar/100% Stacked Bar         \% with/without supporting documents

  **Complaint Drilldown**          Table with slicers           Detailed records for investigation team
  -------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

**🔹 5. Filters and Slicers for Dynamic Analysis**

- Facility County / Name

- Incident Date Range

- Reported to Police/APS/ISDH (Yes/No)

- Supporting Documents (Yes/No)

- Victim Name or Facility Type (if available)

------------------------------------------------------------------------

**🔹 6. Recommendations**

1.  **Automate data ingestion** from the online form to Power BI using Power Automate or API integration.

2.  Use **row-level security** in Power BI to restrict sensitive case details by user role (e.g., investigators vs. analysts).

3.  Implement **alerts** for spikes in complaints from any one facility or region.

4.  Use **natural language Q&A** in Power BI to allow stakeholders to ask questions directly (e.g., \"Show complaints reported last month\").
