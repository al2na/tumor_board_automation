# 🩺 AI Tumor Board Simulation

---

An automated, multi-agent multidisciplinary tumor-board workflow for **2ndOpinion Desktop**. This workflow processes patient history, pathology, radiology, and surgical/procedural information, generates focused questions for different clinical specialists, allows each specialist agent to independently evaluate the case, and combines their conclusions into a structured multidisciplinary oncology synthesis.

## 📌 About This Automation

The **Tumor Board Simulation** automation performs a structured, multi-stage evaluation of an oncology case:

1. **Clinical Case Summarization:** Combines the patient history, pathology report, radiology report, and diagnostic surgery/procedural report into a concise structured case summary while preserving important uncertainties, measurements, dates, and findings.

2. **Lead Oncologist Question Generation:** A Lead Oncologist agent reviews the case summary and the original tumor-board question, then generates focused questions for the Pathologist, Surgeon, and Radiologist based on what each specialty can uniquely clarify.

3. **Specialist Review:** Three independent specialist agents evaluate the case:

   * **Pathologist:** Reviews diagnosis, differential diagnosis, biomarkers, molecular findings, specimen adequacy, and pathology-specific uncertainties.
   * **Surgeon:** Evaluates technical feasibility, oncological role of surgery, potential surgical approaches, risks, and information required before a surgical decision.
   * **Radiologist:** Reviews disease distribution, imaging findings, staging-relevant features, treatment-relevant anatomy, and additional imaging or sampling that may be required.

4. **PubMed Evidence Search:** Specialist agents can use PubMed when external literature is useful for answering their assigned question, interpreting findings, evaluating diagnostic or treatment-related evidence, or identifying important limitations.

5. **Final Multidisciplinary Synthesis:** An Oncology Integrator combines the specialist conclusions and responds directly to the original tumor-board question. The workflow explicitly classifies the case as:

   * **DECISION-READY**
   * **CONDITIONALLY DECISION-READY**
   * **NOT DECISION-READY**

## 🚀 How to Use

### Step 1: Install 2ndOpinion Desktop

1. Download and install **[2ndOpinion Desktop](https://2ndopin.io/desktop)** for macOS or Windows.
2. Launch 2ndOpinion and navigate to the **Automations** tab from the main sidebar.

### Step 2: Import the Automation

1. Download `Tumor_board_simulation.automation.json` [link](ADD_AUTOMATION_LINK) from this repository.
2. In 2ndOpinion Desktop, click **Import Automation** (or the **Import** button in the Automations sidebar).
3. Select `Tumor_board_simulation.automation.json` to load the workflow onto the automation canvas.

### Step 3: Provide the Case Information

The workflow expects the following inputs:

1. **Patient History**
2. **Pathology Report**: Can include molecular biomarkers and other molecular testing.
3. **Radiology Report**
4. **Diagnostic Surgery / Procedural Report**
5. **Query to the Tumor Board**

   * The specific clinical question you want the simulated multidisciplinary team to address.

For best results, provide the relevant reports as complete text while preserving dates, measurements, anatomical locations, pathology terminology, and qualifying language such as *possible*, *suspicious*, *indeterminate*, or *cannot exclude*.

### Step 4: Run the Automation

1. Switch to **Run Mode** on the automation canvas.
2. Enter the required clinical information into the corresponding input nodes.
3. Enter the specific question you want the tumor board to address in the **Query to the tumor board** input.
4. Click **Run** to execute the workflow.
5. Review the specialist outputs and the final multidisciplinary synthesis.

## 🧠 Workflow Structure

The workflow follows this general sequence:

`Clinical Inputs → Case Summary → Lead Oncologist → Specialist Questions → Pathologist / Surgeon / Radiologist → Final Oncology Synthesis`

The Lead Oncologist does **not** independently answer the tumor-board question. Instead, it determines which uncertainties should be addressed by each specialist.

The specialist agents then independently answer their assigned questions within the limits of their specialty.

The final Oncology Integrator combines these outputs without silently resolving disagreements or inventing missing patient-specific information.

## 📚 Literature Search

The following specialist agents have access to PubMed:

* **Pathologist**
* **Surgeon**
* **Radiologist**

PubMed may be used when literature can help clarify diagnostic criteria, imaging approaches, surgical evidence, biomarkers, treatment-relevant pathology, or other specialist-specific questions.

The **Lead Oncologist** and **Final Oncology Integrator** do not perform independent PubMed searches.

This separation is intentional: literature evaluation occurs within the relevant specialty, while the final node focuses on integrating the outputs already produced by the multidisciplinary team.

## 📊 Example Results

A sample execution report can be added to this repository to demonstrate the complete workflow on a synthetic or appropriately de-identified oncology case.

Example:

**[Tumor_board_simulation_Execution_Report.md](./Tumor_board_simulation_Execution_Report.md)**



## ⚠️ Clinical Use and Privacy

This workflow is a **simulated multidisciplinary tumor-board system** and is not a substitute for review by qualified clinicians.

The final synthesis explicitly states that it requires review by the accountable treating clinicians before use in patient care.

The workflow is currently configured to allow cloud-based models. Before entering real patient information, make sure your deployment, model configuration, and data-handling procedures comply with applicable institutional policies, privacy requirements, and regulations.

For testing and demonstration purposes, synthetic or appropriately de-identified cases are recommended.

## ⚙️ Metadata

* **Format:** `2ndopinion-automation` (v1.0)
* **Workflow Name:** `Tumor board simulation`
* **Tools Enabled:** `pubmed-search`
* **Model Policy:** `cloud_allowed`

## ⚠️ Disclaimer

This automation is intended for research, experimentation, education, and clinical decision-support exploration.

It does not provide autonomous medical advice and should not be used as a replacement for a multidisciplinary tumor board, specialist consultation, or accountable clinical decision making.

All outputs should be reviewed against the original clinical records and independently evaluated by qualified healthcare professionals.
