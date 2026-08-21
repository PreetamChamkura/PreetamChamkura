# Preetam Chamkura

CS student at UC Irvine (BS, Specialization in Intelligent Systems, June 2027), previously two years at Florida State. Currently interning at Comcast on the Billing Architecture team; last summer I was on their IoT and Embedded Security team.

Most of my work sits at the intersection of **security and systems** — certificate infrastructure, vulnerability auditing, and lately using agent orchestration to find things static scanners miss.

---

## Experience

**Comcast — Billing Architecture** · Summer 2026
- Drove an AI-orchestrated security audit across 4 production microservices, surfacing **51 validated vulnerabilities** including a critical IDOR (CVSS 9.4) that commercial scanners missed
- Built a human-in-the-loop exploitability triage process that ruled out 30–50% of ~190 automated findings as false positives
- Raised line coverage on a core Java/Spring Boot billing microservice from ~2% to ~50% across payment-flow and exception-handling paths
- **TensorForge** — GPU tensor compiler and runtime (C++/Python, MLX/Metal)
- Retrieval-augmented onboarding agent (Python, LangGraph) over internal docs and repos, using chunking + BM25 ranked retrieval behind a tool-calling workflow

**Comcast — IoT and Embedded Security** · Summer 2025
- Cut certificate validation latency **40%** across infrastructure serving millions of IoT devices with a production Python client for real-time OCSP/CRL revocation checks
- Extended **libCertifier** (Comcast's open-source C library for x509 provisioning on constrained devices) with custom provisioning parameters and Sectigo CA support — ~100+ engineering hours saved annually
- Authored technical documentation that cut implementation time **60%** across 5+ engineering teams

---

## Projects

### 🔒 Sentinel — Agentic Vulnerability Auditor *(in progress)*
`Python` `Claude API` `AWS Fargate / SQS / DynamoDB` `Docker`

Open-source security auditor that orchestrates AI sub-agents to detect web vulnerabilities and triage false positives, measured against the labeled OWASP Benchmark dataset. Built on an async, horizontally scalable pipeline — stateless API, SQS job queue, containerized Fargate workers, DynamoDB state — so request handling and long-running agent orchestration scale independently.

### 🔍 Full-Text Search Engine
`Python` `Information Retrieval`

Inverted index built from scratch over **53,297 crawled documents / 1,066,353 unique tokens**, with sub-second ranked retrieval. SPIMI-style disk-flushed partial indexes, k-way merge, byte-offset seek table for O(1) lookups, tf-idf scoring with cosine normalization.

### ♿ Mapping Access — Theme Park Accessibility Planner
`JavaScript` `Node.js`

Deployed accessibility prototype built with a 5-person intern team: scores rides against a guest's mobility, sensory, and medical needs and generates a routed itinerary. Presented to directors and VPs as our internship capstone.
[Demo](https://preetamchamkura.github.io/capstone_new/) · [Repo](https://github.com/PreetamChamkura/capstone_new)

---

## Research

### 🧪 LabGenie — AHRQ-Funded LLM Research, FSU eHealth Lab
`Python` `LLM Prompt Engineering`

An LLM system generating tailored patient follow-up questions from lab results. Ran an evaluation loop with 3 board-certified physicians over de-identified EHR cases, coded their feedback in NVivo to isolate hallucination and ambiguity failure modes, and iterated prompts against them — raising clarity from 96.7% → 100% and clinical sense from 89.6% → 100%. Presented at FSU's UROP poster symposium.

---

## Stack

**Languages:** Python · C++ · C · Java · JavaScript/TypeScript · SQL
**Systems:** AWS (Fargate, SQS, DynamoDB) · Docker · Unix/Linux · REST APIs · async & distributed architectures
**Security:** OpenSSL · PKI · x509 · OCSP/CRL · threat modeling
**AI:** agentic workflows · LLM orchestration & evaluation · RAG · PyTorch

---

## Contact

[LinkedIn](https://linkedin.com/in/preetam-chamkura) · <chamkurapreetam@gmail.com>
