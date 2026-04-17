# Resume–Job Matcher (GenAI + ML Pipeline)

## Overview

This project implements a multi-agent pipeline to match resumes with job descriptions using a combination of:

* Machine Learning (XGBoost)
* Semantic similarity (SBERT)
* Retrieval-Augmented Generation (FAISS)
* Generative AI (FLAN-T5)

The system evaluates candidate-job fit, identifies skill gaps, and generates explanations and recommendations.

---

##  Repository Structure

* `preprocessing/` → Resume & job description preprocessing

* `Phase2/` → Model training (feature engineering + XGBoost models)

* `Phase3/` → Full pipeline implementation (Agents 1–5) 

* `Phase4_Dashboard/` → Dashboard and visualization

* `assets/` → Required model + config files (for running pipeline)

* `main_pipeline.ipynb` → Main execution notebook

---

## Setup Instructions

### Option 1 — Google Colab (Recommended)

1. Open the repository in Colab
2. Navigate to `main_pipeline.ipynb`
3. Click `Runtime → Run all`

No manual file upload required — all necessary files are already included in the `assets/` folder.

---

### Option 2 — Local Setup

```bash
git clone https://github.com/Mahika6/genai-project.git
cd genai-project
pip install -r requirements.txt
```

Then open and run the `main_pipeline.ipynb` notebook.

---

## How It Works

The system follows a **5-agent architecture**:

1. **Agent 1 — Parsing**
   Extracts skills, experience, and education from resume and JD

2. **Agent 2 — Skill Normalization (RAG)**
   Uses FAISS to map skills to a standardized corpus

3. **Agent 3 — Semantic Matching**
   Computes similarity scores using SBERT + ML features

4. **Agent 4 — Gap Analysis**
   Identifies missing skills and experience gaps

5. **Agent 5 — Explanation & Recommendations**

   * Rule-based explanation (SHAP)
   * LLM-generated explanation (FLAN-T5)

---

## Generative AI Component

We integrate a lightweight transformer model:

* **Model:** FLAN-T5-small
* **Purpose:** Generate natural language explanations

### Note:

* Outputs are intentionally kept **raw (unfiltered)**
* This demonstrates the **true generative behavior and limitations** of small LLMs

---

## Output Includes

* Overall match score
* Section-wise scoring
* Matched and missing skills
* Rule-based explanation
* LLM-generated explanation
* Resume improvement suggestions
* ATS compatibility score

---

##  Limitations

* Small LLM produces inconsistent or low-quality outputs
* No external APIs (Gemini / Claude) used due to quota constraints
* Limited dataset for training
* Prototype-level system (not production-ready)

---

## 🚀 Future Improvements

* Integrate larger LLMs (Gemini / GPT / Claude)
* Improve prompt engineering
* Enhance output formatting
* Deploy as web application

---

## Contributors

* **Mahika** — Model training, pipeline development
* **Ranjitha** — Dashboard, streamlit UI
* **Swathi** — Dataset preprocessing, GenAI Integration

---

## Notes

All required model and configuration files are included in the `assets/` folder.
The project can be run directly without additional setup beyond installing dependencies.
