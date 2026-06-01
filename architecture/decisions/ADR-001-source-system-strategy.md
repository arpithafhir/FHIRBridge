# ADR-001: Source System Strategy

## Status
Accepted

## Context
FHIRBridge is designed to simulate real-world healthcare interoperability where data comes from multiple clinical systems, supplemental systems, claims feeds, lab systems, and future FHIR-native sources.

Healthcare data is rarely clean or centralized. It often comes from different vendors, different formats, different identifiers, different coding practices, and different levels of data quality.

## Decision
FHIRBridge will support a progressive source-system strategy.

Initial Phase 1 source ecosystem:

### Clinical EHR Sources
- Epic-like System A
- Epic-like System B
- Epic-like System C
- Cerner-like System D
- Allscripts-like System E

### Supplemental Sources
- Independent Lab Source
- Claims Source A

### Native FHIR Source
- Synthea FHIR Bundles

Phase 1 source mix target:
- 70% Epic-like clinical data
- 15% Cerner-like clinical data
- 10% Allscripts-like clinical data
- 5% lab and claims supplemental data

## Future Source Expansion
FHIRBridge will be designed for progressive source complexity.

Future source categories may include:
- Additional claims sources
- Additional lab sources
- Provider directory sources
- HAPI FHIR data
- OMOP datasets
- Oncology datasets
- Quality measurement datasets

## Rationale
This strategy keeps Phase 1 realistic but manageable.

The project starts with multiple clinical systems and one claims/lab pattern, then expands toward more complex real-world healthcare data ecosystems over time.

This allows the project to teach interoperability progressively instead of overwhelming the first implementation phase.

## Consequences
FHIRBridge must preserve source-system identity, raw source data, source identifiers, and mapping context.

The architecture must support:
- source-specific schemas
- clean and messy data
- provenance
- data quality tracking
- source-to-target mapping
- future source expansion