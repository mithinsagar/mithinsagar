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

## Toolkit

|  |  |
| :--- | :--- |
| **Languages** | Python · C++ · C · Java · C# · JavaScript · SQL |
| **ML & Deep Learning** | PyTorch · TensorFlow · Keras · scikit-learn · XGBoost · YOLOv8 · OpenCV |
| **NLP & GenAI** | Hugging Face Transformers · BERT / SBERT · FAISS · RAG · LLM integration |
| **Explainability** | SHAP · LIME · Integrated Gradients · Captum |
| **Backend & APIs** | Flask · FastAPI · Streamlit · Pydantic · REST · Jinja2 |
| **Frontend & Design** | HTML5 · CSS3 · JavaScript · Plotly · Responsive UI · Figma |
| **Cloud & DevOps** | AWS (EC2, S3, IAM, Lambda, EventBridge, CloudWatch, SNS) · Boto3 · Docker · Kubernetes · Nginx · GitHub Actions |
| **Data** | pandas · NumPy · MongoDB · SQL |
| **Game Development** | Unity 2022 LTS · Cinemachine · Unity Input System |

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
