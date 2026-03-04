# AI eConsent Assistant (Prototype)

A product workflow prototype showing how an AI assistant could improve **informed consent comprehension** and reduce operational burden in clinical trials while maintaining **human oversight** and **auditability**.

## Problem
Informed Consent Forms (ICFs) are often long, complex, and written above typical reading levels. This can lead to:
- low participant comprehension and uneven consent quality
- repeated questions and delays during consent appointments
- inconsistent documentation of what was explained and understood

## Proposed Solution
An AI-assisted eConsent workflow that:
1) extracts structured consent facts (procedures, risks, benefits, rights)
2) generates plain-language explanations at configurable reading levels
3) produces a “teach-back” question set to confirm understanding
4) flags high-risk areas that require clinician review
5) creates an audit trail (what was shown, what was accepted, what changed)

## Key Outputs
- **Structured JSON extraction** (facts + evidence mapping)
- **Plain-language summary** (patient-friendly)
- **Teach-back questions** (comprehension check)
- **Risk & governance flags** (what must be reviewed by humans)
- **Audit metadata** (versioning + redaction + confidence)

## What This Demonstrates (Skills)
- Product thinking in regulated environments (human-in-the-loop, traceability)
- Requirements shaping (outputs, constraints, and measurable outcomes)
- Data structures & API-ready artifacts (JSON schema)
- Clinical trial operations context (consent workflows, documentation needs)

## Files
- `sample_consent.md` — example consent excerpt used as input
- `prompt.md` — prompt template used for structured extraction
- `structured_output.json` — example AI output with confidence + audit fields
- `architecture.md` — system design + governance layer
- `user_flow.md` — user journey and edge cases

## Disclaimer
This is a conceptual prototype using example text. It is not a medical device and must not be used for clinical decision-making. Any real implementation would require privacy/security controls, validation, and regulatory review.
