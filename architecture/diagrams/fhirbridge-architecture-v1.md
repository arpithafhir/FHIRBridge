# FHIRBridge Architecture Diagram V1

## Target Architecture

```mermaid
flowchart TD

%% Source Systems
subgraph S["Source Systems"]
    E1["Epic-like Systems"]
    C1["Cerner-like System"]
    A1["Allscripts-like System"]
    L1["Independent Lab Source"]
    CL1["Claims Source"]
    SY["Synthea FHIR Bundles"]
end

%% Ingestion
subgraph I["Ingestion & Landing"]
    RAW["Raw Landing Zone<br/>Files first, cloud object storage later"]
    INT["Intermediate / Normalized Layer"]
end

%% Trust and Governance
subgraph T["Trust, Identity & Governance"]
    DQ["Data Quality Layer"]
    MPI["Master Patient Index"]
    PROV["Provenance & Lineage"]
    TERM["Terminology Layer<br/>Source + standard terminology"]
end

%% FHIR Core
subgraph F["Canonical FHIR Core"]
    MAP["FHIR Mapping Engine"]
    VAL["FHIR Validation"]
    STORE["Canonical FHIR Store<br/>JSON files -> PostgreSQL JSONB -> HAPI FHIR"]
end

%% Access and Analytics
subgraph A["Access, Analytics & Intelligence"]
    API["API Layer<br/>FHIR APIs / App APIs"]
    SQLFHIR["SQL on FHIR Views"]
    OMOP["Future OMOP Layer"]
    ANALYTICS["Analytics / Population Health"]
    AI["Future AI Workflows"]
end

%% Cloud
subgraph C["Cloud-Native Future"]
    CLOUD["Cloud Layer<br/>S3 / Blob Storage / Cloud DB / Containers"]
end

S --> RAW
RAW --> INT
INT --> DQ
DQ --> MPI
MPI --> PROV
PROV --> TERM
TERM --> MAP
MAP --> VAL
VAL --> STORE

STORE --> API
STORE --> SQLFHIR
SQLFHIR --> ANALYTICS
STORE --> OMOP
ANALYTICS --> AI
STORE --> CLOUD
API --> CLOUD
```

## Design Notes

FHIRBridge starts locally with file-based storage, then evolves toward PostgreSQL JSONB, HAPI FHIR, SQL on FHIR, and cloud-native deployment.

The Terminology Layer, API Layer, and Cloud Layer are included in V1 because they are part of the long-term enterprise target architecture, even if not fully implemented in Phase 1A.

Security, consent, privacy, audit, access control, and PHI governance are recognized as future extensibility areas when the project evolves beyond synthetic data.

## Future Extensibility Areas

- Security
- Consent
- Privacy
- Audit
- Access Control
- PHI Governance