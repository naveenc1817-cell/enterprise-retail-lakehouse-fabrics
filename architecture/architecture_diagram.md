# Architecture Diagram

```mermaid
flowchart TD

    A[ADLS Gen2<br/>Raw Source Files] --> B[Fabric Data Pipeline<br/>Copy Activity]

    B --> C[OneLake Lakehouse<br/>Bronze Files]

    C --> D[Bronze Notebook<br/>Create Bronze Delta Tables]

    D --> W1[Wait Activity<br/>60-120 sec]

    W1 --> E[Silver Notebook<br/>Clean & Standardize Data]

    E --> W2[Wait Activity<br/>60-120 sec]

    W2 --> F[Gold Notebook<br/>Create Sales Fact Table]

    F --> W3[Wait Activity<br/>60-120 sec]

    W3 --> G[Incremental MERGE Notebook<br/>Upsert Customer & Order Updates]

    G --> W4[Wait Activity<br/>60-120 sec]

    W4 --> H[Data Quality Notebook<br/>Validation Checks]

    H --> I[Gold Tables<br/>sales_fact + validation_results]

    I --> J[Power BI Semantic Model]

    J --> K[Power BI Dashboard<br/>Executive + Operational Monitoring]

    subgraph Medallion Architecture
        C
        D
        E
        F
        I
    end

    subgraph Production Features
        G
        H
        W1
        W2
        W3
        W4
    end
