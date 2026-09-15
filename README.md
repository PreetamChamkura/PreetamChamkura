# Hi there, I'm Preetam Chamkura! 👋

## 🎓 About Me

I'm a Computer Science student at UC Irvine (Specialization in Intelligent Systems, graduating June 2027), who transferred from Florida State University. I'm passionate about **security**, **agentic AI systems**, and building things end to end — from low-level systems work to production tools people actually use.

Currently exploring the intersection of **AI agent orchestration**, **applied security**, and **systems programming**.

## 💼 Experience Highlights

- **Software Engineer Intern @ Comcast — Billing Architecture Team (2026):** Independently drove a multi-agent AI-orchestrated security audit across 4 production microservices, surfacing 51 validated vulnerabilities including a critical IDOR (CVSS 9.4) that commercial scanners missed; built a retrieval-augmented internal agent (LangGraph, BM25) and a self-directed GPU tensor compiler (TensorForge) in C++.
- **Software Engineer Intern @ Comcast — IoT and Embedded Security Team (2025):** Reduced certificate validation latency 40% across distributed infrastructure serving millions of devices; contributed to libCertifier, Comcast's open-source C library for x509 provisioning, adding Sectigo as a second supported certificate authority.
- **Undergraduate Researcher @ FSU eHealth Lab:** Built LabGenie, an AHRQ-funded LLM tool generating patient follow-up questions from lab results; ran a physician-evaluation loop that raised clinical-sense and clarity scores from 89.6%/96.7% to 100%/100%.

## 🔧 Technical Stack

**Languages:** Python • C++ • Java • JavaScript/TypeScript • C • SQL
**AI & Agents:** LLM APIs (Claude), agentic orchestration, RAG, prompt engineering, LangGraph
**Security:** Applied cryptography (x509/PKI), vulnerability assessment, multi-agent detection pipelines
**Systems & Infra:** AWS (Fargate, SQS, DynamoDB), Docker, Unix/Linux, distributed systems, Git

## 🚀 Featured Projects

### 🛡️ [Sentinel](https://github.com/PreetamChamkura/sentinel) — Multi-Agent Vulnerability Auditor
*Python, Anthropic Claude API*
Security vulnerability auditor that orchestrates specialized Claude sub-agents to detect web application vulnerabilities across a codebase. Designed a modular pipeline: line-based code chunking with configurable overlap, a fan-out orchestration layer dispatching chunks to vulnerability-class-specific sub-agents, dedup logic collapsing overlap-induced duplicate findings, and a strict JSON-schema contract with retry-and-fail-loud error handling so no finding is silently dropped. New vulnerability-class detectors (IDOR shipped; SQLi/XSS/SSRF scaffolded) require only a new system prompt, fully decoupled from chunking and orchestration logic.

**Results:** validated on a hand-labeled, cross-framework benchmark (Flask, Express/Node.js, Django, Spring, Rails — 7 files, 21 endpoints): **12/12 true-positive IDOR detections, 0 false positives**, including correctly withholding findings on 8 endpoints specifically designed to bait an indiscriminate detector (ownership-scoped queries, role-gated routes, session-derived identity). Full 7-file cross-framework scan completes in ~36s (~5s/API call). Backed by a 7-test suite (deterministic chunking unit tests + live API smoke tests) and a running architecture-decisions log documenting every tradeoff.

*(Benchmark is intentionally small and hand-labeled for precise ground truth — strong initial signal, not a claim of production-scale coverage.)*

### 🎬 [Clipper](https://github.com/PreetamChamkura/agent-shorts) — Automated Video Production Pipeline
*Python, Claude API, OpenCV, ffmpeg*
End-to-end pipeline that turns long-form VODs and clips into short-form video: ingestion, transcription, LLM-based moment selection, TTS narration, and ffmpeg rendering as independently-cacheable stages. Includes a 3-layer visual quality gate (pixel-stats pre-filter, OpenCV face detection, vision-model judgment) to reject dead footage before it reaches paid LLM calls, schema-validated structured outputs with a warn-and-keep posture, and a measured effort/model cost-quality sweep rather than blind tuning. Published output has reached thousands of views within hours.

### ⚙️ TensorForge — GPU Tensor Compiler
*C++, Python, MLX, Metal*
Self-directed GPU tensor compiler and runtime, built independently at Comcast. Lowers tensor expressions into a computation graph and custom IR, with shape inference, dependency tracking, and DFS-based cycle detection to reject invalid structures before compilation.

### 🔍 Full-Text Search Engine
*Python*
Inverted index built from scratch over 53,297 documents and 1,066,353 unique tokens — disk-flushed partial indexes, external k-way merge, and a byte-offset seek table for O(1) lookups — achieving sub-second ranked retrieval via tf-idf scoring with cosine normalization.

### ♿ [Mapping Access](https://github.com/PreetamChamkura/mapping-access) — Accessibility Planner
*JavaScript, Node.js, Full-Stack*
Full-stack prototype built with a 5-person team that scores theme park rides against a guest's mobility and sensory needs and generates a routed itinerary. Presented to directors and VPs.

## 📫 Let's Connect!

- 💼 [LinkedIn](https://linkedin.com/in/preetam-chamkura)
- 📧 chamkurapreetam@gmail.com
- 🌐 Location: Irvine, CA

💡 *Always learning, always building. Open to collaborations on security and AI-agent projects!*
