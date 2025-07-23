# PROJECT
🔁 Real-time Change Data Capture Pipeline using Azure Data Factory and Databricks
This project demonstrates how to build a robust data pipeline for Change Data Capture (CDC) using Azure Data Factory (ADF) and Azure Databricks. It captures changes from an on-premises or cloud-hosted SQL Server database and processes the updates at regular intervals. The pipeline handles ETL operations, data refresh, and email notifications—all fully automated.

📌 Project Overview
The goal is to create an end-to-end data ingestion and transformation pipeline that captures incremental changes (CDC) from SQL Server tables such as Customer, Product, Order, and Inventory. These changes are processed through a scheduled ETL notebook in Azure Databricks, orchestrated by Azure Data Factory (ADF), and the results are sent via email in a file format.

⚙ Key Features
🏗 SQL Server Table Setup


🔌 Secure Integration with Azure Data Factory using JDBC


📈 CDC Logic Executed with Databricks Notebooks


⏰ Scheduled Execution Every Hour


📧 Email Notification with File Attachment


🛠 Technologies Used-->
Tool/Service	Purpose
SQL Server,Source data storage (Customer, Product, etc.)
Azure Data Factory, Orchestration and scheduling engine
Azure Databricks, Data processing and CDC logic
JDBC Connector, Secure connectivity to SQL Server
Logic Apps / SMTP	Email notification service (optional)

🧱 Architecture Diagram
csharp
Copy
Edit
[SQL Server DB]
      |
      | (JDBC)
      v
      
[ADF -> Linked Service]
      |
      | (Trigger + Pipeline)
      v
      
[Databricks Notebook]
      |
      | (Transformed Data)
      v
      
[Email Notification + File Output]
🗂 Database Schema
1. Customer Table
Fields: customer_id, name, address, email, phone_number

2. Product Table
Fields: product_id, name, description, price, category

3. Order Table
Fields: order_id, customer_id, product_id, quantity, order_date, total_amount

4. Inventory Table
Fields: product_id, quantity, location

🔄 Step-by-Step Implementation
✅ Step 1: Create SQL Server Tables
Define and populate your tables with dummy data to simulate real-time updates.

🔗 Step 2: Connect SQL Server with ADF
Use Linked Service in ADF to securely connect to SQL Server.

Install and configure Self-hosted Integration Runtime (SHIR) if accessing an on-prem DB.

Test the connection and allow JDBC connectivity.

🔁 Step 3: Build the CDC Pipeline in Databricks
Use JDBC Connector to read from SQL Server.

Apply logic to fetch only changed records (using timestamps or row version).

Transform the data using PySpark or SQL in the Databricks notebook.

⏱ Step 4: Schedule with ADF
Schedule the Databricks notebook execution every 1 hour using ADF’s Trigger.

This ensures all recent changes are captured and processed timely.

✉ Step 5: Send Email Notifications
After pipeline execution:

Export results to .parquet

Send the updated file via email using Logic Apps or SMTP integration

🔐 Security & Best Practices
Use managed identities or Key Vault to store credentials securely.

Restrict firewall access to ADF and Databricks IPs only.

Log pipeline runs and notebook outputs for audit and rollback.

✅ Success Criteria
Updated data is captured correctly from all 4 tables

ETL pipeline runs successfully every hour

Email with the updated file is received on completion

📂 Output Example
Output.parquet

