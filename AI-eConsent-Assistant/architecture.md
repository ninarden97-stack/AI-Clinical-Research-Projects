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
