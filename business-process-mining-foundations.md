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
