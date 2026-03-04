# System Architecture (Concept)

This prototype shows how AI could help pharmacovigilance teams surface **potential safety signals** from adverse event (AE) reports, while keeping **human PV review** as the decision gate.

---

## End-to-end workflow

```mermaid
flowchart LR
  A[Adverse Event Reports] --> B[Input Data Processing<br/>cleaning + standardisation]
  B --> C[AI Pattern Detection<br/>clustering / semantic similarity]
  C --> D[Potential Safety Signals<br/>ranked + explainable]
  D --> E[Human Pharmacovigilance Review<br/>triage + confirm + escalate]
```

# What each stage does

Input Data Processing: de-duplicate, normalise terms (e.g., MedDRA-like grouping), basic QC checks.

AI Pattern Detection: group similar events, detect unusual clusters, trend shifts, or severity spikes.

Potential Safety Signals: output a ranked list with reasoning features (why it was flagged).

Human PV Review: confirm signal, request more data, open investigation, or dismiss as noise.

# Guardrails (regulated mindset)

```mermaid
flowchart TB
  X[Model output: clusters + flags] --> Y{Meets signal threshold?}
  Y -->|No| N[Log only<br/>no action]
  Y -->|Yes| H[Human PV review required]
  H --> D{Decision}
  D -->|Dismiss| N
  D -->|Investigate| I[Create case + follow-up actions]
  I --> A1[Audit log + versioning]
```
**Note:** This is a conceptual workflow using example data. It is not a validated pharmacovigilance system and should not be used for safety decisions.
