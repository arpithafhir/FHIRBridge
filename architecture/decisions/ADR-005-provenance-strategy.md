# ADR-005: Provenance Strategy

## Status

Accepted

## Context

FHIRBridge will ingest data from multiple source systems and transform that data into canonical FHIR resources.

Healthcare interoperability requires understanding not only the final data, but also:

* Where the data originated
* Which system supplied it
* When it was received
* What transformations occurred
* What target resource was generated

Without provenance, it becomes difficult to troubleshoot, audit, validate, or trust healthcare data.

## Decision

FHIRBridge will implement provenance tracking across all major processing stages.

Phase 1A provenance will track:

* Source system
* Source file
* Source record identifier
* Transformation step
* Processing timestamp
* Target FHIR resource identifier

## Provenance Flow

Example:

Epic-A
→ patient_001.csv
→ Patient Record 12345
→ Patient Mapping Transformation
→ Timestamp
→ FHIR Patient Resource

FHIRBridge must be able to trace any canonical FHIR resource back to its original source.

## Architecture Principle

Data should never lose its origin.

FHIRBridge must preserve sufficient provenance information to understand:

* Where data came from
* How data was transformed
* Why a target value exists

## Future Evolution

Future provenance capabilities may include:

* Transformation versioning
* Pipeline version tracking
* Match decisions
* MPI decisions
* Data quality decisions
* Terminology mapping decisions
* Cloud processing metadata

## Rationale

Healthcare interoperability requires trust.

Clinicians, analysts, and downstream systems must be able to understand the origin and processing history of data.

Provenance is a foundational capability for:

* Auditability
* Lineage
* Data quality
* MPI
* Analytics
* AI

## Consequences

FHIRBridge must preserve provenance metadata across:

* Raw data
* Intermediate data
* Canonical FHIR resources

Future architecture components must remain compatible with provenance requirements.

