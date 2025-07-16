# Business Process Mining Foundations

## Phase 1: Understand Process Mining Basics

**Definition:**  
Process Mining analyzes business processes using IT system event logs, turning raw data into visual flows showing actual operations.

**Main Types:**  
- Process Discovery  
- Conformance Checking  
- Enhancement  

**Why It Matters:**  
- Identifies bottlenecks, reduces cycle time  
- Improves compliance, automation  

**Event Log Structure Essentials:**  
- Case ID  
- Activity  
- Timestamp  
- Attributes  

**Process Mining Steps:**  
1. Extract data  
2. Transform into event logs  
3. Analyze using SAP Signavio PI  
4. Take action  

---

## Phase 2: Learn Business Context  

**Core Business Processes:**  
- Procure-to-Pay (P2P)  
- Order-to-Cash (O2C)  
- Hire-to-Retire (H2R)  
- Issue-to-Resolution  
- Record-to-Report (R2R)  
- Plan-to-Fulfill (P2F)  

**Typical P2P Steps:**  
Create Requisition → Approve → PO → Supplier → Receive Goods → Invoice → Pay Supplier  

**Key KPIs:**  
| KPI               | Purpose                |
|-------------------|-----------------------|
| Cycle Time        | Bottlenecks            |
| Touchless Rate    | Automation potential   |
| Rework Rate       | Inefficiencies         |
| Conformance Score | Compliance             |
| Lead Time/Step    | Step delays            |

**Business Problems Solved:**  
- Bottlenecks  
- Deviations  
- Supplier or step delays  
- Automation opportunities  

**Communicating Findings:**  
Focus on business impact. Example:  
“Reducing rework saves 10 days/month.”  

---

## Phase 3: Build and Understand Event Logs

**What Is an Event Log:**  
A structured table used in process mining showing:  
- Case ID  
- Activity  
- Timestamp  
- Attributes  

**Example Table:**  
| Case ID | Activity    | Timestamp           | User     | Amount |  
|---------|-------------|--------------------|----------|--------|  
| PO001   | Create PO   | 2025-06-20 08:15   | UserA    | 1000€  |  
| PO001   | Approve PO  | 2025-06-20 14:30   | ManagerB | 1000€  |  

**Steps from Raw Data to Event Logs:**  
1. Identify Case IDs, Activities, Timestamps, Attributes  
2. Transform using SQL or Python  

**SQL Essentials:**  
SELECT, FROM, JOIN, WHERE, ORDER BY, GROUP BY  

**SQL Query Example:**  

SELECT po.po_number AS CaseID, 'Create PO' AS Activity, po.creation_date AS Timestamp  
FROM purchase_orders po  
UNION ALL  
SELECT ap.po_number AS CaseID, 'Approve PO' AS Activity, ap.approval_date AS Timestamp  
FROM approvals ap  
ORDER BY CaseID, Timestamp;  

**Python Skills:**  
- pandas for event log creation  
- CSV export for SAP Signavio upload  

**Validation Checklist:**  
- Case IDs consistent  
- Timestamps ordered  
- Activities clear  
- Attributes formatted  

---

## Phase 4: SAP Signavio Process Intelligence Basics

**What It Is:**  
SAP’s cloud-based tool for process mining, monitoring, and optimization.

**Core Functions:**  
- Upload/manage event logs  
- Visualize processes, variants  
- Analyze performance, conformance  
- Build dashboards  

**Navigating SAP Signavio PI:**  
- Home  
- Analysis View  
- Data Upload  

**Uploading Event Logs:**  
- Format: Case ID, Activity, Timestamp, Attributes  
- Validate data integrity  
- Upload and map fields  

**Analyzing Processes:**  
- Process Explorer: Activity frequency, cycle time, top variants  
- Common questions: Happy path %, deviations, rework  

**Conformance Checking:**  
- Define reference model  
- Compare event logs  
- Review conformance rate, deviations  

**Building Dashboards:**  
- Elements: Cycle Time, Top Variants, Conformance, Rework, Touchless Rate  
- Tools: Drag-and-drop charts, filters  
- Tip: Sketch layout first  

---

## Phase 5: SAP System Integration  

**Why It Matters:**  
SAP systems must feed structured event logs into SAP Signavio PI for real business monitoring.

**Main SAP Systems:**  
| System         | Purpose/Use Case                |
|----------------|---------------------------------|
| S/4HANA        | Modern ERP (P2P, O2C)          |
| SAP ECC        | Legacy ERP                      |
| Ariba          | Procurement                     |
| SuccessFactors | HR processes (Hire-to-Retire)   |

**Data Extraction Methods:**  
- Direct Connectors (SAP BTP Integration Services)  
- Manual Extraction (CDS Views, SAP Data Intelligence, Datasphere, CSV)  

**When Manual?**  
Legacy systems, custom processes.

**Tools Overview:**  
| Tool              | Function                        |
|-------------------|--------------------------------|
| CDS Views         | Pre-built queries              |
| SAP DI            | Data orchestration             |
| SAP Datasphere    | Data warehouse                 |
| ETL Tools/APIs    | General extraction            |

**From SAP System to PI: 5 Steps:**  
1. Identify relevant tables (Purchase Orders, Invoices)  
2. Extract data (CDS Views, SAP DI)  
3. Transform: Case ID, Activity, Timestamp, Attributes  
4. Clean and validate  
5. Upload (CSV or Connector)  

**Scheduling & Automation:**  
- Scheduled Jobs: Automated extraction  
- Data Refresh in SAP PI  
- Tools: SAP DI Pipelines, SAP BTP Services

---

## Phase 6: SAP Signavio Analytics Language (SiGNAL)

**Purpose:**  
SiGNAL is SAP Signavio Process Intelligence's SQL-inspired query language, optimized for large-scale process mining analyses. It supports read-only queries for conformance checking, cycle time, and rework analysis.

---

**Core Concept:**  
- Single nested table: case attributes + nested events.  
- SQL-like syntax (SELECT, WHERE, GROUP BY, ORDER BY).  
- Read-only: no update/delete commands.

---

**Data Model:**  
- Mandatory fields:  
  - case_ID  
  - event_name  
  - end_time  
- Case attributes: Customer ID, Status, City (fixed per case).  
- Event attributes: Payment Method, Cancellation Reason (vary by event).

### Table Example:

<img width="843" height="569" alt="image" src="https://github.com/user-attachments/assets/06141c45-193d-4db0-b072-3e7270ee6b5c" />

---

**Iteration Options:**  
- By Case → 1 row per case, nested events table  
- By Event → 1 row per event, repeating case attributes  

---

**SiGNAL Usage Overview:**  
- Query structure: SELECT, WHERE, GROUP BY, ORDER BY  
- Optimized for KPIs like cycle time, conformance rate  
- Handles nested data directly  

**Example Query:**  
SELECT variant, COUNT(*)  
FROM event_log  
GROUP BY variant  
ORDER BY COUNT(*) DESC  
LIMIT 10;

---

**Key Takeaways:**  
- Case + Event attributes structure  
- SQL-like querying but adapted for nested event logs  
- Focused on process mining KPIs  
- Used directly inside SAP Signavio PI  

---

## Phase 7: Understand Core Business Processes

---

### Procurement  

#### Procure-to-Pay (P2P)  
1. Create Purchase Requisition  
2. Approve Requisition  
3. Create Purchase Order  
4. Send to Supplier  
5. Receive Goods  
6. Receive Invoice  
7. Pay Supplier  

#### Source-to-Contract (S2C)  
1. Identify Sourcing Needs  
2. Supplier Discovery  
3. Request for Proposal (RFP)/Quotation  
4. Negotiate Terms  
5. Contract Creation  
6. Contract Approval and Storage  

#### Supplier Relationship Management (SRM)  
1. Supplier Onboarding  
2. Monitor Supplier Performance  
3. Conduct Supplier Audits  
4. Manage Supplier Compliance  
5. Develop Supplier Improvement Plans  

---

### Supply Chain  

#### Plan-to-Fulfill (P2F)  
1. Demand Planning  
2. Supply Planning  
3. Production Scheduling  
4. Manufacturing/Assembly  
5. Quality Control  
6. Delivery/Shipment  

#### Inventory Management  
1. Stock Level Monitoring  
2. Replenishment Planning  
3. Safety Stock Management  
4. Inventory Auditing  
5. Inventory Adjustment  

#### Warehouse Management (WM)  
1. Goods Receipt  
2. Putaway  
3. Picking  
4. Packing  
5. Shipping  

#### Logistics Execution  
1. Transportation Planning  
2. Freight Booking  
3. Goods Dispatch  
4. Track and Trace  
5. Goods Receipt Confirmation  

---

### Sales and Customer Service  

#### Order-to-Cash (O2C)  
1. Receive Customer Order  
2. Check Credit  
3. Create Sales Order  
4. Deliver Goods/Services  
5. Issue Invoice  
6. Receive Payment  

#### Issue-to-Resolution  
1. Receive Customer Issue/Ticket  
2. Categorize and Prioritize  
3. Assign to Support Agent  
4. Investigate and Resolve Issue  
5. Close Ticket  
6. Provide Feedback (Optional)  

---

### Finance  

#### Record-to-Report (R2R)  
1. Record Financial Transactions  
2. Reconcile Accounts  
3. Close Period/Month-End  
4. Generate Financial Statements  
5. Report to Stakeholders  

#### Treasury-to-Pay (T2P)  
1. Manage Cash and Liquidity  
2. Execute Payments  
3. Monitor Payment Status  
4. Reconcile Bank Statements  

---

### Human Resources  

#### Hire-to-Retire (H2R)  
1. Recruit and Hire Employee  
2. Onboarding  
3. Manage Employment (Payroll, Benefits)  
4. Performance Management  
5. Offboarding/Retirement  

#### Learning and Development  
1. Identify Training Needs  
2. Design Training Programs  
3. Conduct Training Sessions  
4. Evaluate Training Effectiveness  

#### Payroll Processing  
1. Collect Time and Attendance Data  
2. Calculate Payroll  
3. Process Deductions and Taxes  
4. Distribute Payslips  
5. Report to Authorities  

---

### IT & Compliance  

#### Access-to-Authorization  
1. Request User Access  
2. Approve Access Rights  
3. Assign Roles and Permissions  
4. Monitor Access Logs  
5. Revoke Access When Needed  

#### Compliance Monitoring  
1. Define Compliance Rules  
2. Monitor Transactions  
3. Flag Violations  
4. Conduct Audits  
5. Report Compliance Status  

