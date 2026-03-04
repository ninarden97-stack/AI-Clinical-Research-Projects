# System Architecture (Concept)

This diagram illustrates how an AI-assisted eConsent system could process informed consent documents while maintaining human oversight and auditability.

```mermaid
flowchart LR

A[Consent text / eICF PDF] --> B[Pre-processing<br/>sectioning + redaction]

B --> C[LLM Extraction Service<br/>structured facts + evidence]

C --> D[Validation & Schema Enforcement<br/>JSON structure + field validation]

D --> E[Policy & Guardrails<br/>PII rules, reading level, banned claims]

E --> F[Outputs API]

C --> G[Confidence Scoring]

C --> H[Human Review Queue]

F --> I[Patient View<br/>plain-language explanation + glossary]

F --> J[Clinician / Coordinator Dashboard<br/>flags + evidence mapping]

F --> K[Compliance View<br/>audit trail + versioning]

F --> L[(Audit Store)]

F --> M[(Configuration Store<br/>reading level, locale, templates)]
