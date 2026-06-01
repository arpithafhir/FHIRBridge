# ADR-009: Terminology Strategy

## Status

Accepted

## Context

FHIRBridge will ingest healthcare data from multiple source systems. These systems may use local codes, free text, different coding standards, different levels of granularity, and different terminology practices.

Semantic interoperability requires more than valid FHIR structure. The data must also preserve meaning across systems.

## Decision

FHIRBridge will implement terminology capability progressively.

The terminology architecture will remain extensible and standards-agnostic so the project can support current and future healthcare terminology standards, governance frameworks, and semantic interoperability capabilities.

## Terminology Maturity Model

### Level 1: Preserve Source Terminology

FHIRBridge will preserve:

- Source code
- Source text
- Source coding system
- Source system
- Source record context

### Level 2: Industry Standard Terminologies

FHIRBridge will progressively support widely adopted healthcare terminology standards used across clinical, administrative, laboratory, pharmacy, billing, quality, research, and interoperability workflows.

Examples include:

- ICD-10-CM
- CPT
- HCPCS
- LOINC
- SNOMED CT
- RxNorm

but are not limited to these standards.

### Level 3: FHIR Terminology Constructs

FHIRBridge will progressively explore FHIR terminology constructs.

Examples include:

- CodeSystem
- ValueSet
- ConceptMap

but are not limited to these constructs.

### Level 4: Terminology Governance and Quality

FHIRBridge will progressively evaluate terminology governance and semantic quality capabilities.

Examples include:

- VSAC
- Value set governance
- Terminology quality validation
- Semantic quality controls

but are not limited to these capabilities.

### Level 5: Enterprise Semantic Interoperability

FHIRBridge will progressively evaluate enterprise semantic interoperability capabilities.

Examples include:

- UMLS
- FHIR terminology services
- Terminology servers
- Cross-system semantic interoperability

but are not limited to these capabilities.

## Architecture Principles

FHIRBridge will preserve both source terminology and standard terminology.

Example:

- Source code: DM2
- Source text: Type 2 Diabetes
- Standard code: ICD-10-CM E11.9

FHIRBridge should not discard source terminology after mapping.

FHIR valid does not always mean semantically interoperable.

## Phase 1A Scope

Phase 1A will focus on:

- Preserving source terminology
- Capturing source text
- Capturing source coding system when available
- Introducing simple mappings where useful
- Avoiding full terminology-service complexity

## Future Scope

Future phases may introduce:

- Standard terminology mappings
- Value set usage
- Concept maps
- Terminology validation
- VSAC exploration
- UMLS exploration
- FHIR terminology service patterns
- Semantic interoperability checks

## Rationale

Terminology is central to trusted healthcare interoperability.

The project should learn terminology concepts early while avoiding enterprise terminology complexity too soon.

An extensible terminology strategy allows FHIRBridge to support clinical, claims, quality, oncology, OMOP, SQL on FHIR, analytics, and AI use cases over time.

## Consequences

FHIRBridge must preserve terminology metadata across raw, intermediate, and canonical FHIR layers.

Future implementations must support:

- Source terminology preservation
- Standard terminology mapping
- Mapping traceability
- Terminology quality checks
- Semantic interoperability expansion