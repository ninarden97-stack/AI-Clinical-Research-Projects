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
