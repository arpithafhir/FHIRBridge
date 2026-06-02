# ADR-003: OMOP Roadmap

## Status

Accepted

## Context

FHIRBridge is designed to generate canonical FHIR resources from multiple healthcare data sources.

FHIR is well suited for interoperability and APIs, while OMOP is commonly used for observational research, population health analytics, cohort discovery, and real-world evidence.

FHIRBridge should remain open to future OMOP integration without making OMOP part of Phase 1A implementation.

## Decision

FHIRBridge will treat OMOP as a future analytics and research model, not as the primary Phase 1A implementation model.

Phase 1A will focus on:

- Source data
- Raw storage
- Intermediate normalization
- Canonical models
- FHIR R4 Patient resources
- MPI
- Provenance
- Data quality

Future phases may evaluate:

- FHIR-to-OMOP mapping
- OMOP common data model concepts
- Cohort analytics
- Oncology analytics
- Real-world evidence use cases

## Rationale

FHIR and OMOP solve different problems.

FHIRBridge will use FHIR for interoperability and API-oriented exchange, while OMOP may be introduced later for analytics and research-oriented use cases.

## Consequences

FHIRBridge should preserve enough source data, terminology context, provenance, and canonical modeling structure to support future OMOP mapping.

OMOP integration should not block Phase 1A implementation.
