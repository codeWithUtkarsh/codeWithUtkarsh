[![Header](https://github.com/codeWithUtkarsh/codeWithUtkarsh/blob/main/header-banner.png "Header")](https://dev.to/codewithutkarsh)

# Hi, I'm Utkarsh <img src="https://github.com/codeWithUtkarsh/codeWithUtkarsh/blob/main/wave.gif" width="30px">

**AI/ML Engineer** in London, currently at **Acutro**. I have 6+ years shipping production systems and now work end-to-end on **GenAI** — agentic architectures, RAG at scale, and LLM-powered products — with the MLOps to keep them alive after the demo.

- 🔭 Building agentic systems with **LangGraph**, **Claude**, and **MCP** — most recently [**ortelius/pdvd-aiops**](https://github.com/ortelius/pdvd-aiops); plus time-series and predictive-maintenance ML on high-dimensional IoT sensor data.
- 🎓 **MSc Big Data Science, Queen Mary University of London** — Distinction.
- 🏆 **Top CDF Contributor 2024** (The Linux Foundation), Ortelius **Governing Board** member, and the first-ever **Gold Legend** — see [Open Source](#-open-source--the-linux-foundation).
- ✍️ I write about the things I build — see [Writing](#-writing) below.
- 📄 **[Résumé (PDF)](https://drive.google.com/file/d/1BiaZ8UL96MT4ytYCg2Mjtqo-Rq_32TB6/view?usp=share_link)** — the full detail behind everything below.
- 📫 Reach me on [![LinkedIn][3.2]][3] [LinkedIn][3] · [![Twitter][1.2]][1] [Twitter][1] · <utkarshkviim@gmail.com>

## ⭐ Featured Work — [`ortelius/pdvd-aiops`](https://github.com/ortelius/pdvd-aiops)

[![LangGraph](https://img.shields.io/badge/LangGraph-informational?style=flat&logo=langgraph&logoColor=white&color=2bbc8a)](https://github.com/ortelius/pdvd-aiops)
[![MCP](https://img.shields.io/badge/GitHub_MCP-informational?style=flat&logo=anthropic&logoColor=white&color=2bbc8a)](https://github.com/ortelius/pdvd-aiops)
[![Python](https://img.shields.io/badge/Python-informational?style=flat&logo=python&logoColor=white&color=2bbc8a)](https://github.com/ortelius/pdvd-aiops)
[![FastAPI](https://img.shields.io/badge/FastAPI-informational?style=flat&logo=fastapi&logoColor=white&color=2bbc8a)](https://github.com/ortelius/pdvd-aiops)
[![Trivy](https://img.shields.io/badge/Trivy-informational?style=flat&logo=trivy&logoColor=white&color=2bbc8a)](https://github.com/ortelius/pdvd-aiops)
[![Apache 2.0](https://img.shields.io/badge/Apache_2.0-informational?style=flat&logo=apache&logoColor=white&color=2bbc8a)](https://github.com/ortelius/pdvd-aiops/blob/main/LICENSE)

**Ortelius AIOps** — an autonomous, agentic pipeline for dependency health and supply-chain security, built for the CDF's [Ortelius](https://ortelius.io) project. Point it at a GitHub repo and it updates every outdated dependency, builds and tests the result, bisects and rolls back whatever breaks, patches CVEs, and opens a PR with an LLM-written risk assessment. **Sole author — all 45 commits.**

The design principle is that **most of a pipeline shouldn't need an LLM**. Ecosystem detection, update application, build/test, scanning, and PR creation are all deterministic; the model is invoked only for the nine judgement calls that genuinely require it. Total cost lands at **$0.001–$0.01 per run**.

| | |
|---|---|
| **Orchestration** | **LangGraph** state machine with conditional routing — analyse → detect commands → prepare → build → test → rollback ⟲ → integrations → security audit → patch → PR/Issue, with an orchestrator agent routing tasks and a typed state object threaded throughout. |
| **Binary-search rollback** | When tests fail, packages are ranked by suspicion (error mentions + major-bump risk). Low confidence bisects the suspicious *half*, isolating the culprit in **log₂(n)** retries instead of n. |
| **Nine LLM analysers** | Changelog risk · source-code impact · config drift · security triage · **reachability** · failure root-cause · maintainer PR summary · update grouping · multi-repo synthesis. |
| **Reachability analysis** | Rather than reporting every advisory, it greps for imports of the vulnerable package and asks whether the vulnerable path is actually reachable from your application — turning CVE noise into a ranked action list. |
| **Supply-chain scanning** | Seven tools in concert — pip-audit, npm audit, govulncheck, cargo audit, **Trivy**, **OSV-Scanner**, Semgrep, Bandit — with fixable CVEs auto-patched and unfixable ones tracked in a persistent GitHub Issue. |
| **Breadth** | Eight package ecosystems (pip, poetry, npm, pnpm, yarn, cargo, go, plus extras); six interchangeable LLM providers (Anthropic, Gemini, OpenAI, Groq, HuggingFace, Ollama); GitHub access via the **GitHub MCP server**. |
| **Surfaces** | CLI, a **FastAPI** async job API with OpenAPI docs, Docker Compose, and org-wide batch mode that synthesises shared CVEs across repos and ranks which to fix first for maximum blast-radius reduction. |

## 🧠 What I've Shipped

- **Predictive maintenance at scale** — 200+ regression and tree-based models over **3,000+ IoT sensors** across 50 sites, plus an N-BEATS network for HVAC fault detection. *70% faster training, 60% less unplanned downtime.*
- **Production GenAI assistant** — agentic orchestration on Claude with LangChain tool calling and RAG at scale, served via FastAPI streaming + Next.js. *Search time 10 min → 10s.*
- **Agentic IaC provisioning** — a repo-aware agent that proposes an architecture, renders it for review, then auto-provisions post-RBAC. *Turnaround 5 days → 1 day.*
- **GenAI NER on Vertex AI** — Gemini 1.5 Flash + RAG with domain-adaptation fine-tuning and RLHF alignment. *~95% extraction accuracy.*

> 📄 **These are summaries.** The stack, scale, and full context behind each one — plus six years of prior work — are in my **[résumé](https://drive.google.com/file/d/1BiaZ8UL96MT4ytYCg2Mjtqo-Rq_32TB6/view?usp=share_link)**.

## 🔬 Featured Projects

**Multimodal retrieval & recommender systems**

| Repo | What it is |
|---|---|
| [**GenAIFashionStore**](https://github.com/codeWithUtkarsh/GenAIFashionStore) | **CLIP** embeddings in a **ChromaDB** vector store for visual, text, and hybrid search; GPT-driven styling chat; recommendations blending visual similarity, category, and collaborative filtering. |
| [**fashion-visual-search**](https://github.com/codeWithUtkarsh/fashion-visual-search) | The retrieval engine done properly: **ResNet50** features, **FAISS** similarity index, and **MMR**-based diversification for complementary and complete-the-outfit suggestions. Methodology documented in `METHODOLOGY.md`. |
| [**deep-learning-fashion-search**](https://github.com/codeWithUtkarsh/deep-learning-fashion-search) | Neural Networks & Deep Learning coursework — an image-based fashion search system, with the written report alongside the notebook. |

**Quantum & classical optimisation**

| Repo | What it is |
|---|---|
| [**tsp-quantum-algorithm**](https://github.com/codeWithUtkarsh/tsp-quantum-algorithm) | MSc research: a **QAOA** solver for the Travelling Salesman Problem in **Qiskit**, configurable across problem sizes, optimisers, and penalty weights, running on simulator or real quantum hardware. |
| [**tsp-playground**](https://github.com/codeWithUtkarsh/tsp-playground) | The classical control group in C++ — Branch and Bound, Held-Karp, Genetic Algorithm, and Simulated Annealing, benchmarked head to head. |
| [**quantum-research**](https://github.com/codeWithUtkarsh/quantum-research) | Held-Karp baselines and the benchmarking harness that makes the quantum-vs-classical comparison measurable. |

**ML & data foundations**

| Repo | What it is |
|---|---|
| [**neural-networks**](https://github.com/codeWithUtkarsh/neural-networks) | Twelve weeks of network architectures built up from scratch. |
| [**NLP**](https://github.com/codeWithUtkarsh/NLP) | Tweet sentiment analysis and vector-space semantics for character similarity. |
| [**ClassifierML**](https://github.com/codeWithUtkarsh/ClassifierML) · [**Gaussians_Mixture_model**](https://github.com/codeWithUtkarsh/Gaussians_Mixture_model) | Text + image feature fusion for cuisine classification; GMMs over the Peterson & Barney vowel formant dataset. |
| [**predictive-analysis**](https://github.com/codeWithUtkarsh/predictive-analysis) · [**spark-taxi-analytics**](https://github.com/codeWithUtkarsh/spark-taxi-analytics) | Insurance-cost regression; distributed **Spark** analytics on a JupyterHub/Kubernetes cluster. |

**Applied GenAI & open source**

| Repo | What it is |
|---|---|
| [**llm-product-attribute-extraction**](https://github.com/codeWithUtkarsh/llm-product-attribute-extraction) | LLM-driven product attribute extraction over scraped retail catalogues, running **Ollama** locally against a category/attribute taxonomy — the working notebooks behind the NER pipeline. |
| [**GPT5VideoSubtitleGeneration**](https://github.com/codeWithUtkarsh/GPT5VideoSubtitleGeneration) | Video → transcript → translated subtitles, wrapped in a small web service around the processing and translation stages. |
| [**Ortelius** microservices](https://github.com/codeWithUtkarsh?tab=repositories&q=ortelius) | CNCF/CDF software supply-chain evidence store — the contributions behind the two Linux Foundation awards. |

## 🔧 Technologies & Tools

**GenAI & LLMs**

![](https://img.shields.io/badge/Claude-informational?style=flat&logo=anthropic&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/OpenAI-informational?style=flat&color=2bbc8a)
![](https://img.shields.io/badge/LangChain-informational?style=flat&logo=langchain&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/LangGraph-informational?style=flat&logo=langgraph&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/RAG-informational?style=flat&logo=databricks&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/MCP-informational?style=flat&logo=anthropic&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Ollama-informational?style=flat&logo=ollama&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Fine_tuning_&_RLHF-informational?style=flat&logo=huggingface&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/ChromaDB-informational?style=flat&logo=chromatic&logoColor=white&color=2bbc8a)

**ML & Deep Learning**

![](https://img.shields.io/badge/PyTorch-informational?style=flat&logo=pytorch&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/scikit_learn-informational?style=flat&logo=scikitlearn&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/XGBoost-informational?style=flat&color=2bbc8a)
![](https://img.shields.io/badge/pandas-informational?style=flat&logo=pandas&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/NumPy-informational?style=flat&logo=numpy&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Time_Series_&_Anomaly_Detection-informational?style=flat&logo=plotly&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/FAISS-informational?style=flat&logo=meta&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/CLIP_&_ResNet-informational?style=flat&logo=pytorch&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Streamlit-informational?style=flat&logo=streamlit&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Qiskit-informational?style=flat&logo=qiskit&logoColor=white&color=2bbc8a)

**MLOps & Platform**

![](https://img.shields.io/badge/AWS_SageMaker-informational?style=flat&color=2bbc8a)
![](https://img.shields.io/badge/Amazon_Bedrock-informational?style=flat&color=2bbc8a)
![](https://img.shields.io/badge/Vertex_AI-informational?style=flat&logo=googlecloud&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Docker-informational?style=flat&logo=docker&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Kubernetes-informational?style=flat&logo=kubernetes&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Terraform-informational?style=flat&logo=terraform&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/GitHub_Actions-informational?style=flat&logo=githubactions&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Prometheus-informational?style=flat&logo=prometheus&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Grafana-informational?style=flat&logo=grafana&logoColor=white&color=2bbc8a)

**Data, Backend & Cloud**

![](https://img.shields.io/badge/Python-informational?style=flat&logo=python&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/FastAPI-informational?style=flat&logo=fastapi&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Next.js-informational?style=flat&logo=nextdotjs&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Java-informational?style=flat&logo=openjdk&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Go-informational?style=flat&logo=go&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Apache_Kafka-informational?style=flat&logo=apachekafka&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Apache_Flink-informational?style=flat&logo=apacheflink&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Apache_Spark-informational?style=flat&logo=apachespark&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/PostgreSQL-informational?style=flat&logo=postgresql&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/AWS-informational?style=flat&color=2bbc8a)
![](https://img.shields.io/badge/GCP-informational?style=flat&logo=googlecloud&logoColor=white&color=2bbc8a)
![](https://img.shields.io/badge/Azure-informational?style=flat&color=2bbc8a)

## &#x1f4c8; GitHub Stats

<a href="https://github.com/codeWithUtkarsh/codeWithUtkarsh">
  <img align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=codeWithUtkarsh&layout=compact&langs_count=8&hide=html,css,tex,mustache,scss,shell&title_color=ffffff&text_color=c9cacc&icon_color=2bbc8a&bg_color=1d1f21" />
</a>
<a href="https://github.com/codeWithUtkarsh/codeWithUtkarsh">
  <img align="center" src="https://github-readme-stats.vercel.app/api?username=codeWithUtkarsh&show_icons=true&line_height=27&count_private=true&title_color=ffffff&text_color=c9cacc&icon_color=2bbc8a&bg_color=1d1f21" alt="Utkarsh's GitHub Stats" />
</a>

## 🏅 Open Source — The Linux Foundation

<table>
  <tr>
    <td align="center" width="150">
      <a href="https://www.credly.com/badges/346094d9-beb9-423c-9399-d4c41e8345eb/public_url"><img src="https://images.credly.com/images/598deb01-729d-430b-a79d-5b12e9687a04/image.png" width="110" alt="Top CDF Contributor Award 2024" title="Top CDF Contributor Award 2024" /></a>
    </td>
    <td align="center" width="150">
      <a href="https://www.credly.com/badges/461fa368-ba7e-4112-abb2-61de63e060d7/public_url"><img src="https://images.credly.com/images/1f8c6683-e5f4-4123-b5a6-d6a7e26c8c9e/image.png" width="110" alt="Ortelius Most Valuable Contributor 2024" title="Ortelius Most Valuable Contributor 2024" /></a>
    </td>
    <td align="center" width="150">
      <a href="https://www.credly.com/badges/81a82816-958c-43f2-a68f-0af627ef4589/public_url"><img src="https://images.credly.com/images/2550bcb9-f3b6-415d-a8b1-2fc6d737d746/blob" width="110" alt="Program Committee — cdCon 2026" title="Program Committee — cdCon 2026" /></a>
    </td>
    <td align="center" width="150">
      <a href="https://www.credly.com/badges/166327e4-71d7-4319-9b5f-24b218e70f00/public_url"><img src="https://images.credly.com/images/8dd85c4a-a98d-4e07-9809-3f77d9ddfcb8/blob" width="110" alt="Program Committee — OSS + ELC North America 2026" title="Program Committee — OSS + ELC North America 2026" /></a>
    </td>
  </tr>
  <tr>
    <td align="center" width="150"><b>Top CDF Contributor Award 2024</b><br /><sub>The Linux Foundation · 2024</sub></td>
    <td align="center" width="150"><b>Ortelius Most Valuable Contributor 2024</b><br /><sub>The Linux Foundation · 2024</sub></td>
    <td align="center" width="150"><b>Program Committee — cdCon 2026</b><br /><sub>The Linux Foundation · 2026</sub></td>
    <td align="center" width="150"><b>Program Committee — OSS + ELC North America 2026</b><br /><sub>The Linux Foundation · 2026</sub></td>
  </tr>
</table>

- 🥇 **Gold Legend** — the **first-ever recipient** of Ortelius' highest recognition, which requires reaching Gold in *both* the Champion (technical contribution) and Ambassador (community outreach) tracks. [Announcement](https://cd.foundation/blog/2023/12/13/utkarsh-sharma-achieves-gold-legend-status/)
- 🏛️ **Governing Board member, Ortelius** — leading the project's machine-learning direction, after starting out by volunteering at an architecture meeting and shipping the Flask backend for the frontend service.
- 🎤 **Program Committee** for **cdCon 2026** and **Open Source Summit + Embedded Linux Conference North America 2026** — reviewing and rating submitted speaking proposals.
- 📰 Featured in the CDF [**Continuous Spotlight**](https://cd.foundation/blog/2024/08/27/continuous-spotlight-meet-utkarsh-kumar-sharma/) interview series, and named [**Top CDF Contributor 2024**](https://cd.foundation/cdf-community-awards-2024/).
- 🛠️ Contributor to **Ortelius**, **Jenkins X**, and **Keptn**.

> *"Don't think too much and don't be afraid to reach out to people."*

## 📜 Certifications

Microsoft Azure — **AI-900** (AI Fundamentals) · **DP-900** (Data Fundamentals) · **AZ-900** (Fundamentals) · **AZ-204** (Developer Associate) · **AZ-303** (Solutions Architect)

## &#x270d; Writing

  <!-- BLOG-POST-LIST:START -->
- [Get started with Keptn — Multi-stage delivery with Quality Gates (Demo)](https://codewithutkarsh.medium.com/get-started-with-keptn-multi-stage-delivery-with-quality-gates-demo-part-1-e13438d6374)
- [Kafka 2.7 in Docker and Spring Boot | Let's develop a pub-sub application](https://codewithutkarsh.medium.com/kafka-2-7-in-docker-and-spring-boot-lets-develop-a-pub-sub-application-a0fafd3ea3d5)
<!-- BLOG-POST-LIST:END -->

More on [Medium](https://codewithutkarsh.medium.com/) and [dev.to](https://dev.to/codewithutkarsh).

<!-- links to social media icons -->

<!-- icons with padding -->

[1.1]: http://i.imgur.com/tXSoThF.png (twitter icon with padding)
[2.1]: http://i.imgur.com/0o48UoR.png (github icon with padding)

<!-- icons without padding -->

[1.2]: http://i.imgur.com/wWzX9uB.png (twitter icon without padding)
[2.2]: http://i.imgur.com/9I6NRUm.png (github icon without padding)
[3.2]: https://raw.githubusercontent.com/MartinHeinz/MartinHeinz/master/linkedin-3-16.png (LinkedIn icon without padding)

<!-- links to your social media accounts -->

[1]: https://twitter.com/codeWithUtkarsh
[2]: https://github.com/codeWithUtkarsh
[3]: https://www.linkedin.com/in/codewithutkarsh/

<!---
codeWithUtkarsh/codeWithUtkarsh is a special repository because its `README.md` (this file) appears on your GitHub profile.
--->
