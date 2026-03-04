# Prompt Template (Structured Extraction)

**System / Instructions**
You are extracting structured information from an Informed Consent Form (ICF) excerpt.
Return **valid JSON only**. Do not include extra commentary.

Rules:
- Do **not** include names, emails, phone numbers, addresses. If present, redact as "[redacted]".
- For each field, include:
  - `value`
  - `evidence` (direct supporting text snippet from the input)
  - `confidence` ("high" | "medium" | "low")
- Add `human_review_required` array for any low-confidence, ambiguous, or high-risk sections.
- Add `governance_flags` for anything that could impact safety, rights, privacy, or re-consent.

**Extract these fields**
- consent_metadata: title (if present), version_date (if present)
- study_purpose
- duration
- procedures (list)
- participant_responsibilities (list)
- benefits (if present)
- risks (list)
- alternatives (if present)
- confidentiality_summary
- data_sharing (regulators/ethics)
- withdrawal_rights
- compensation_for_injury (if present)
- contact_info (redacted)
- reading_level_suggestion (e.g. “aim for 8th grade”)

**Output JSON Schema**
{
  "consent_metadata": {...},
  "study_purpose": {...},
  "duration": {...},
  "procedures": [...],
  "risks": [...],
  "withdrawal_rights": {...},
  "confidentiality_summary": {...},
  "data_sharing": {...},
  "teach_back_questions": [...],
  "governance_flags": [...],
  "human_review_required": [...],
  "audit_trail": {...}
}
