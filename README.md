<p align="center">
  <img src="assets/banner.svg" alt="Mithin Sagar — AI &amp; Machine Learning · Software Engineering · Interface Design" width="100%">
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/mithinsagar"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://huggingface.co/mithinsagar"><img src="https://img.shields.io/badge/Hugging%20Face-FFAF00?style=flat-square&logo=huggingface&logoColor=white" alt="Hugging Face"></a>
  <a href="mailto:mithinsagar@gmail.com"><img src="https://img.shields.io/badge/Email-1F2937?style=flat-square&logo=gmail&logoColor=white" alt="Email"></a>
  <img src="https://img.shields.io/badge/Chennai,%20India-334155?style=flat-square&logo=googlemaps&logoColor=white" alt="Chennai, India">
</p>

---

I build machine learning systems that can explain themselves — and the interfaces that make those explanations useful to someone who isn't an ML engineer.

I'm a Computer Science undergrad at **VIT Chennai** (AI & ML specialisation, class of 2027). I spent a summer at the **Indira Gandhi Centre for Atomic Research** replacing a manual industrial weld-inspection workflow with an end-to-end YOLOv8 pipeline, and I've presented a paper on automated AWS cost and security cleanup at **ICANDIT 2026**.

The through-line across everything below is the same, whether it's a research notebook or a game engine: a system nobody can inspect is a system nobody should trust. So my projects ship with the model *and* the dashboard, the metric *and* the interface, the paper *and* the CI pipeline.

---

## Selected work

### [Society Maintenance Tracker](https://github.com/mithinsagar/society-maintenance-tracker) &nbsp;·&nbsp; Complaint lifecycle and audit trail for residential societies

A full-stack platform where residents raise maintenance complaints with photos and track them to resolution, while the management committee triages through a strict OPEN → IN PROGRESS → RESOLVED workflow with priorities, configurable overdue detection and a permanent, append-only audit trail — enforced at the database level, not just in application code.

`Next.js 16` `TypeScript` `PostgreSQL` `Drizzle ORM` `Tailwind CSS` `Radix UI` `Vitest`

[Live demo](https://society-maintenance-tracker-two-omega.vercel.app) &nbsp;·&nbsp; [Source](https://github.com/mithinsagar/society-maintenance-tracker)

### [EXAI-ResumeIntel](https://github.com/mithinsagar/EXAI-ResumeIntel) &nbsp;·&nbsp; Explainable resume-to-role matching

Most ATS tools hand you a score. This one hands you the reasoning — Shapley values, LIME, counterfactuals and attention heatmaps that name the exact skills that earned the score, and price out what adding the missing ones would be worth. Built on a 22-skill / 346-alias ontology and SBERT embeddings over **1M+ job postings** and **2,484 real resumes**, with the Shapley and LIME implementations written from first principles rather than imported. The 6 GB of model artifacts stream from memory-mapped arrays, which is what makes it deployable at all.

Deployed live and usable in a browser.

`FastAPI` `Streamlit` `sentence-transformers` `scikit-learn` `Plotly` `Docker` `Kubernetes` `Nginx`

[Live demo](https://huggingface.co/spaces/mithinsagar/exai-resumeintel) &nbsp;·&nbsp; [Datasets](https://huggingface.co/datasets/mithinsagar/exai-resumeintel-data) &nbsp;·&nbsp; [Models](https://huggingface.co/mithinsagar/exai-resumeintel-models)

### [xai-attack-defense-framework](https://github.com/mithinsagar/xai-attack-defense-framework) &nbsp;·&nbsp; Can you make an explanation lie?

An adversarial robustness study of post-hoc explainability: can an attacker leave a security model's *prediction* untouched while corrupting the explanation the analyst reads? Across **235,795 phishing URLs**, an intrusion-detection set and a fraud corpus, four attacks against SHAP, LIME and Integrated Gradients say yes. Four defenses follow — the hybrid one cuts mean explanation drift by **91.1%** while holding classification performance. A few-shot analysis shows the problem gets 40–100% worse in the low-data regime, which is exactly where security teams operate.

`PyTorch` `SHAP` `LIME` `Captum` `XGBoost` `scikit-learn` `pytest`

### [mediXplain-disease-prediction](https://github.com/mithinsagar/mediXplain-disease-prediction) &nbsp;·&nbsp; Diagnosis you can audit

Symptom-to-diagnosis prediction across **41 conditions** and **133 symptoms**, wrapped in explainability at every layer: calibrated confidence, a ranked differential, a FAISS-retrieved evidence paragraph, and an optional LLM explanation in plain English. Seven classifiers benchmarked under 5-fold CV. If FAISS or a GPU isn't available it degrades gracefully to TF-IDF retrieval, so it runs on any laptop — and the LLM layer is optional by design, never load-bearing.

The front end is a dark-themed responsive Flask UI with live symptom search, chip selection and an animated confidence bar. No build step, no bundler.

`Flask` `scikit-learn` `FAISS` `sentence-transformers` `Jinja2` `Vanilla JS` `pytest` `GitHub Actions`

### [aws-ai-resource-cleanup](https://github.com/mithinsagar/aws-ai-resource-cleanup) &nbsp;·&nbsp; Cloud hygiene, automated

Cloud accounts accumulate ghosts: forgotten EC2 instances, orphaned EBS snapshots, stale IAM users, security groups nobody remembers opening. This scans **seven AWS resource domains**, pulls real CloudWatch utilisation, and runs a Random Forest over engineered idle-signal features to recommend *keep / review / delete* with a confidence score — falling back to a rule engine when no model is present.

Deletion is treated as the dangerous operation it is: dry-run by default, protected tags honoured, hardcoded exclusions, pre-deletion verification and a timestamped audit log. Ships with a Flask dashboard, PDF and CSV audit reports, and Lambda + EventBridge scheduling. The research behind it was presented at ICANDIT 2026.

`Boto3` `scikit-learn` `Flask` `ReportLab` `AWS Lambda` `EventBridge` `SNS` `unittest.mock`

### [StriderRunner-UnityGame](https://github.com/mithinsagar/StriderRunner-UnityGame) &nbsp;·&nbsp; A finished game, written like a library

Seven hand-built levels, nine movement abilities, fourteen trap behaviours, two enemy types — deliberately written as a clean reference codebase rather than a jam prototype. **47 C# files** across a four-layer architecture (input, simulation, presentation, persistence), where every playable character is a ScriptableObject, so adding one touches zero lines of code.

Nine UI screens with real confirmation flows, a pooled audio system that never instantiates an AudioSource at runtime, and a Unity CI pipeline that runs edit-mode and play-mode tests and produces Windows and WebGL artifacts on every push. Validated across six build targets.

`Unity 2022 LTS` `C#` `Cinemachine` `Unity Input System` `TextMesh Pro` `GitHub Actions` `Git LFS`

---

## Tech Arsenal

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![C](https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black)
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

**ML & Deep Learning**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-337AB7?style=for-the-badge&logo=xgboost&logoColor=white)
![YOLOv8](https://img.shields.io/badge/YOLOv8-00FFFF?style=for-the-badge&logo=yolo&logoColor=black)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)

**NLP & GenAI**

![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFAF00?style=for-the-badge&logo=huggingface&logoColor=white)
![BERT](https://img.shields.io/badge/BERT%20%2F%20SBERT-4285F4?style=for-the-badge&logo=google&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=for-the-badge&logo=meta&logoColor=white)
![RAG](https://img.shields.io/badge/RAG-6E48AA?style=for-the-badge&logo=openai&logoColor=white)
![LLM](https://img.shields.io/badge/LLM%20Integration-10A37F?style=for-the-badge&logo=openai&logoColor=white)

**Explainability**

![SHAP](https://img.shields.io/badge/SHAP-FF6B6B?style=for-the-badge&logo=chartdotjs&logoColor=white)
![LIME](https://img.shields.io/badge/LIME-00C853?style=for-the-badge&logo=limesurvey&logoColor=white)
![Captum](https://img.shields.io/badge/Captum-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Integrated Gradients](https://img.shields.io/badge/Integrated%20Gradients-7B61FF?style=for-the-badge&logo=tensorflow&logoColor=white)

**Backend & APIs**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=for-the-badge&logo=pydantic&logoColor=white)
![REST](https://img.shields.io/badge/REST%20API-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

**Frontend & Design**

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white)

**Cloud & DevOps**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Boto3](https://img.shields.io/badge/Boto3-FF9900?style=for-the-badge&logo=amazonwebservices&logoColor=white)

**Data**

![pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)

**Game Development**

![Unity](https://img.shields.io/badge/Unity-FFFFFF?style=for-the-badge&logo=unity&logoColor=black)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)
![Cinemachine](https://img.shields.io/badge/Cinemachine-000000?style=for-the-badge&logo=unity&logoColor=white)

---

## How I build

Every repository above follows the same discipline, and I think it's the more interesting half of the work. Packages, not scripts — modules with clear boundaries you can swap or test in isolation. Configuration in YAML with typed dataclasses, not constants buried three files deep. Test suites that run without cloud credentials, a GPU, or a 6 GB download, because a test nobody can run is documentation at best. GitHub Actions on every push. Architecture docs written for someone who isn't me.

And sensible failure modes throughout: the RAG layer falls back to TF-IDF, the recommender falls back to rules, the explanation layer falls back to a template — and the tool that deletes cloud infrastructure won't do it unless you ask twice.

---

## Recognition

- **Winner — Hack The Gap**, VIT Chennai (2025). Full-stack platform connecting underserved students to mentors and learning resources; recognised for solution design and practical impact.
- **First Runner-Up — Figma × Apple Vision Pro Design Challenge**, GDSC VIT Chennai (2023). Spatial-computing UI prototype.
- **Paper presented — ICANDIT 2026**, INTI International University, Malaysia. *Automated AWS Resource Cleanup for Optimization of Cost and Security.*
- **Outreach Head — TechnoVIT & Vibrance** (2024–25). Led a 25-member team across two flagship university festivals.
- **Certifications** — Google UX Design Professional Certificate · Introduction to Generative AI, Google Cloud (100%) · Python Data Structures, University of Michigan (97.6%)

---

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=mithinsagar&layout=compact&langs_count=8&hide=jupyter%20notebook&hide_border=true&bg_color=00000000&title_color=58A6FF&text_color=8B949E" alt="Top languages" align="right" height="150">

### Elsewhere

Away from the keyboard I shoot photography and play badminton. The photography is where most of my design instinct comes from — framing, hierarchy, and knowing what to leave out of the frame turn out to be the same problem as designing an interface.

**Open to SDE and AI/ML roles.** The fastest way to reach me is [email](mailto:mithinsagar@gmail.com) or [LinkedIn](https://www.linkedin.com/in/mithinsagar).

<br clear="right">

---

<p align="center">
  <img src="https://raw.githubusercontent.com/mithinsagar/mithinsagar/output/snake-dark.svg" alt="Contribution Snake" />
</p>

---

<p align="center">
  <img src="https://raw.githubusercontent.com/mithinsagar/mithinsagar/main/profile-3d-contrib/profile-night-rainbow.svg" alt="3D Contribution Graph" width="100%" />
</p>
