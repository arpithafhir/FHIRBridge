# ADR-002: Storage Strategy

## Status

Accepted

## Context

FHIRBridge requires storage for source data, intermediate transformation outputs, canonical FHIR resources, and future analytics workloads.

The architecture must support:

* Data lineage
* Auditability
* Reprocessing
* Future cloud adoption
* Future analytics workloads
* Progressive learning of healthcare interoperability concepts

## Decision

FHIRBridge will adopt a progressive storage strategy.

### Phase 1A

File-based storage.

Directory structure:

* /raw
* /intermediate
* /fhir
* /synthea/fhir-bundles

FHIRBridge will preserve:

* Raw source data
* Intermediate transformation outputs
* Canonical FHIR resources
* Native FHIR bundles from Synthea

### Phase 2

PostgreSQL JSONB storage.

Objectives:

* Persist canonical FHIR resources
* Introduce database concepts
* Support analytics queries
* Prepare for future SQL on FHIR patterns

### Phase 3

HAPI FHIR server.

Objectives:

* FHIR-native persistence
* FHIR API access
* Resource search
* FHIR validation support

### Phase 4

Cloud-native architecture.

Potential technologies:

* AWS S3
* Azure Blob Storage
* Google Cloud Storage
* Cloud databases
* Containerized deployment

### Future

* SQL on FHIR
* OMOP integration
* AI and analytics workloads

## Rationale

The architecture is designed to teach interoperability concepts progressively.

Starting with file-based storage allows focus on:

* Source-system understanding
* Data transformation
* FHIR mapping
* Canonical resource generation

before introducing database administration and cloud infrastructure complexity.

The architecture remains aligned with modern enterprise healthcare patterns through planned cloud-native evolution.

## Consequences

FHIRBridge must preserve:

* Raw data
* Intermediate data
* Canonical FHIR data

Storage layers must support future:

* Provenance
* Lineage
* Auditability
* Reprocessing
* Analytics workloads
* Semantic interoperability initiatives
* Cloud deployment patterns
