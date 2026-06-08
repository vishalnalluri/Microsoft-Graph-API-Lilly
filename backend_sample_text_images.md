# backend sample text images

## Page 1

![Page 1](<images/backend_sample_text_images/page_1.png>)

Sample PDF for Backend Testing
Purpose: This file contains regular text, headings, bullet points, a table, images, and a chart. It can be used to
test PDF upload, text extraction, page parsing, table reading, image detection, and metadata handling in
backend code.
1. Sample Paragraph Text
This is a general sample document created for software testing. The content is intentionally simple and includes
predictable labels so that backend logic can verify whether text extraction is working correctly. The document
also includes visual objects to test whether image extraction or OCR-based fallback logic is required.
Important test keywords: invoice, customer, API, dashboard, health record, Salesforce, document parser,
backend service, and sample image.
2. Bullet List Sample
• Extract all text from each page.
• Identify embedded images and charts.
• Read tabular content without losing row and column structure.
• Preserve page order and section headings.
• Return clean JSON output from the backend service.
3. Sample Table
Record ID
Name
Type
Status
Amount
1001
Alpha Health
Customer
Active
$1,250
1002
Blue River
Partner
Pending
$860
1003
Care Plus
Lead
New
$420
1004
Delta Clinic
Customer
Closed
$2,100
4. Embedded Image Sample

---

## Page 2

![Page 2](<images/backend_sample_text_images/page_2.png>)

Figure 1: Dummy landscape image included to test image extraction from PDFs.

---

## Page 3

![Page 3](<images/backend_sample_text_images/page_3.png>)

5. Diagram and Chart Page
This page contains a process diagram and a chart. These visual elements help validate whether the backend
can detect non-text objects and preserve their relationship to nearby captions.
Figure 2: Sample backend processing workflow diagram.
Figure 3: Dummy bar chart with monthly API request values.
6. JSON-like Text Block
{ "document_id": "PDF-TEST-001", "pages": 2, "contains_images": true, "contains_tables": true, "source":
"sample_backend_test" }
End of sample PDF. This final sentence is included to confirm that the parser reaches the end of the document.