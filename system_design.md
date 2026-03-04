# System Design Concepts for AI Clinical Research Tools

This document outlines practical system design concepts for deploying the AI workflow prototypes in this repository.

The designs focus on **scalable and responsible AI deployment in regulated healthcare environments**, where **traceability, auditability, and human oversight** are essential.

---

## 1) Reference System Architecture (end-to-end)
┌──────────────────────────────┐
│ Users │
│ - Clinical Ops / Regulatory │
│ - PV / Safety │
│ - Study Teams │
└───────────────┬──────────────┘
│
v
┌──────────────────────────────┐
│ Input Layer │
│ - Protocol PDFs / text │
│ - AE datasets │
│ - Site performance datasets │
│ - eConsent documents │
└───────────────┬──────────────┘
│
v
┌──────────────────────────────┐
│ Ingestion & Pre-processing │
│ - Document parsing (PDF/text) │
│ - OCR if needed │
│ - Sectioning + chunking │
│ - Basic redaction rules │
└───────────────┬──────────────┘
│
v
┌──────────────────────────────┐
│ AI Processing Layer │
│ - LLM extraction (protocol) │
│ - ML prediction (feasibility) │
│ - Pattern detection (PV) │
│ - Summarisation (eConsent) │
└───────────────┬──────────────┘
│
v
┌──────────────────────────────┐
│ Structured Output Layer │
│ - JSON schema outputs │
│ - Evidence links to source │
│ - Confidence scoring │
└───────────────┬──────────────┘
│
v
┌──────────────────────────────┐
│ Validation & Governance │
│ - Schema validation │
│ - Policy checks (PII, claims) │
│ - Human review queue │
│ - Audit log + versioning │
└───────────────┬──────────────┘
│
v
┌──────────────────────────────┐
│ Operational Interfaces │
│ - Dashboards / reports │
│ - Export to trackers / tools │
│ - Implementation/API delivery │
└──────────────────────────────┘

---

## 2) Data Flow (how information moves)
Input document / dataset
|
v
Pre-process (extract text, chunk, normalize)
|
v
AI processing (LLM / ML / rules)
|
v
Structured output (JSON + evidence + confidence)
|
v
Human validation (approve / correct / override)
|
v
Publish to dashboard / export / API response
|
v
Store audit trail + version history


---

## 3) Human-in-the-loop governance (required for regulated AI)
AI output produced
|
v
Confidence scoring
|
+-------------------------+
| |
v v
High confidence Medium/Low confidence
(auto-pass allowed) (human review required)
| |
v v
Structured output Review + corrections
| |
+-----------+-------------+
v
Approved output
|
v
Audit log + versioning

Why this matters:
- Keeps AI **decision-support**, not autonomous decision-making
- Preserves **inspection readiness** and **traceability**
- Prevents “silent failure” in ambiguous protocol content

---

## 4) Core components (mapped to your portfolio projects)

### A) Data ingestion
Handles input types such as:
- protocol PDFs / text
- adverse event datasets
- site performance datasets
- consent documents

### B) Pre-processing
Typical steps:
- PDF parsing / OCR (if needed)
- section detection + chunking
- lightweight redaction rules (e.g., remove personal contact info)

### C) AI processing
Examples:
- Protocol Analyzer: LLM extraction → trial metadata, endpoints, eligibility, schedules
- AE Signal Detector: clustering / rule triggers → candidate safety signals
- Site Feasibility: ML scoring → feasibility score + risk drivers + actions
- eConsent: plain-language summaries + teach-back questions

### D) Structured output
All systems output **machine-readable JSON** that includes:
- extracted values
- evidence/source text reference
- confidence score
- “human review required” flags

### E) Validation & governance
- schema validation (ensure output is complete and consistent)
- policy checks (PII handling, safe language, no unsupported claims)
- human review workflow
- audit logs and versioning

### F) Operational interface
Outputs can be consumed via:
- dashboards (clinical ops / PV / regulatory)
- exports (CSV/JSON)
- API integration into internal tools

---

## 5) Deployment considerations (practical)

### Infrastructure patterns
- API-first services (request/response)
- batch pipelines (nightly/weekly scoring)
- secure data store (encrypted at rest/in transit)
- audit logging (who changed what and why)

### Key non-functional requirements
- Security: access control, least privilege, encrypted storage
- Compliance: traceability, documentation, human validation
- Reliability: retries, monitoring, error handling
- Transparency: evidence-linked outputs + confidence scoring

---

## 6) Principles used across these designs

- **Human oversight by default** in regulated decision-making
- **Evidence traceability** from output back to source text
- **Structured outputs** to enable downstream automation
- **Auditability and versioning** for inspection readiness
- **Pragmatic deployment** (simple pipelines first, scale later)

---
