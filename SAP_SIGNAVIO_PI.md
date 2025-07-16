# SAP Signavio PI Basics + Integration Knowledge

### What Is SAP Signavio PI?  
Cloud-based process mining tool for analyzing, monitoring, and optimizing business processes using event logs.

**Core Functions:**  
- Upload/manage event logs  
- Visualize processes and variants  
- Analyze performance and conformance  
- Build dashboards  

**Key Terms:**  
Process Explorer, Variants, Conformance, Case Attributes

---

### SAP Systems for Process Mining  

| System         | Purpose/Use Case                |
|----------------|---------------------------------|
| S/4HANA        | Modern ERP (P2P, O2C)          |
| SAP ECC        | Legacy ERP                      |
| Ariba          | Procurement                     |
| SuccessFactors | HR processes (Hire-to-Retire)   |

---

### Data Extraction Methods  

- **Direct Connectors:** SAP BTP integration services (preferred)  
- **Manual Extraction:** CDS Views, SAP DI, Datasphere, CSV  

When manual? Legacy/custom processes.

---

### Tools Overview  

| Tool              | Function                         |
|-------------------|---------------------------------|
| CDS Views         | Pre-built queries               |
| SAP DI            | Data orchestration/transformation |
| SAP Datasphere    | Data warehouse                  |
| ETL Tools/APIs    | General extraction  

---

### From SAP System to PI: 5 Steps  

1. Identify relevant tables (e.g., Purchase Orders)  
2. Extract using CDS Views/SAP DI  
3. Transform: Case ID, Activity, Timestamp, Attributes  
4. Clean and validate data  
5. Upload to PI (CSV or Connector)  

---

### Navigating SAP Signavio PI  

**Key Areas:** Home, Analysis View, Data Upload  
**User Flow:** Log in → Upload event log → Explore  

---

### Uploading Event Logs  

- Format: Case ID, Activity, Timestamp, Attributes  
- Validate: No missing/invalid values  
- Upload: Create Analysis → Upload CSV → Map Fields  

---

### Analyzing Processes in PI  

- Use Process Explorer  
- Review: Activity Frequency, Cycle Time, Variants  
- Typical Questions: Happy path %, deviations, rework  

---

### Conformance Checking  

- Define reference model  
- Compare event log  
- Analyze: Conformance Rate, Deviations, Violations  

---

### Building Dashboards  

**Include:**  
- Cycle Time, Top Variants, Conformance, Rework, Touchless Rate  
**Tools:**  
- Drag-and-drop dashboards, filters  
**Tip:** Sketch before building.

---

### Scheduling and Automation  

- Scheduled Jobs: Automatic extractions  
- Data Refresh in PI  
- Tools: SAP DI Pipelines, SAP BTP
