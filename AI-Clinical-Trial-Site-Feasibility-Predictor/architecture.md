```mermaid
sequenceDiagram
autonumber
participant Ops as Clinical Ops User
participant UI as Dashboard
participant API as Prediction API
participant FE as Feature Pipeline
participant M as Model Service
participant DB as Data Store
participant Log as Audit Log

Ops->>UI: Select trial + candidate sites
UI->>API: Request site feasibility scores
API->>DB: Fetch latest site + protocol + ops signals
DB-->>API: Return raw datasets
API->>FE: Run feature engineering
FE-->>API: Return feature set
API->>M: Score sites (RF/XGBoost)
M-->>API: Return scores + explanations
API-->>UI: Display risk bands + top drivers
Ops->>UI: Validate / override site shortlist
UI->>Log: Store decision + rationale
UI-->>Ops: Export shortlist + recommended actions
