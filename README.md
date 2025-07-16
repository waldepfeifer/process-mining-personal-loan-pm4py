<img width="1469" height="258" alt="image" src="https://github.com/user-attachments/assets/a12aa242-cda0-41b5-84c7-a82e179a35b3" />


## Project Overview

This project applies process mining techniques to analyze the personal loan application process in a financial services context.  
It uses structured event log data to discover actual process flows, identify bottlenecks, check conformance, and extract performance insights.  
The notebook is built with PM4Py, a leading Python process mining library.

## Objectives

- Convert raw event data into a structured event log format
- Discover process models using Inductive Miner and Heuristics Miner
- Analyze performance: cycle times, bottlenecks, waiting times
- Check conformance between expected and actual process flows
- Visualize key business insights for operational improvement

## Technologies Used

- Python 3.x
- PM4Py
- pandas
- matplotlib
- seaborn
- datetime

## Project Structure

personal-loan-process-mining-pm4py/  
├── personal_loan_process_mining_workflow.ipynb   – Main Jupyter notebook  
├── loan_application_event_log.csv                – Sample structured event log file  
├── README.md                                     – Project documentation  

## Dataset Description

The dataset captures loan application events with the following structure:

- case_id: Unique ID for each application process
- activity: Business step (e.g., submit_application, funding_complete)
- timestamp: Event timestamp
- [optional attributes]: Additional fields like loan_amount, user_id, region

## Process Mining Techniques Demonstrated

- **Process Discovery**  
  Using PM4Py to reconstruct process models from event logs.

- **Performance Analysis**  
  - Cycle time measurement  
  - Bottleneck detection  
  - Waiting time analysis  

- **Conformance Checking**  
  Comparing the discovered model with expected models and quantifying deviations.

- **Variant and Frequency Analysis**  
  Identifying the most common process variants in the loan application workflow.

## How to Use

1. Install requirements:
   pip install pm4py pandas matplotlib seaborn

2. Open the notebook in Jupyter:
   personal_loan_process_mining_workflow.ipynb

3. Upload your structured event log CSV file.

4. Run the cells step-by-step to visualize discovered models, conformance results, and performance charts.

## Example Outputs

- Discovered process model visualizations
- Variant frequency charts
- Cycle time distributions
- Bottleneck heatmaps
- Conformance matrices

## Requirements

pip install pm4py pandas matplotlib seaborn

## License

This project is licensed under the MIT License. See the LICENSE file for details.
