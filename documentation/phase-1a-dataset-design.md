# Phase 1A Dataset Design

## Purpose

Phase 1A will create synthetic patient source data to test ingestion, canonical modeling, MPI, provenance, data quality, FHIR R4 Patient generation, and validation.

## Dataset Scope

Phase 1A will include:

- 20 canonical patients
- 36 total source records
- 18 Epic-like CSV records
- 18 Cerner-like CSV records
- 8 overlapping patients across both systems
- 12 non-overlapping patients across one system only

Expected output:

- 20 CanonicalPatient records
- 20 FHIR R4 Patient resources
- MPI match report
- Provenance report
- Data quality report

## Phase 1A Source Systems

### Epic-like Source

Format:

- CSV

Purpose:

- Simulate EHR-style patient data using Epic-like naming and identifiers.

### Cerner-like Source

Format:

- CSV

Purpose:

- Simulate EHR-style patient data using Cerner-like naming and identifiers.

### Synthea Source

Format:

- FHIR R4 Bundle

Purpose:

- Provide FHIR-native comparison data.

## MPI and Data Quality Challenges

The dataset will intentionally include:

- Different identifiers
- Different field names
- Different name formats
- Different phone formats
- Different address formats
- Missing values
- Minor demographic differences
- Source provenance
- Data quality flags
- Canonical patient creation

## Overlapping Patient Scenarios

The 8 overlapping patients will test:

1. Exact match
2. Nickname variation
3. Shortened name
4. Middle initial difference
5. Phone format difference
6. Address format difference
7. Missing value in one source
8. Gender normalization

## Phase 1A Boundaries

Phase 1A will not include:

- HL7 v2
- CCDA
- Claims
- AI extraction
- SMART applications
- Cloud deployment
- OMOP implementation
- Complex probabilistic MPI

These are deferred to future roadmap phases.