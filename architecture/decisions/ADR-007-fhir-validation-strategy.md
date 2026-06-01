# ADR-007: FHIR Validation Strategy

## Status

Accepted

## Context

FHIRBridge will generate canonical FHIR resources from messy, multi-source healthcare data and will also ingest native FHIR data from sources such as Synthea.

FHIR validation is required to ensure that generated resources are structurally correct, usable, and progressively aligned with real-world interoperability expectations.

## Decision

FHIRBridge will implement FHIR validation progressively.

## FHIR Validation Maturity Model

### Level 1: Structural Validation

Validate that generated resources follow valid FHIR JSON structure.

Examples:
- resourceType is present
- required fields are present where applicable
- JSON format is valid
- Patient resource structure is correct

### Level 2: Resource Relationship Validation

Validate that resources reference each other correctly.

Examples:
- Encounter references Patient
- Observation references Patient
- DiagnosticReport references Patient
- MedicationRequest references Patient

### Level 3: Profile Validation

Future enhancement.

Validate resources against profiles such as:
- US Core
- QI-Core
- mCODE
- Custom FHIRBridge profiles

### Level 4: Terminology Validation

Future enhancement.

Validate coded elements against:
- CodeSystem
- ValueSet
- ConceptMap
- LOINC
- SNOMED CT
- RxNorm
- ICD-10-CM
- CPT
- HCPCS
- VSAC

### Level 5: Interoperability Validation

Future enhancement.

Validate whether resources are not only valid FHIR, but also useful across systems.

Examples:
- Standard terminology usage
- Consistent references
- Expected search behavior
- API usability
- Analytics readiness

## Architecture Principle

FHIR valid does not always mean clinically meaningful, analytically useful, or semantically interoperable.

FHIRBridge must distinguish between:

- Data quality validation
- FHIR structural validation
- FHIR profile validation
- Terminology validation
- Interoperability validation

## Phase 1A Validation Scope

Phase 1A will focus on:

- Patient resource structure
- Valid JSON output
- Required Patient fields
- Identifier structure
- Name structure
- Gender normalization
- Birth date formatting
- Source identifier preservation

## Future Validation Challenges

FHIRBridge should eventually handle:

- Missing required data
- Invalid references
- Broken resource relationships
- Local codes without standard mappings
- Conflicting source values
- Profile conformance failures
- Terminology binding failures
- Version differences across FHIR releases
- Validation differences between generated FHIR and Synthea FHIR
- Validation differences between file-based FHIR and HAPI FHIR server behavior

## Rationale

FHIR validation ensures that FHIRBridge produces resources that can be trusted, exchanged, queried, and extended.

Starting with simple structural validation keeps Phase 1A manageable while creating a path toward real-world interoperability validation.

## Consequences

FHIRBridge must support:

- Validation checks
- Validation error reporting
- Validation warnings
- Validation logs
- Future profile validation
- Future terminology validation
- Future HAPI FHIR validation