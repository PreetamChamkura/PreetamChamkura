# Hi there, I'm Preetam Chamkura! 👋

## 🎓 About Me

I'm a Computer Science student at UC Irvine (Specialization in Intelligent Systems, graduating June 2027), who transferred from Florida State University. I'm passionate about **security**, **agentic AI systems**, and building things end to end — from low-level systems work to production tools people actually use.

I like using AI to move faster, and I like verifying its output even more: most of my projects pair an AI-driven system with a measured evaluation of whether it actually works.

## 💼 Experience Highlights

- **Software Engineer Intern @ Comcast — Billing Architecture Team (2026):**
  - Raised test coverage on a production Java/Spring Boot billing service from ~2% to 50% using AI-generated tests with manual review, then added a test stage to the team's Azure DevOps CI/CD pipeline so the suite runs on every pull request.
  - Drove a multi-agent AI-orchestrated security audit across 4 production microservices, surfacing 51 validated vulnerabilities; human-in-the-loop triage ruled out 30–50% of ~190 AI-generated findings as false positives.
  - Built a billing PDF extraction tool from an unassigned idea to a demo for directors and VPs (Python, legacy Oracle 10g over JDBC, React/TypeScript), plus a retrieval-augmented onboarding agent (LangGraph, BM25) and a self-directed GPU tensor compiler (TensorForge).
- **Software Engineer Intern @ Comcast — IoT and Embedded Security Team (2025):** Reduced certificate validation latency 40% across distributed infrastructure serving millions of devices; contributed to [libCertifier](https://github.com/PreetamChamkura/libcertifier), Comcast's open-source C library for x509 provisioning on constrained devices, adding custom provisioning parameters and Sectigo as a second supported certificate authority.
- **Undergraduate Researcher @ FSU eHealth Lab (AHRQ-funded):** Built LabGenie, an LLM tool that generates patient follow-up questions, and ran a physician-evaluation loop with 3 board-certified physicians across multiple LLMs. Separating hallucination from ambiguity as distinct failure modes raised clinical-sense and clarity scores from 89.6%/96.7% to 100%/100%.

## 🔧 Technical Stack

**Languages:** Python • C++ • Java • JavaScript/TypeScript • C • SQL
**AI & Agents:** Claude API, agentic orchestration, RAG, hybrid retrieval (FAISS + TF-IDF), LangGraph, prompt engineering
**ML:** PyTorch, scikit-learn, OpenCV
**Security:** Applied cryptography (x509/PKI), vulnerability assessment, guardrails, container hardening
**Systems & Infra:** AWS (Fargate, SQS, DynamoDB), Docker, Kubernetes, Azure DevOps (CI/CD), Grafana, Kibana, Unix/Linux, Git
**Web:** React, Node.js, Spring Boot

## 🚀 Featured Projects

### 🛰️ [Mission Agent Platform](https://github.com/PreetamChamkura/mission-agent-platform) — Air-Gap-Deployable AI Agent Platform
*Python, asyncio, FAISS, ONNX Runtime, Docker, Kubernetes*
Full-stack AI agent platform designed for high-stakes, disconnected environments, with zero external API or network dependency.
- **Guardrails:** 5-layer engine covering prompt-injection detection, PII redaction, classification-based access control (simulated PUBLIC → TOP SECRET labels), rate limiting, and output schema validation.
- **Retrieval:** hybrid dense + sparse search unifying 4 siloed sources (CSV, JSON, unstructured text). A local embedding model (bge-small via ONNX) in a FAISS index is fused with a self-implemented TF-IDF; a test confirms paraphrased queries with zero keyword overlap still retrieve correctly.
- **Orchestration:** custom `asyncio` worker pool with a 6-state task lifecycle and human-approval checkpoints across 3 agent roles with different data clearances. No workflow framework.
- **Anomaly detection:** rolling z-score plus IQR/Tukey's fences, with a test showing IQR catches an outlier that skews its own z-score baseline.
- **Deployment & evaluation:** hardened multi-stage Docker (non-root, read-only rootfs, dropped capabilities), Kubernetes with default-deny egress, and an evaluation harness that gates every policy or model change (4/4 reliability cases passing; 13/13 tests).
- **Bug I caught:** approval-required verdicts were originally passing through silently instead of halting the agent. Fixed and now covered by a regression test.

### 🛡️ [Sentinel](https://github.com/PreetamChamkura/sentinel) — Multi-Agent Vulnerability Auditor
*Python, Claude API, Docker, AWS (Fargate, SQS, DynamoDB)*
Security auditor that orchestrates specialized Claude sub-agents to detect web application vulnerabilities across a codebase. Modular pipeline: line-based code chunking with configurable overlap, a fan-out layer dispatching chunks to vulnerability-class-specific sub-agents, dedup logic for overlap-induced duplicates, and a strict JSON-schema contract with retry-and-fail-loud error handling so no finding is silently dropped. New detectors (IDOR shipped; SQLi/XSS/SSRF scaffolded) need only a new system prompt.

**Results:** on a hand-labeled, cross-framework benchmark (Flask, Express/Node.js, Django, Spring, Rails; 7 files, 21 endpoints): **12/12 true-positive IDOR detections, 0 false positives**, including correctly withholding findings on 8 endpoints designed to bait an indiscriminate detector. A full scan completes in ~36s. Backed by a 7-test suite and an architecture-decisions log.

*(The benchmark is intentionally small and hand-labeled for precise ground truth: a strong initial signal, not a claim of production-scale coverage.)*

### 🎬 [Clipper](https://github.com/PreetamChamkura/agent-shorts) — Automated Video Production Pipeline
*Python, Claude API, faster-whisper, OpenCV, ffmpeg, OpenAI TTS*
End-to-end pipeline that turns long-form VODs and clips into short-form video: ingestion, transcription, LLM-based moment selection, TTS narration, and ffmpeg rendering as independently cacheable stages.
- **3-layer visual quality gate** (pixel stats, OpenCV face detection, vision-model judgment) rejects dead footage before it reaches paid LLM calls.
- **Cost engineering:** per-request token/cache accounting, batching, and a model sweep graded against known-correct outcomes cut cost per published clip **~90% ($0.30–0.40 → under $0.02)**.
- **Determinism where it matters:** LLM-guessed timestamps drifted 10+ seconds run to run, so I replaced them with transcript phrase-matching.
- Published output has reached **4,000+ views**.

### ⚙️ TensorForge — GPU Tensor Compiler
*C++, Python, MLX, Metal*
Self-directed GPU tensor compiler and runtime, built independently at Comcast. Lowers tensor expressions into a computation graph and custom IR, with shape inference, dependency tracking, and DFS-based cycle detection to reject invalid structures before compilation.

### 🖼️ [CIFAR-10 Image Classifier](https://github.com/PreetamChamkura/cifar10-cnn-classifier)
*Python, PyTorch, scikit-learn*
ResNet9 CNN (6.6M params) trained from scratch to **93.46% test accuracy** in ~29 minutes on an M3 Pro. The first attempt (Adam + OneCycleLR) plateaued at 85% while still climbing; I diagnosed it as an optimizer/schedule mismatch rather than "needs more epochs," and switched to SGD with Nesterov momentum. Leak-free evaluation (test set touched once) with precision/recall/F1 and a confusion matrix.

### 🔍 Full-Text Search Engine
*Python*
Inverted index built from scratch over 53,297 documents and 1,066,353 tokens: disk-flushed partial indexes, external k-way merge, and a byte-offset seek table for constant-time disk lookups, with tf-idf scoring and cosine-similarity ranking.

### ♿ [Mapping Access](https://github.com/PreetamChamkura/mapping-access) — Accessibility Planner
*JavaScript, Node.js, Full-Stack*
Full-stack prototype built with a 5-person team that scores theme park rides against a guest's mobility and sensory needs and generates a routed itinerary. Presented to directors and VPs.

### 💣 [Minesweeper Solver](https://github.com/PreetamChamkura/MineSweeperAI)
*Python*
Solver combining constraint propagation with probabilistic reasoning to choose safe moves when the board is ambiguous.

## 📫 Let's Connect!

- 💼 [LinkedIn](https://linkedin.com/in/preetam-chamkura)
- 📧 chamkurapreetam@gmail.com
- 🌐 Location: Irvine, CA

💡 *Always learning, always building. Open to collaborations on security and AI-agent projects!*
