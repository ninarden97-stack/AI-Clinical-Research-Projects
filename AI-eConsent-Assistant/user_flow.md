
# User Flow (Product)

## Primary user
- Trial participant (patient)
## Secondary users
- Clinical Research Coordinator (CRC)
- Investigator/Clinician
- QA/Compliance

## Happy path
1. CRC uploads/links the ICF version to the eConsent system.
2. System generates:
   - plain-language summary (reading level configurable)
   - glossary of terms
   - teach-back questions
   - key risks/rights checklist
3. Participant reviews content and completes teach-back questions.
4. CRC dashboard shows:
   - completion status
   - flagged misunderstandings
   - sections requiring clinician sign-off
5. Clinician reviews flagged sections and signs off.
6. Audit package saved (version, timestamps, what was shown, what changed).

## Edge cases
- Participant prefers another language (locale switch + translator workflow)
- Consent updated mid-study (re-consent triggered + diff view)
- Participant low digital literacy (assisted mode for CRC)
- High-risk procedures (e.g., biopsy, radiation, genetic testing) auto-flagged
- Conflicting text (system flags ambiguity + requires human validation)

## Acceptance criteria (examples)
- Every extracted field includes evidence text and confidence.
- No personal contact info is stored in outputs.
- Any low-confidence item is automatically routed to human review.
- Teach-back answers are stored as “comprehension confirmation” metadata.
