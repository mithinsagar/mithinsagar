<p align="center">
  <img src="assets/banner.svg" alt="Mithin Sagar — AI &amp; Machine Learning · Software Engineering · Interface Design" width="100%">
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/mithinsagar"><img src="https://img.shields.io/badge/LinkedIn-0A0F1D?style=flat-square&logo=linkedin&logoColor=0A66C2" alt="LinkedIn"></a>
  <a href="https://huggingface.co/mithinsagar"><img src="https://img.shields.io/badge/Hugging%20Face-0A0F1D?style=flat-square&logo=huggingface&logoColor=FFD21E" alt="Hugging Face"></a>
  <a href="mailto:mithinsagar@gmail.com"><img src="https://img.shields.io/badge/Email-0A0F1D?style=flat-square&logo=gmail&logoColor=EA4335" alt="Email"></a>
  <img src="https://img.shields.io/badge/Chennai,%20India-0A0F1D?style=flat-square&logo=googlemaps&logoColor=34A853" alt="Chennai, India">
</p>

I build machine learning systems that can explain themselves — and the interfaces that make those explanations useful to someone who isn't an ML engineer.

Computer Science undergrad at **VIT Chennai** (AI & ML, class of 2027). I spent a summer at the **Indira Gandhi Centre for Atomic Research** replacing a manual industrial weld-inspection workflow with an end-to-end YOLOv8 pipeline, and presented a paper on automated AWS cost and security cleanup at **ICANDIT 2026**.

The through-line, whether it's a research notebook or a game engine: a system nobody can inspect is a system nobody should trust. So everything below ships with the model *and* the dashboard, the metric *and* the interface.

---

## Selected work

#### [FlashForensics AI](https://github.com/mithinsagar/flashforensics-ai) · agentic recovery for corrupted flash storage

Reads a damaged SD card sector by sector, rebuilds the files its index lost, and says which ones will actually open — with the evidence behind every verdict. It ships with a card it damages on purpose and a manifest of exactly what it did, so every run is graded against ground truth in the browser: **100% recall, zero false positives** across 25 planted files.

`Python` `FastAPI` `LangGraph` `ChromaDB` `Next.js` `TypeScript` `Docker`

[![Live demo](https://img.shields.io/badge/Live%20demo-6366F1?style=flat-square)](https://frontend-mithin-sagar.vercel.app) [![Source](https://img.shields.io/badge/Source-0A0F1D?style=flat-square&logo=github&logoColor=white)](https://github.com/mithinsagar/flashforensics-ai)

#### [EXAI-ResumeIntel](https://github.com/mithinsagar/EXAI-ResumeIntel) · explainable resume-to-role matching

Most ATS tools hand you a score. This one hands you the reasoning — Shapley values, LIME, counterfactuals and attention heatmaps that name the exact skills which earned the score, then price out what adding the missing ones is worth. Built on SBERT embeddings over **1M+ job postings** and **2,484 real resumes**, with the Shapley and LIME implementations written from first principles and 6 GB of model artifacts streamed from memory-mapped arrays.

`FastAPI` `Streamlit` `sentence-transformers` `scikit-learn` `Plotly` `Docker` `Kubernetes`

[![Live demo](https://img.shields.io/badge/Live%20demo-6366F1?style=flat-square)](https://huggingface.co/spaces/mithinsagar/exai-resumeintel) [![Source](https://img.shields.io/badge/Source-0A0F1D?style=flat-square&logo=github&logoColor=white)](https://github.com/mithinsagar/EXAI-ResumeIntel) [![Datasets](https://img.shields.io/badge/Datasets-0A0F1D?style=flat-square&logo=huggingface&logoColor=FFD21E)](https://huggingface.co/datasets/mithinsagar/exai-resumeintel-data) [![Models](https://img.shields.io/badge/Models-0A0F1D?style=flat-square&logo=huggingface&logoColor=FFD21E)](https://huggingface.co/mithinsagar/exai-resumeintel-models)

#### [Society Maintenance Tracker](https://github.com/mithinsagar/society-maintenance-tracker) · complaint lifecycle and audit trail

Residents raise maintenance complaints with photos and follow them to resolution, while the committee triages through a strict OPEN → IN PROGRESS → RESOLVED workflow with priorities and configurable overdue detection. The audit trail is append-only and enforced at the database level, not merely in application code.

`Next.js 16` `TypeScript` `PostgreSQL` `Drizzle ORM` `Tailwind CSS` `Radix UI` `Vitest`

[![Live demo](https://img.shields.io/badge/Live%20demo-6366F1?style=flat-square)](https://society-maintenance-tracker-two-omega.vercel.app) [![Source](https://img.shields.io/badge/Source-0A0F1D?style=flat-square&logo=github&logoColor=white)](https://github.com/mithinsagar/society-maintenance-tracker)

#### [xai-attack-defense-framework](https://github.com/mithinsagar/xai-attack-defense-framework) · can you make an explanation lie?

An adversarial study of post-hoc explainability: can an attacker leave a security model's *prediction* untouched while corrupting the explanation the analyst reads? Across **235,795 phishing URLs**, an intrusion-detection set and a fraud corpus, four attacks on SHAP, LIME and Integrated Gradients say yes — and of the four defenses that follow, the hybrid one cuts mean explanation drift by **91.1%** while holding classification performance.

`PyTorch` `SHAP` `LIME` `Captum` `XGBoost` `scikit-learn` `pytest`

[![Source](https://img.shields.io/badge/Source-0A0F1D?style=flat-square&logo=github&logoColor=white)](https://github.com/mithinsagar/xai-attack-defense-framework)

#### [mediXplain](https://github.com/mithinsagar/mediXplain-disease-prediction) · diagnosis you can audit

Symptom-to-diagnosis prediction across **41 conditions** and **133 symptoms**, with calibrated confidence, a ranked differential and a FAISS-retrieved evidence paragraph behind every prediction. It degrades to TF-IDF retrieval when FAISS or a GPU isn't available, so it runs on any laptop, and the LLM explanation layer is optional by design — never load-bearing.

`Flask` `scikit-learn` `FAISS` `sentence-transformers` `Vanilla JS` `pytest` `GitHub Actions`

[![Source](https://img.shields.io/badge/Source-0A0F1D?style=flat-square&logo=github&logoColor=white)](https://github.com/mithinsagar/mediXplain-disease-prediction)

#### [aws-ai-resource-cleanup](https://github.com/mithinsagar/aws-ai-resource-cleanup) · cloud hygiene, automated

Scans **seven AWS resource domains**, pulls real CloudWatch utilisation, and runs a Random Forest over engineered idle-signal features to recommend *keep / review / delete* with a confidence score — falling back to a rule engine when no model is present. Deletion is treated as the dangerous operation it is: dry-run by default, protected tags honoured, pre-deletion verification and a timestamped audit log.

`Boto3` `scikit-learn` `Flask` `ReportLab` `AWS Lambda` `EventBridge` `SNS`

[![Source](https://img.shields.io/badge/Source-0A0F1D?style=flat-square&logo=github&logoColor=white)](https://github.com/mithinsagar/aws-ai-resource-cleanup)

#### [StriderRunner](https://github.com/mithinsagar/StriderRunner-UnityGame) · a finished game, written like a library

Seven hand-built levels, nine movement abilities, fourteen trap behaviours — deliberately written as a clean reference codebase rather than a jam prototype. **47 C# files** across a four-layer architecture, where every playable character is a ScriptableObject, so adding one touches zero lines of code; Unity CI runs edit-mode and play-mode tests and ships Windows and WebGL builds on every push.

`Unity 2022 LTS` `C#` `Cinemachine` `Unity Input System` `GitHub Actions` `Git LFS`

[![Source](https://img.shields.io/badge/Source-0A0F1D?style=flat-square&logo=github&logoColor=white)](https://github.com/mithinsagar/StriderRunner-UnityGame)

---

## Toolkit

**Languages**<br>
![Python](https://img.shields.io/badge/Python-0A0F1D?style=flat-square&logo=python&logoColor=3776AB)
![C++](https://img.shields.io/badge/C%2B%2B-0A0F1D?style=flat-square&logo=cplusplus&logoColor=00599C)
![C](https://img.shields.io/badge/C-0A0F1D?style=flat-square&logo=c&logoColor=A8B9CC)
![Java](https://img.shields.io/badge/Java-0A0F1D?style=flat-square&logo=openjdk&logoColor=ED8B00)
![C#](https://img.shields.io/badge/C%23-0A0F1D?style=flat-square&logo=csharp&logoColor=239120)
![TypeScript](https://img.shields.io/badge/TypeScript-0A0F1D?style=flat-square&logo=typescript&logoColor=3178C6)
![JavaScript](https://img.shields.io/badge/JavaScript-0A0F1D?style=flat-square&logo=javascript&logoColor=F7DF1E)
![SQL](https://img.shields.io/badge/SQL-0A0F1D?style=flat-square&logo=postgresql&logoColor=4479A1)

**Machine learning & explainability**<br>
![PyTorch](https://img.shields.io/badge/PyTorch-0A0F1D?style=flat-square&logo=pytorch&logoColor=EE4C2C)
![TensorFlow](https://img.shields.io/badge/TensorFlow-0A0F1D?style=flat-square&logo=tensorflow&logoColor=FF6F00)
![Keras](https://img.shields.io/badge/Keras-0A0F1D?style=flat-square&logo=keras&logoColor=D00000)
![scikit-learn](https://img.shields.io/badge/scikit--learn-0A0F1D?style=flat-square&logo=scikitlearn&logoColor=F7931E)
![XGBoost](https://img.shields.io/badge/XGBoost-0A0F1D?style=flat-square&logo=xgboost&logoColor=337AB7)
![OpenCV](https://img.shields.io/badge/OpenCV-0A0F1D?style=flat-square&logo=opencv&logoColor=5C3EE8)
![YOLOv8](https://img.shields.io/badge/YOLOv8-0A0F1D?style=flat-square&logo=yolo&logoColor=00FFFF)
![SHAP](https://img.shields.io/badge/SHAP-0A0F1D?style=flat-square&logo=chartdotjs&logoColor=FF6B6B)
![LIME](https://img.shields.io/badge/LIME-0A0F1D?style=flat-square&logo=limesurvey&logoColor=00C853)
![Captum](https://img.shields.io/badge/Captum-0A0F1D?style=flat-square&logo=pytorch&logoColor=EE4C2C)

**Retrieval, NLP & agents**<br>
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-0A0F1D?style=flat-square&logo=huggingface&logoColor=FFD21E)
![SBERT](https://img.shields.io/badge/BERT%20%2F%20SBERT-0A0F1D?style=flat-square&logo=google&logoColor=4285F4)
![FAISS](https://img.shields.io/badge/FAISS-0A0F1D?style=flat-square&logo=meta&logoColor=0467DF)
![ChromaDB](https://img.shields.io/badge/ChromaDB-0A0F1D?style=flat-square)
![LangGraph](https://img.shields.io/badge/LangGraph-0A0F1D?style=flat-square&logo=langchain&logoColor=1C6E64)

**Backend & data**<br>
![FastAPI](https://img.shields.io/badge/FastAPI-0A0F1D?style=flat-square&logo=fastapi&logoColor=009688)
![Flask](https://img.shields.io/badge/Flask-0A0F1D?style=flat-square&logo=flask&logoColor=FFFFFF)
![Streamlit](https://img.shields.io/badge/Streamlit-0A0F1D?style=flat-square&logo=streamlit&logoColor=FF4B4B)
![Pydantic](https://img.shields.io/badge/Pydantic-0A0F1D?style=flat-square&logo=pydantic&logoColor=E92063)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-0A0F1D?style=flat-square&logo=postgresql&logoColor=4169E1)
![MongoDB](https://img.shields.io/badge/MongoDB-0A0F1D?style=flat-square&logo=mongodb&logoColor=47A248)
![pandas](https://img.shields.io/badge/pandas-0A0F1D?style=flat-square&logo=pandas&logoColor=8A5CF6)
![NumPy](https://img.shields.io/badge/NumPy-0A0F1D?style=flat-square&logo=numpy&logoColor=4DABCF)

**Frontend & design**<br>
![Next.js](https://img.shields.io/badge/Next.js-0A0F1D?style=flat-square&logo=nextdotjs&logoColor=FFFFFF)
![React](https://img.shields.io/badge/React-0A0F1D?style=flat-square&logo=react&logoColor=61DAFB)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-0A0F1D?style=flat-square&logo=tailwindcss&logoColor=06B6D4)
![Plotly](https://img.shields.io/badge/Plotly-0A0F1D?style=flat-square&logo=plotly&logoColor=636EFA)
![Figma](https://img.shields.io/badge/Figma-0A0F1D?style=flat-square&logo=figma&logoColor=F24E1E)

**Cloud, DevOps & tooling**<br>
![AWS](https://img.shields.io/badge/AWS-0A0F1D?style=flat-square&logo=amazonwebservices&logoColor=FF9900)
![Docker](https://img.shields.io/badge/Docker-0A0F1D?style=flat-square&logo=docker&logoColor=2496ED)
![Kubernetes](https://img.shields.io/badge/Kubernetes-0A0F1D?style=flat-square&logo=kubernetes&logoColor=326CE5)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-0A0F1D?style=flat-square&logo=githubactions&logoColor=2088FF)
![Nginx](https://img.shields.io/badge/Nginx-0A0F1D?style=flat-square&logo=nginx&logoColor=009639)
![Vercel](https://img.shields.io/badge/Vercel-0A0F1D?style=flat-square&logo=vercel&logoColor=FFFFFF)
![Unity](https://img.shields.io/badge/Unity-0A0F1D?style=flat-square&logo=unity&logoColor=FFFFFF)

---

## How I build

Packages, not scripts — modules with clear boundaries you can swap or test in isolation. Configuration in YAML with typed dataclasses, not constants buried three files deep. Test suites that run without cloud credentials, a GPU or a 6 GB download, because a test nobody can run is documentation at best.

And sensible failure modes throughout: the RAG layer falls back to TF-IDF, the recommender falls back to rules, the explanation layer falls back to a template — and the tool that deletes cloud infrastructure won't do it unless you ask twice.

---

## Recognition

**Winner — Hack The Gap**, VIT Chennai (2025) · full-stack platform connecting underserved students to mentors, recognised for solution design and practical impact<br>
**First Runner-Up — Figma × Apple Vision Pro Design Challenge**, GDSC VIT Chennai (2023) · spatial-computing UI prototype<br>
**Paper presented — ICANDIT 2026**, INTI International University, Malaysia · *Automated AWS Resource Cleanup for Optimization of Cost and Security*<br>
**Outreach Head — TechnoVIT & Vibrance** (2024–25) · led a 25-member team across two flagship university festivals<br>
**Certifications** · Google UX Design Professional Certificate · Introduction to Generative AI, Google Cloud (100%) · Python Data Structures, University of Michigan (97.6%)

---

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=mithinsagar&layout=compact&langs_count=8&hide=jupyter%20notebook&hide_border=true&bg_color=00000000&title_color=22D3EE&text_color=8B949E" alt="Top languages" align="right" height="150">

### Elsewhere

Away from the keyboard I shoot photography and play badminton. The photography is where most of my design instinct comes from — framing, hierarchy and knowing what to leave out of the frame turn out to be the same problem as designing an interface.

**Open to SDE and AI/ML roles.** The fastest way to reach me is [email](mailto:mithinsagar@gmail.com) or [LinkedIn](https://www.linkedin.com/in/mithinsagar).

<br clear="right">

<p align="center">
  <img src="https://raw.githubusercontent.com/mithinsagar/mithinsagar/output/snake-dark.svg" alt="Contribution graph" width="100%" />
</p>
