# System Architecture

This project demonstrates how AI could support clinical trial protocol analysis.

The workflow converts unstructured protocol text into structured trial data for operational and regulatory review.

## Workflow

Clinical Trial Protocol Text
        │
        ▼
Input Processing
(input_sample.md)
        │
        ▼
Prompt Template
(prompt.md)
        │
        ▼
Large Language Model
(Structured Extraction)
        │
        ▼
Structured JSON Output
(output_sample.json)
        │
        ▼
Human Review Layer
(Regulatory / Clinical Ops)
        │
        ▼
Validated Trial Summary

## Key Features

• Evidence-linked extraction  
• Human review flags for uncertain fields  
• Regulatory risk indicators  
• Confidence scoring for extracted data  

This design supports **AI-assisted protocol review while maintaining human oversight required in regulated clinical environments**.
