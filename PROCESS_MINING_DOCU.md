## Phase 1–2: Process Mining Basics + Business Context

### Key Concepts
- **What is Process Mining?**  
  Analyze real processes from event logs — Discovery, Conformance, Enhancement.
- **Why It Matters:**  
  Bottlenecks, Compliance, Efficiency, Automation, Customer Satisfaction.

### Core Business Processes
- **Procure-to-Pay (P2P)** → S/4HANA, Ariba  
- **Order-to-Cash (O2C)** → S/4HANA, ECC  
- **Hire-to-Retire (H2R)** → SuccessFactors  
- **Issue-to-Resolution** → ServiceNow, Zendesk  
- **Record-to-Report (R2R)** → SAP FI/CO  
- **Plan-to-Fulfill (P2F)** → SAP IBP, S/4HANA  

### Process Mining KPIs  
| KPI               | What It Measures            |
|-------------------|----------------------------|
| Cycle Time        | Bottlenecks                 |
| Touchless Rate    | Automation potential       |
| Rework Rate       | Inefficiencies             |
| Conformance Score | Compliance                 |
| Lead Time per Step| Step delays                |

### Communicating Insights  
Focus on business impact (time, cost, compliance).  
Example:  
- “Reducing rework saves X days/month.”  
- “40% POs need manual correction — automation opportunity.”

---

## Phase 3: Event Logs — Build, Validate, Upload

### Event Log Structure
- **Case ID:** Unique identifier (e.g., PO Number)  
- **Activity:** Action performed (e.g., Create PO)  
- **Timestamp:** Exact date/time  
- **Attributes:** User, Amount, Department  

### Data Sources
- SAP S/4HANA, ECC, Ariba, SuccessFactors

### Tools  
- **SQL (must-know):** SELECT, JOIN, UNION, WHERE, ORDER BY  
- **Python:** pandas, pm4py for process mining workflows

### Validation Checklist
- Case IDs consistent  
- Timestamps in order  
- Activities clear  
- Attributes formatted  

### Uploading to SAP Signavio PI
- Format as CSV: Case ID, Activity, Timestamp, Attributes  
- Map fields in SAP Signavio PI  
- Confirm structure and sample cases  

---

## Phase 4–5: SAP Signavio PI Basics + SAP Integration

### SAP Signavio PI Capabilities
- Upload/manage event logs  
- Visualize processes and variants  
- Analyze performance and conformance  
- Build dashboards  

### SAP Systems for Process Mining
| System         | Use Case                     |
|----------------|------------------------------|
| S/4HANA        | P2P, O2C                     |
| SAP ECC        | Legacy ERP                   |
| Ariba          | Procurement                  |
| SuccessFactors | Hire-to-Retire               |

### Data Extraction Methods
- **Direct Connectors (via SAP BTP)**  
- **Manual Extraction (CSV/ETL):**  
  - **CDS Views**: Pre-built SAP queries  
  - **SAP Data Intelligence (DI)**: Data orchestration  
  - **SAP Datasphere**: Cloud data warehousing  
  - **APIs/ETL Tools**: Custom integrations

### Workflow: SAP System → Event Log → PI  
1. Identify relevant tables (e.g., Purchase Orders)  
2. Extract via CDS Views, SAP DI, Datasphere  
3. Transform into event log format  
4. Clean and validate  
5. Upload to PI (CSV or Connector)

### Navigating SAP Signavio PI  
- **Core Areas:** Home, Analysis View, Data Upload  
- **User Flow:** Log in → Upload event log → Explore processes

### Analyzing Processes
- Review: Activity Frequency, Cycle Time, Variants  
- Key Questions: Happy path %, deviations, rework  

### Conformance Checking
- Define reference model  
- Compare against event log  
- Analyze: Conformance Rate, Deviations, Violations  

### Building Dashboards
- Include: Cycle Time, Top Variants, Conformance, Rework, Touchless Rate  
- Tools: Drag-and-drop charts, filters  
- Tip: Sketch layout before building  

### Scheduling & Automation
- **Why:** Continuous monitoring  
- **Tools:**  
  - SAP DI Pipelines  
  - SAP BTP Integration Services  
- **Concepts:**  
  - Scheduled Jobs for automatic extraction  
  - Regular data refresh in PI  
