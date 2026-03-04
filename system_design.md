# System Design Concepts (AI Clinical Research Tools)

This document outlines scalable system patterns for deploying the AI workflow prototypes in this repo in regulated environments.
Focus: **traceability, auditability, and human oversight**.

---

## 1) Reference System Architecture (end-to-end)

```mermaid
flowchart LR
  %% Lanes
  subgraph U[Users]
    U1[Clinical Ops / Regulatory]
    U2[PV / Safety]
    U3[Study Teams]
  end

  subgraph I[Input Layer]
    I1[Protocol PDFs / Text]
    I2[Adverse Event Datasets]
    I3[Site Performance Datasets]
    I4[eConsent Documents]
  end

  subgraph P[Ingestion & Pre-processing]
    P1[Document parsing (PDF/Text)]
    P2[OCR (if needed)]
    P3[Sectioning + Chunking]
    P4[Basic redaction rules]
  end

  subgraph A[AI Processing Layer]
    A1[LLM Extraction (protocol/eConsent)]
    A2[ML Prediction (feasibility)]
    A3[Pattern Detection (PV signals)]
  end

  subgraph S[Structured Output Layer]
    S1[JSON schema output]
    S2[Evidence links to source]
    S3[Confidence scoring]
  end

  subgraph G[Validation & Governance]
    G1[Schema validation]
    G2[Policy checks (PII, claims)]
    G3[Human review queue]
    G4[Audit log + versioning]
  end

  subgraph O[Operational Interfaces]
    O1[Clinical Ops dashboard]
    O2[Safety review dashboard]
    O3[Exports (CSV/JSON)]
    O4[API for integrations]
  end

  U --> I
  I --> P
  P --> A
  A --> S
  S --> G
  G --> O
