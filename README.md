# AI-Driven-Odoo-Project-Reporting-Agent-n8n-Workflow-
An autonomous AI Agent built in n8n that queries Odoo ERP for project metadata, tasks, and timesheets, dynamically converts the unstructured data into formatted records, and generates an executive PDF project report delivered via Telegram.
## 🎯 Problem Solved
Compiling project progress reports, cross-referencing timesheets, and updating clients or managers on task statuses from Odoo usually requires tedious manual data filtering and export formatting. 

This workflow deploys a conversational **AI Agent** capable of:
1. **Natural Language Processing:** Understanding user requests for specific project reports via chat.
2. **Autonomous Tool Calling:** Interrogating Odoo ERP modules (`project.project`, `project.task`, and timesheets) to extract related data using dynamic ID resolution.
3. **Automated ETL & Reporting:** Using custom JavaScript to normalize fields, casting complex tuple structures (like Odoo's dynamic `stage_id` or `employee_id`), converting the outcome into clean HTML-to-PDF templates, and shipping the PDF report instantly.

---

## ⚡ Workflow Architecture
[ User Request via Telegram ]
↓
[ n8n AI Agent Executor ]
↓  (Autonomous Tool Calls)
[ Query Odoo ERP Modules ] -> Project / Tasks / Timesheets
↓
[ JavaScript Data Transformer ] -> JSON Normalization & Type Casting
↓
[ HTML to PDF Generator ] -> Dynamic Document Compilation
↓
[ Telegram Document Sender ] -> instant Executive PDF Delivery


---

## 🔧 Tech Stack
| Tool | Role |
| :--- | :--- |
| **n8n Advanced AI** | Agent orchestration, tool calling framework, and system instruction guardrails |
| **OpenAI (GPT Models)** | The core LLM powering the agent's database querying reasoning |
| **Odoo ERP API** | Target system of record for project management tracking |
| **Puppeteer / HTML-to-PDF** | Document generation engine for rendering charts and structured tables |
| **Telegram Bot API** | Seamless user interface for report requests and PDF document distribution |

---

## 📋 Key Logic & Data Transformations
* **🧠 Strict JSON Formatting Guardrails:** The agent's system prompt enforces a zero-text, raw JSON-only payload extraction from Odoo to ensure programmatic safety down the pipeline.
* **🔧 Tuple Mapping & Resolution:** Custom JavaScript code automatically transforms typical Odoo database arrays (e.g., converting `[4, "Done"]` into `"Done"`) and maps project stages into binary states (`Done` vs `In Progress`).
* **📁 Dynamic PDF Compilation:** Seamlessly injects the cleaned dataset into structured HTML layouts to output beautifully styled corporate PDFs.

---

## 🚀 Setup Instructions

### Prerequisites
* n8n instance (Self-hosted or Cloud) with **Advanced AI** nodes and custom file binaries enabled.
* Odoo ERP Instance with Project and Timesheet tracking modules installed.
* OpenAI API Key (or a similar compatible LLM credential).
* Telegram Bot Token for report ingestion and dispatching.

### Steps to Deploy
1.  **Import:** Download and import `Odoo_Project_Reporting_Agent.json` into your n8n workspace.
2.  **Configure API Access:** Input your Telegram Bot Token, OpenAI Key, and Odoo ERP endpoint credentials in their respective nodes.
3.  **Adjust System Message:** Customize the target system instructions inside the AI Agent node if your Odoo instance utilizes non-standard custom project tracking variables.
4.  **Style Your Report:** Open the JavaScript/HTML node to inject your corporate branding styles, logos, or customized data tables for the PDF output.
5.  **Test:** Fire up your Telegram Bot, ask it for a project summary, and watch it generate and reply with the complete executive PDF report.

---

## 📁 Repository Structure
```bash
odoo-project-reporting-agent/
├── Odoo_Project_Reporting_Agent.json # The clean n8n reporting agent workflow file (Import this)
├── reporting-pipeline-canvas.png    # Visual screenshot of the automated ETL and PDF render pipeline
└── README.md                         # Project documentation
👤 Author
Asem Ahmed — AI Automation Engineer
