Step 1 — Log in
Open Splunk Cloud Web UI
Step 2 — Create Index
Navigate to:
Settings → Indexes → New Index
<img width="1889" height="902" alt="image" src="https://github.com/user-attachments/assets/04e72267-220e-4eaf-a9ee-b491b2038f7f" />
Fill in:

Index Name: lab_logs
Data Type: Events
Keep all other settings as default
Click Save
✅ Your index is now ready

Lab 2 — Ingest a Sample Log File
Sample Log File (sample.log)
2024-06-20 12:10:23 INFO User login successful 
2024-06-20 12:11:05 ERROR Failed to connect to database 
2024-06-20 12:11:20 WARN Low memory threshold reached 
2024-06-20 12:12:00 ERROR Application crashed
Step 1 — Add Data
Go to:
Settings → Add Data → Upload
Select your sample.log
Click Next
Step 2 — Set Source Info
Sourcetype: lab_log
Index: lab_logs
Click:
Review → Submit
✅ Data is now ingested
<img width="1890" height="940" alt="image" src="https://github.com/user-attachments/assets/96f2a5e2-9e2b-48a6-962c-5afac4d597b9" />
<img width="1825" height="910" alt="image" src="https://github.com/user-attachments/assets/933e556c-6e0c-4212-995d-8ede27dd7d30" />
<img width="1901" height="802" alt="image" src="https://github.com/user-attachments/assets/d5969a3a-7cdb-4c95-bc1f-b81440aa8d43" />
<img width="1859" height="839" alt="image" src="https://github.com/user-attachments/assets/991ff0f7-2a6c-4550-ac06-c76cb1496263" />
<img width="1829" height="874" alt="image" src="https://github.com/user-attachments/assets/cbb20388-2331-4137-96e7-bfa0aebf1b1b" />
<img width="1780" height="397" alt="image" src="https://github.com/user-attachments/assets/af3acf9a-0ebb-4432-8524-06914984b897" />
<img width="1881" height="806" alt="image" src="https://github.com/user-attachments/assets/a34f75f4-2ace-4301-a9ad-c8886964345b" />
<img width="1905" height="915" alt="image" src="https://github.com/user-attachments/assets/db7a6dfa-795b-404c-9963-d51ea3c9d03b" />

Lab 3 — Search Your Data (SPL)
Go to Search & Reporting and try:
1. Verify ingestion
index=lab_logs
2. Count errors
index=lab_logs "ERROR"
| stats count
3. Error trends over time
index=lab_logs "ERROR"
| timechart count
<img width="1881" height="243" alt="image" src="https://github.com/user-attachments/assets/37d981de-a692-46b8-b90e-dc88801eeb35" />
<img width="1911" height="348" alt="image" src="https://github.com/user-attachments/assets/2d34df7e-f929-41b7-ad79-74a2285f3055" />
<img width="1879" height="301" alt="image" src="https://github.com/user-attachments/assets/4a03f70c-6a72-4bfd-9002-3bf4d288063b" />

Lab 4 — Create Dashboard
Step 1 — Create Dashboard
Navigate to:
Search & Reporting → Dashboards → Create New Dashboard
Enter:
Name: Lab Dashboard
ID: lab_dashboard
Permissions: Private or Public
Click Create Dashboard
Step 2 — Add Panels (recommended)
After creating:
Run a query (e.g., error count)
Click Save As → Dashboard Panel
Select Lab Dashboard
👉 Suggested panels:
Total logs (index=lab_logs)
Error count
Error trend (timechart)
<img width="1880" height="678" alt="image" src="https://github.com/user-attachments/assets/1dd66637-32d0-4eaf-830e-31ec7dbbb6a7" />
<img width="1884" height="903" alt="image" src="https://github.com/user-attachments/assets/d6ea941c-3aeb-4562-9392-43962b077142" />
<img width="1914" height="362" alt="image" src="https://github.com/user-attachments/assets/4d335997-2b38-4f8d-bda0-3e4dd1a3cbf4" />
<img width="679" height="647" alt="image" src="https://github.com/user-attachments/assets/0d6ffafc-c068-4883-865b-0b720d2f284c" />
<img width="700" height="287" alt="image" src="https://github.com/user-attachments/assets/7d74a4bb-0f0f-4c31-9482-5dc2d07a19ad" />
















