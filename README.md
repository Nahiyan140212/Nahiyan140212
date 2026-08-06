<h1 align="center">Nahiyan Bin Noor</h1>

<p align="center">
  GenAI Research Scientist and Healthcare Data Scientist<br>
  Data Scientist at the U.S. Department of Veterans Affairs<br>
  PhD Candidate, Biomedical Informatics, UAMS
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/nahiyan-bin-noor-0a2170158/"><img src="https://img.shields.io/badge/LinkedIn-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="https://scholar.google.com/citations?user=GwgCEz8AAAAJ&hl=en"><img src="https://img.shields.io/badge/Google%20Scholar-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white" alt="Google Scholar"/></a>
  <a href="https://nahiyan.sharedskillet.com"><img src="https://img.shields.io/badge/Portfolio-%23000000.svg?style=for-the-badge&logo=firefox&logoColor=#FF7139" alt="Portfolio"/></a>
  <a href="mailto:nahiyan.cuet@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"/></a>
</p>

<p align="center">
  Dallas, TX &nbsp;|&nbsp; US Permanent Resident, no visa sponsorship required &nbsp;|&nbsp; Open to relocation and remote
</p>

---

## About

Most healthcare data problems are actually two problems. The numbers live in a database. The reasoning lives in a note nobody has time to read.

I work on both, and that combination is rarer than it should be.

I build production AI systems on healthcare data, from SQL feature pipelines on claims warehouses to fine-tuned clinical LLMs and retrieval systems that survive contact with real users. I also publish, which means I care about whether a number holds up under scrutiny and not just whether the demo runs.

**Currently:** Data Scientist at the U.S. Department of Veterans Affairs, Intermediate Data Analyst at the UAMS College of Pharmacy, and finishing a PhD in Biomedical Informatics.

**Looking for:** GenAI Research Scientist, AI/ML Engineer, and Data Scientist roles in DFW or remote.

---

## Table of contents

- [Selected work](#selected-work)
- [Research](#research)
- [Tech stack](#tech-stack)
- [Publications and certifications](#publications-and-certifications)
- [GitHub activity](#github-activity)
- [Outside work](#outside-work)
- [Contact](#contact)

---

## Selected work

### Production RAG for healthcare contract compliance

Built and deployed a retrieval system over two client contract corpora totaling 35,000+ documents at Cotiviti. Contract review dropped from days to minutes.

The hard part was not generation. It was ingestion and retrieval.

- **Ingestion.** Over 70% of the first corpus was scanned or photocopied PDFs with no selectable text. I benchmarked PaddleOCR and other open-source options against a GPT vision model. The vision model won and removed the need to host OCR infrastructure at all.
- **Format handling.** An adapter layer normalized scanned PDFs, native PDFs, Excel rate sheets, DOC, and DOCX into per-client ChromaDB collections, keeping each client's contracts isolated from the other's results.
- **Ground truth from nothing.** No evaluation set existed. I worked with stakeholders to define the 14 contract attributes auditors actually care about (provider name, NPI, tax ID, DRG, CPT, HCPCS, and others), sampled 720 pages from 4,236, extracted labels via probabilistic, deterministic, and LLM-assisted methods, then manually validated every page.
- **Retrieval.** Hybrid lexical and semantic search through a LangChain ensemble retriever weighted 0.7 semantic to 0.3 lexical, with E5-Mistral embeddings and `gpt-4.1-mini` handling reranking and redundancy filtering.
- **Evaluation.** 73% F1@10 on retrieval against the labeled ground truth (client 1). Generation quality on the second corpus scored 2.5 out of 3 via LLM-as-judge citation review with parallel human review (client 2). These are separate corpora and the metrics do not transfer between them.
- **Deployment.** Streamlit on AWS EC2 behind an ALB and Route 53 with feedback capture to S3, later migrated to Databricks.

Stakeholders projected roughly $8M in annual savings. That is their estimate, not a measured result.

**The finding worth repeating:** generation was never the bottleneck. Once retrieved chunks were accurate, answers were reliable. Every meaningful quality gain came from retrieval. Most people building RAG spend their effort on prompts and generation model choice.

*Code is proprietary and not published here.*

### Veteran risk stratification

Improved identification of high-risk veterans from a 50% baseline to F1 0.88 (AUC-ROC 0.76) with a Gradient Boosting model in Python on VA Corporate Data Warehouse time-series and claims data. Deployed clinical decision support dashboards in Power BI for real-time risk stratification.

### ResearchBuddy AI

Co-founder and Chief Research Officer. Most students who want to do research never get the chance, not for lack of ability but for lack of access to a supervisor. ResearchBuddy AI is an AI-powered virtual lab connecting 2,000+ researchers with 100+ supervisors worldwide. [researchbuddy.tech](https://researchbuddy.tech)

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

**Languages**

<p>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original-wordmark.svg" width="42" height="42" alt="Python"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/r/r-original.svg" width="42" height="42" alt="R"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original-wordmark.svg" width="42" height="42" alt="SQL"/>
</p>

**ML and deep learning**

<p>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/pytorch/pytorch-original-wordmark.svg" width="42" height="42" alt="PyTorch"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/tensorflow/tensorflow-original.svg" width="42" height="42" alt="TensorFlow"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/scikitlearn/scikitlearn-original.svg" width="42" height="42" alt="scikit-learn"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/pandas/pandas-original-wordmark.svg" width="42" height="42" alt="Pandas"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/numpy/numpy-original-wordmark.svg" width="42" height="42" alt="NumPy"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/streamlit/streamlit-original-wordmark.svg" width="42" height="42" alt="Streamlit"/>
</p>

**Cloud and infrastructure**

<p>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" width="42" height="42" alt="AWS"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/azure/azure-original-wordmark.svg" width="42" height="42" alt="Azure"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-original-wordmark.svg" width="42" height="42" alt="Docker"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original-wordmark.svg" width="42" height="42" alt="Git"/>
</p>

**In detail**

| Area | Tools |
|---|---|
| **LLM and GenAI** | RAG (hybrid lexical and semantic, RRF, ensemble retrieval, LLM reranking), QLoRA/PEFT fine-tuning, agentic systems, LLM-as-judge evaluation, ground truth design, GPT, Llama, Mistral, Meditron, vLLM |
| **Vector stores and orchestration** | ChromaDB, FAISS, Pinecone, LangChain, Transformers |
| **ML and stats** | Gradient boosting, time-series modeling, discrete-time survival analysis, regression, clinical NLP, computer vision, MLflow |
| **Cloud** | AWS (SageMaker, Bedrock, Lambda, S3, EC2, Athena, ALB, Route 53), Azure OpenAI, Databricks, Docker, HIPAA-compliant pipelines |
| **Data at scale** | PySpark on billions of line-level and millions of claim-level records |
| **Health data** | EPIC COSMOS, FHIR, MIMIC-IV, VA Corporate Data Warehouse, claims data |

---

## Publications and certifications

**19 peer-reviewed publications. 200+ citations. h-index 7.**

Published in *Addiction*, *Journal of Addictive Diseases*, and *BMC Pregnancy & Childbirth*, among others. Full list on [Google Scholar](https://scholar.google.com/citations?user=GwgCEz8AAAAJ&hl=en).

Representative work includes a regression analysis of 180,000+ patient records showing that telehealth-based opioid use disorder care is linked to fewer ER visits and increased medication receipt.

**Certifications**

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

## GitHub activity

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Nahiyan140212&show_icons=true&hide_border=true" alt="GitHub stats"/>
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Nahiyan140212&layout=compact&hide_border=true" alt="Most used languages"/>
</p>

---

## Outside work

New dad. Ping pong when I can find a table. Football, which means Argentina and FC Barcelona. Grew up in Bangladesh, work in English and Bangla.

I co-founded ResearchBuddy AI because I got my own start from mentors who made time for me.

---

## Contact

If you are building AI on healthcare data and need someone who can go from a SQL query to a deployed model, reach me at **nahiyan.cuet@gmail.com**.

<p align="left">
  <a href="https://www.linkedin.com/in/nahiyan-bin-noor-0a2170158/"><img src="https://img.shields.io/badge/LinkedIn-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="mailto:nahiyan.cuet@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"/></a>
  <a href="https://nahiyan.sharedskillet.com"><img src="https://img.shields.io/badge/Portfolio-%23000000.svg?style=for-the-badge&logo=firefox&logoColor=#FF7139" alt="Portfolio"/></a>
  <a href="https://scholar.google.com/citations?user=GwgCEz8AAAAJ&hl=en"><img src="https://img.shields.io/badge/Google%20Scholar-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white" alt="Google Scholar"/></a>
</p>
