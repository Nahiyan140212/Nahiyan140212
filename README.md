<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1e3a5f,100:0d9488&height=180&section=header&text=Nahiyan%20Bin%20Noor&fontSize=44&fontColor=ffffff&fontAlignY=32&desc=GenAI%20Research%20Scientist%20%7C%20Healthcare%20Data%20Scientist&descSize=16&descAlignY=52" width="100%" alt=""/>

<p align="center">
  <a href="https://www.linkedin.com/in/nahiyan-bin-noor-0a2170158/"><img src="https://img.shields.io/badge/LinkedIn-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="https://scholar.google.com/citations?user=GwgCEz8AAAAJ&hl=en"><img src="https://img.shields.io/badge/Google%20Scholar-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white" alt="Google Scholar"/></a>
  <a href="https://nahiyan.sharedskillet.com"><img src="https://img.shields.io/badge/Portfolio-%23000000.svg?style=for-the-badge&logo=firefox&logoColor=%23FF7139" alt="Portfolio"/></a>
  <a href="mailto:nahiyan.cuet@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"/></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Dallas,%20TX-475569?style=flat-square" alt="Dallas, TX"/>
  <img src="https://img.shields.io/badge/US%20Permanent%20Resident-no%20sponsorship%20needed-475569?style=flat-square" alt="US Permanent Resident"/>
  <img src="https://img.shields.io/badge/19%20publications-200%2B%20citations-475569?style=flat-square" alt="19 publications, 200+ citations"/>
  <img src="https://img.shields.io/badge/h--index-7-475569?style=flat-square" alt="h-index 7"/>
</p>

---

## About

Most healthcare data problems are actually two problems. The numbers live in a database. The reasoning lives in a note nobody has time to read.

I work on both, and that combination is rarer than it should be.

I build production AI systems on healthcare data, from SQL feature pipelines on claims warehouses to fine-tuned clinical LLMs and retrieval systems that survive contact with real users. I also publish, which means I care about whether a number holds up under scrutiny and not just whether the demo runs.

| | |
|---|---|
| **Now** | Data Scientist, U.S. Department of Veterans Affairs &nbsp;·&nbsp; Intermediate Data Analyst, UAMS College of Pharmacy |
| **Finishing** | PhD in Biomedical Informatics, UAMS (expected 2026) |
| **Looking for** | GenAI Research Scientist, AI/ML Engineer, and Data Scientist roles in DFW or remote |
| **Also** | Co-founder and Chief Research Officer, [ResearchBuddy AI](https://researchbuddy.tech) |

---

## Contents

[Selected work](#selected-work) &nbsp;·&nbsp; [Pinned repositories](#pinned-repositories) &nbsp;·&nbsp; [Research](#research) &nbsp;·&nbsp; [Tech stack](#tech-stack) &nbsp;·&nbsp; [Publications](#publications-and-certifications) &nbsp;·&nbsp; [Activity](#activity) &nbsp;·&nbsp; [Contact](#contact)

---

## Selected work

### Production RAG for healthcare contract compliance

Built and deployed a retrieval system over two client contract corpora totaling 35,000+ documents at Cotiviti. Contract review dropped from days to minutes. Stakeholders projected roughly $8M in annual savings, which is their estimate and not a measured result.

> **The finding worth repeating:** generation was never the bottleneck. Once retrieved chunks were accurate, answers were reliable. Every meaningful quality gain came from retrieval. Most people building RAG spend their effort on prompts and generation model choice.

<details>
<summary><b>How it was built</b></summary>

<br>

**Ingestion.** Over 70% of the first corpus was scanned or photocopied PDFs with no selectable text. I benchmarked PaddleOCR and other open-source options against a GPT vision model. The vision model won and removed the need to host OCR infrastructure at all.

**Format handling.** An adapter layer normalized scanned PDFs, native PDFs, Excel rate sheets, DOC, and DOCX into per-client ChromaDB collections, keeping each client's contracts isolated from the other's results.

**Ground truth from nothing.** No evaluation set existed. I worked with stakeholders to define the 14 contract attributes auditors actually care about (provider name, NPI, tax ID, DRG, CPT, HCPCS, and others), sampled 720 pages from 4,236, extracted labels via probabilistic, deterministic, and LLM-assisted methods, then manually validated every page.

**Retrieval.** Hybrid lexical and semantic search through a LangChain ensemble retriever weighted 0.7 semantic to 0.3 lexical, with E5-Mistral embeddings and `gpt-4.1-mini` handling reranking and redundancy filtering.

**Evaluation.** 73% F1@10 on retrieval against the labeled ground truth (client 1). Generation quality on the second corpus scored 2.5 out of 3 via LLM-as-judge citation review with parallel human review (client 2). These are separate corpora and the metrics do not transfer between them.

**Deployment.** Streamlit on AWS EC2 behind an ALB and Route 53 with feedback capture to S3, later migrated to Databricks.

*Code is proprietary and not published here.*

</details>

### Veteran risk stratification

Improved identification of high-risk veterans from a 50% baseline to F1 0.88 (AUC-ROC 0.76) with a Gradient Boosting model in Python on VA Corporate Data Warehouse time-series and claims data. Deployed clinical decision support dashboards in Power BI for real-time risk stratification.

### ResearchBuddy AI

Most students who want to do research never get the chance, not for lack of ability but for lack of access to a supervisor. ResearchBuddy AI is an AI-powered virtual lab connecting 2,000+ researchers with 100+ supervisors worldwide. I co-founded it in 2025. [researchbuddy.tech](https://researchbuddy.tech)

---

## Pinned repositories

| Repository | What it does | Stack |
|---|---|---|
| [**End-to-End RAG Application**](https://github.com/Nahiyan140212/End-to-End-RAG-Application-Deployment) | Document question answering with a modular pipeline: chunking, embedding, FAISS retrieval, and generation, each swappable so the effect of changing one stage can be isolated. | Python, FAISS, OpenAI |
| [**Predicting Dropout from MOUD**](https://github.com/Nahiyan140212/Predicting-Dropout-from-Medication-for-Opioid-Use-Disorder) | Predicts retention in medication for opioid use disorder treatment, combining machine learning with statistical modeling to identify patients at risk of dropping out. | Python, scikit-learn |
| [**Anemia Detection from Conjunctiva Images**](https://github.com/Nahiyan140212/Detection-of-Anemia-from-Eye-Conjunctiva-Images-using-Deep-Learning) | Screens for anemia from a photograph of the eye conjunctiva. A user uploads a cropped image and the model returns a prediction. Non-invasive screening for settings where bloodwork is not available. | Python, deep learning, computer vision |
| [**Chest Disease Classification from CT**](https://github.com/Nahiyan140212/Chest-Disease-Classification-from-Chest-CT-Scan-Image) | Classifies chest disease from CT scan images through an end-to-end training and inference pipeline. | Jupyter, deep learning |
| [**MediGuide AI**](https://github.com/Nahiyan140212/MediGuide-AI) | TODO: one sentence on what it does and who it is for. | Jupyter |
| [**SharedSkillet**](https://github.com/Nahiyan140212/SharedSkillet) | TODO: one sentence on what it does and who it is for. | HTML |

---

## Research

| Project | What it does | Result |
|---|---|---|
| **Clinical substance use detection** | Meditron3-8B fine-tuned via QLoRA across 8 substance labels on 8,053 clinical notes (MIMIC-Ext) | 0.952 micro F1, a 30%+ gain over the SVM baseline across an 8-model benchmark |
| **Sepsis prediction from clinical notes** | Llama-3 8B and Meditron3-8B fine-tuned on MIMIC-IV across multiple prediction horizons, trained on a single 24GB VRAM GPU | Abstract submitted to AMIA 2026 |
| **Clinical discharge summarization** | HIPAA-compliant pipeline on AWS Bedrock benchmarking Claude 3 Haiku, Llama-3 8B, and Titan on MIMIC-IV, scored with LLM-as-judge and ANOVA/Tukey | Best F1 0.82 |
| **STEADI fall prevention** (PhD dissertation) | LLM and RAG pipeline extracting fall-prevention protocol adoption signals from physical therapy notes via QLoRA fine-tuned open models | Proposal defended |

---

## Tech stack

<p>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original-wordmark.svg" width="40" height="40" alt="Python"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/r/r-original.svg" width="40" height="40" alt="R"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original-wordmark.svg" width="40" height="40" alt="SQL"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/pytorch/pytorch-original-wordmark.svg" width="40" height="40" alt="PyTorch"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/tensorflow/tensorflow-original.svg" width="40" height="40" alt="TensorFlow"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/scikitlearn/scikitlearn-original.svg" width="40" height="40" alt="scikit-learn"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/pandas/pandas-original-wordmark.svg" width="40" height="40" alt="Pandas"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/numpy/numpy-original-wordmark.svg" width="40" height="40" alt="NumPy"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/streamlit/streamlit-original-wordmark.svg" width="40" height="40" alt="Streamlit"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" width="40" height="40" alt="AWS"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/azure/azure-original-wordmark.svg" width="40" height="40" alt="Azure"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-original-wordmark.svg" width="40" height="40" alt="Docker"/>&nbsp;
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original-wordmark.svg" width="40" height="40" alt="Git"/>
</p>

<details>
<summary><b>In detail</b></summary>

<br>

| Area | Tools |
|---|---|
| **LLM and GenAI** | RAG (hybrid lexical and semantic, RRF, ensemble retrieval, LLM reranking), QLoRA/PEFT fine-tuning, agentic systems, LLM-as-judge evaluation, ground truth design, GPT, Llama, Mistral, Meditron, vLLM |
| **Vector stores and orchestration** | ChromaDB, FAISS, Pinecone, LangChain, Transformers |
| **ML and stats** | Gradient boosting, time-series modeling, discrete-time survival analysis, regression, clinical NLP, computer vision, MLflow |
| **Cloud** | AWS (SageMaker, Bedrock, Lambda, S3, EC2, Athena, ALB, Route 53), Azure OpenAI, Databricks, Docker, HIPAA-compliant pipelines |
| **Data at scale** | PySpark on billions of line-level and millions of claim-level records |
| **Health data** | EPIC COSMOS, FHIR, MIMIC-IV, VA Corporate Data Warehouse, claims data |

</details>

---

## Publications and certifications

**19 peer-reviewed publications. 200+ citations. h-index 7.**

Published in *Addiction*, *Journal of Addictive Diseases*, and *BMC Pregnancy & Childbirth*, among others. Full list on [Google Scholar](https://scholar.google.com/citations?user=GwgCEz8AAAAJ&hl=en).

Representative work includes a regression analysis of 180,000+ patient records showing that telehealth-based opioid use disorder care is linked to fewer ER visits and increased medication receipt.

<p>
  <img src="https://img.shields.io/badge/AWS%20Certified%20Cloud%20Practitioner-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white" alt="AWS Cloud Practitioner"/>
  <img src="https://img.shields.io/badge/AWS%20Certified%20AI%20Practitioner-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white" alt="AWS AI Practitioner"/>
  <img src="https://img.shields.io/badge/EPIC%20COSMOS%20Data%20Model-B03060?style=for-the-badge" alt="EPIC COSMOS"/>
</p>

**Education**

- PhD Candidate, Biomedical Informatics, University of Arkansas for Medical Sciences (expected 2026)
- M.S. Information Science, University of Arkansas at Little Rock, with a Graduate Certificate in Data Science
- B.Sc. Electrical & Electronic Engineering, Chittagong University of Engineering & Technology

---

## Activity

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Nahiyan140212&show_icons=true&hide_border=true&hide_title=true&include_all_commits=true" height="150" alt="GitHub stats"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Nahiyan140212&layout=compact&hide_border=true&langs_count=8" height="150" alt="Most used languages"/>
</p>

---

## Outside work

New dad. Ping pong when I can find a table. Football, which means Argentina and FC Barcelona. Grew up in Bangladesh, work in English and Bangla.

I co-founded ResearchBuddy AI because I got my own start from mentors who made time for me.

---

## Contact

If you are building AI on healthcare data and need someone who can go from a SQL query to a deployed model, reach me at **nahiyan.cuet@gmail.com**.

<p>
  <a href="https://www.linkedin.com/in/nahiyan-bin-noor-0a2170158/"><img src="https://img.shields.io/badge/LinkedIn-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="mailto:nahiyan.cuet@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"/></a>
  <a href="https://nahiyan.sharedskillet.com"><img src="https://img.shields.io/badge/Portfolio-%23000000.svg?style=for-the-badge&logo=firefox&logoColor=%23FF7139" alt="Portfolio"/></a>
  <a href="https://scholar.google.com/citations?user=GwgCEz8AAAAJ&hl=en"><img src="https://img.shields.io/badge/Google%20Scholar-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white" alt="Google Scholar"/></a>
</p>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d9488,100:1e3a5f&height=100&section=footer" width="100%" alt=""/>
