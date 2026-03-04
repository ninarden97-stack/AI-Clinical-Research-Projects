flowchart LR

A["Consent text / eICF PDF"] --> B["Pre-processing: sectioning + redaction"]
B --> C["LLM extraction service: structured facts + evidence"]
C --> D["Validation and schema enforcement: JSON + field validation"]
D --> E["Policy and guardrails: PII rules, reading level, banned claims"]
E --> F["Outputs API"]

C --> G["Confidence scoring"]
C --> H["Human review queue"]

F --> I["Patient view: plain language + glossary"]
F --> J["Clinician / coordinator view: flags + evidence"]
F --> K["Compliance view: audit trail + versioning"]

F --> L[("Audit store")]
F --> M[("Configuration store: reading level, locale, templates")]
