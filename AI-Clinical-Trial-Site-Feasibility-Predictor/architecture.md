# System Architecture (Concept)

This prototype demonstrates how machine learning could support clinical trial site selection by predicting recruitment feasibility using historical operational data.

```mermaid
flowchart LR

A[Site Performance Data<br/>historical enrollment] --> B[Data Processing<br/>cleaning + feature engineering]

B --> C[Training Dataset]

C --> D[ML Model Training<br/>Random Forest / Gradient Boosting]

D --> E[Model Evaluation<br/>accuracy + calibration]

E --> F[Prediction Service<br/>API / batch scoring]

F --> G[Site Feasibility Scores]

G --> H[Clinical Ops Dashboard]

H --> I[Human Validation + Decision]
```

Example prediction output

| Site | Feasibility Score | Risk Level | Key Drivers |
|-----|-----|-----|-----|
| Site A | 0.82 | Low | high enrollment history |
| Site B | 0.55 | Medium | slow startup timelines |

Key system components include:

**Data processing**
- cleaning operational datasets
- generating features from site performance

**Machine learning layer**
- training predictive models using historical recruitment data
- evaluating model accuracy and calibration

**Prediction service**
- generating feasibility scores for candidate sites
- supporting batch or API-based predictions

**Operational interface**
- dashboards for clinical operations teams
- human validation of recommended sites
