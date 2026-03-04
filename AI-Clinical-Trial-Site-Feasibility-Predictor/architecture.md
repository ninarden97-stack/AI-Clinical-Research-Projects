# System Architecture (Concept)

This prototype demonstrates how machine learning could support clinical trial site selection by predicting recruitment feasibility using historical operational data.

```mermaid
flowchart LR

subgraph Data_Sources
A["Site performance dataset<br/>(historical enrollment, screen failures)"]
B["Protocol factors<br/>(visit burden, inclusion complexity)"]
C["Operational metrics<br/>(startup timelines, query rate, deviations)"]
end

subgraph Data_Processing
D["Data cleaning and normalization"]
E["Feature engineering<br/>(site enrollment trends, sponsor effects)"]
F["Training dataset preparation"]
end

subgraph Modeling
G["Model training<br/>(Random Forest / Gradient Boosted Trees)"]
H["Model evaluation<br/>(accuracy, recall, calibration)"]
I["Explainability layer<br/>(feature importance / SHAP)"]
end

subgraph Serving
J["Prediction API"]
K["Batch scoring pipeline<br/>(weekly updates)"]
end

subgraph Product_Surface
L["Clinical operations dashboard<br/>(site feasibility ranking)"]
M["Operational recommendations<br/>(add sites, adjust timeline)"]
end

subgraph Governance
N["Human validation<br/>(clinical operations review)"]
O["Audit log and model monitoring"]
end

A --> D
B --> D
C --> D

D --> E
E --> F

F --> G
G --> H
G --> I

G --> J
G --> K

J --> L
K --> L

L --> M
M --> N

N --> O
```
