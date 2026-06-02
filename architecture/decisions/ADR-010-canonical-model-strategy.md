# ADR-010: Canonical Model Strategy

## Status

Accepted

## Context

FHIRBridge is designed as an extensible healthcare interoperability, intelligence, and application platform.

Healthcare data originates from multiple structured and unstructured sources that represent similar concepts in different ways. Examples include EHRs, claims systems, laboratories, FHIR APIs, clinical documents, clinical notes, voice transcripts, and future data sources.

FHIRBridge requires a consistent internal modeling strategy to normalize, validate, govern, and transform data before it is used for interoperability, analytics, intelligence, and applications.

## Decision

FHIRBridge will use a canonical modeling framework consisting of:

1. Internal canonical models for structured healthcare data
2. Canonical concepts for intelligence extracted from unstructured data
3. FHIR R4 as the primary canonical interoperability layer

The canonical framework serves as the trusted normalization layer between source systems and downstream consumers.

FHIR remains the primary interoperability standard, while canonical models provide flexibility, extensibility, and platform independence.

## Canonical Data Flow

### Structured Data

```text
Source Systems
      ↓
Raw Layer
      ↓
Canonical Models
      ↓
FHIR R4 Canonical Layer
      ↓
Analytics
SQL on FHIR
OMOP
SMART Applications
Intelligence Layer
```

### Unstructured Data

```text
Clinical Notes
Voice
Documents
Reports
      ↓
AI / NLP Extraction
      ↓
Canonical Concepts
      ↓
FHIR Resources (when appropriate)
      ↓
Intelligence Layer
```

## Phase 1A Canonical Models

Initial canonical models include:

* CanonicalPatient
* CanonicalIdentifier
* CanonicalAddress
* CanonicalTelecom
* CanonicalCareContext
* CanonicalProvenance
* CanonicalDataQualityIssue

These models support generation of FHIR R4 Patient resources.

## Future Canonical Models

As the platform evolves, additional canonical models may include:

* CanonicalEncounter
* CanonicalClaim
* CanonicalLabResult
* CanonicalMedication
* CanonicalCondition
* CanonicalObservation
* CanonicalProcedure
* CanonicalCarePlan
* CanonicalDocument

## Canonical Concepts

FHIRBridge recognizes that meaningful healthcare intelligence often originates from unstructured sources.

Concepts extracted from notes, documents, voice transcripts, and future unstructured sources are considered first-class canonical entities.

Examples include:

* CanonicalExtractedConcept
* CanonicalClinicalInsight
* CanonicalOncologyConcept
* Future domain-specific intelligence concepts

Canonical concepts may contribute to:

* FHIR resources
* Analytics datasets
* AI workflows
* Clinical intelligence products
* SMART on FHIR applications

## Architecture Principles

### Separation of Concerns

FHIRBridge separates:

* Raw source data
* Canonical models
* Canonical concepts
* FHIR interoperability resources
* Analytics products
* Intelligence products
* Application products

### Extensibility

Canonical models and concepts must support future:

* Source systems
* Data formats
* FHIR resources
* Claims data
* Terminology services
* Unstructured data
* AI workflows
* SMART applications
* Future healthcare standards

without requiring platform redesign.

### Intelligence Enablement

The canonical framework is designed to support both interoperability and intelligence.

FHIRBridge treats healthcare intelligence as a first-class architectural capability rather than a downstream afterthought.

## Rationale

This strategy creates a stable internal architecture while preserving interoperability through FHIR.

The canonical framework enables:

* Data normalization
* Source system independence
* Reusable platform capabilities
* Longitudinal patient records
* Healthcare intelligence
* SMART application development
* Future platform evolution

without locking FHIRBridge to a specific technology, source system, or implementation pattern.

## Consequences

FHIRBridge will maintain:

* Raw source preservation
* Canonical normalization
* Canonical intelligence concepts
* FHIR interoperability outputs
* Provenance and lineage
* Future analytics capabilities
* Future intelligence capabilities
* Future application capabilities

This strategy supports the long-term vision of FHIRBridge as a trusted healthcare interoperability, intelligence, and application platform.

