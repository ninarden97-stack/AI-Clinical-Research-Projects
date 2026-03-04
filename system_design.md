# System Design Concepts for AI Clinical Research Tools

This document outlines reference architectures for deploying the AI workflow prototypes in this repository in regulated environments.

The goal is **operational usefulness** while maintaining:
- **traceability** (evidence links)
- **auditability** (versioning + logs)
- **human oversight** (review gates)
- **policy controls** (PII / prohibited claims)

---

## 1) Reference System Architecture (end-to-end)

```mermaid
flowchart LR

  subgraph U[Users]
    U1[Clinical Ops / Regulatory]
    U2[PV / Safety]
    U3[Study Teams]
  end

  subgraph I[Input Layer]
    I1[Protocol PDFs / Text]
    I2[AE datasets]
    I3[Site performance datasets]
    I4[eConsent documents]
  end

  subgraph P[Ingestion and Pre-processing]
    P1[Document parsing]
    P2[OCR if needed]
    P3[Sectioning and chunking]
    P4[Basic redaction rules]
  end

  subgraph A[AI Processing Layer]
    A1[LLM extraction]
    A2[ML prediction]
    A3[Pattern detection]
  end

  subgraph S[Structured Output Layer]
    S1[JSON schema output]
    S2[Evidence links to source]
    S3[Confidence scoring]
  end

  subgraph G[Validation and Governance]
    G1[Schema validation]
    G2[Policy checks]
    G3[Human review queue]
    G4[Audit log and versioning]
  end

  subgraph O[Operational Interfaces]
    O1[Dashboards and reports]
    O2[Export to trackers and tools]
    O3[API delivery for integrations]
  end

  U --> I
  I --> P
  P --> A
  A --> S
  S --> G
  G --> O


```mermaid
sequenceDiagram
  autonumber
  participant User as User (Ops/Reg/Safety)
  participant Ingest as Ingestion Service
  participant Prep as Pre-processing
  participant AI as AI Service (LLM/ML)
  participant Gov as Validation + Policies
  participant Review as Human Review
  participant Store as Audit Store
  participant UI as Dashboard / API

  User->>Ingest: Upload protocol / dataset
  Ingest->>Prep: Extract text + normalize + chunk
  Prep->>AI: Send chunks/features
  AI->>Gov: Return JSON + evidence + confidence
  Gov->>Review: Route flagged / low-confidence items
  Review->>Gov: Approve / correct / override
  Gov->>Store: Write audit log + version
  Gov->>UI: Publish validated output
