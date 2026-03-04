# Architecture (Concept)

```mermaid
flowchart LR
  A[Consent text / eICF PDF] --> B[Pre-processing<br/>sectioning + redaction]
  B --> C[LLM Extraction Service<br/>structured facts + evidence]
  C --> D[Policy & Guardrails<br/>PII rules, reading level, banned claims]
  D --> E[Outputs API]
  E --> F1[Patient View<br/>plain-language + glossary]
  E --> F2[Clinician/Coordinator View<br/>flags + evidence]
  E --> F3[Compliance View<br/>audit trail + versioning]

  C --> G[Confidence Scoring]
  G --> F2

  C --> H[Human Review Queue]
  H --> F2

  E --> I[(Audit Store)]
  E --> J[(Config Store<br/>reading level, locale)]


Governance Layer (non-negotiables)

Human-in-the-loop: high-risk sections require clinician sign-off

Evidence traceability: each extracted field includes supporting text

Versioning: output tied to consent version + timestamp

Redaction: remove personal contacts/PII from shared artifacts

No clinical advice: only explain what is in the consent

Success Metrics (example)

% reduction in coordinator time spent answering repeated questions

comprehension score via teach-back completion rate

reduction in consent-related deviations / re-consent events
