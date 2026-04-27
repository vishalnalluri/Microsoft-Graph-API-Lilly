# HCSP Onboarding KT Document

**Onboarding Process**

**People Involved:**

**Syra –** Sely-Ann (Project Manager), Ekaterina (Reporting Team), Ajay (Support Team), Anusha (Learning Paths Content Creator)

**Yes LMS** – **Felipe**/Doug

**State –** Jessica, **Kathy**, Richard

**Steps of Onboarding Process:**

**Step1:** Ajay Sends Survey through email.

**Step 2:** Download Survey and make sure Provider Names have any special characters like the apostrophe. If found, remove it.

**Step 3: Open**

**Lambda Function:** Onboarding-List-Creation - \> Change List number in the Lambda function code and deploy. Ex: List-43

**S3:** onboarding-list-creation-data

**Step 4: In S3 bucket,** onboarding-list-creation-data - \> Input

Delete old Survey from onboarding-list-creation-data - \> Input.

Upload New Survey in onboarding-list-creation-data - \> Input.

<img src="C:\Users\VISHAL~1\AppData\Local\Temp\conv_56bw255q\media/media/image1.png" style="width:7.1212in;height:1.58096in" />

<img src="C:\Users\VISHAL~1\AppData\Local\Temp\conv_56bw255q\media/media/image2.png" style="width:6.73021in;height:0.67719in" />

Group Code Creation Lambda Function:\
**Group-Code-Creation**

Once we get Group Code, we need to recheck if it is unique:

<img src="C:\Users\VISHAL~1\AppData\Local\Temp\conv_56bw255q\media/media/image3.png" style="width:6.05293in;height:0.42714in" />

<img src="C:\Users\VISHAL~1\AppData\Local\Temp\conv_56bw255q\media/media/image4.png" style="width:5.17781in;height:0.40631in" />

**Send Emails to Providers:**

**Lambda Function:** send_bulk_ses_emails

**S3 Bucket:** ses-email-info

**Inserting List into RDS:**

**Lambda Function:** List-Insertions-Into-RDS

**S3:** list-insertion-into-rds-storage
