# AI Clinical Trial Protocol Analyser

## Dataset
This project uses publicly available study summaries from ClinicalTrials.gov as a proxy for clinical trial protocols.
Full protocols can exceed 200–600 pages. For demonstration purposes, this proof-of-concept uses structured trial descriptions that contain many of the key elements required for protocol review

## Problem
Clinical trial protocols often exceed 150–300 pages and require manual extraction of key elements such as endpoints, eligibility criteria, and safety considerations.
Protocol review can delay trial startup and regulatory submissions.


## Concept
An AI workflow that extracts key structured information from protocols.

## Example Outputs
1) input_sample.md
2) output_sample.json
3) prompt.md

   
## Goal
Explore how AI could assist clinical operations and regulatory review.

Architecture Concept

Protocol PDF
↓
Document parsing
↓
AI extraction
↓
Structured output
↓
Human validation
