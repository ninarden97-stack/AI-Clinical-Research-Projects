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


Governance & Safety Layers

Healthcare AI systems must operate with strict oversight.

This architecture intentionally includes:

Human-in-the-loop review

Low confidence outputs or high-risk sections are routed to a human reviewer.

Evidence traceability

Each extracted field links to supporting text from the source document.

Auditability

Every generated output is versioned and stored with timestamps.

Policy guardrails

The system prevents generation of:

medical advice

unsupported claims

patient identifiable information
