# ADR-006: Data Quality Framework

## Status

Accepted

## Context

FHIRBridge integrates data from multiple healthcare sources.

Healthcare data often contains:

* Missing values
* Invalid values
* Duplicate records
* Conflicting values
* Different coding systems
* Different levels of granularity

Trusted healthcare analytics and interoperability require a structured approach to data quality.

## Decision

FHIRBridge will implement a progressive data quality framework.

Data quality issues will be surfaced, measured, and governed rather than hidden.

## Phase 1A Quality Dimensions

FHIRBridge will initially evaluate:

### Completeness

Examples:

* Missing DOB
* Missing gender
* Missing identifiers

### Validity

Examples:

* Future birth dates
* Invalid phone numbers
* Invalid code formats

### Consistency

Examples:

* Conflicting gender values
* Conflicting demographic attributes

### Uniqueness

Examples:

* Duplicate patients
* Duplicate records

## Future Quality Dimensions

### Semantic Quality

Examples:

* Local code vs standard code
* Different coding systems
* Different terminology representations

### Terminology Quality

Examples:

* Unmapped codes
* Invalid value sets
* Terminology drift

### Cross-Source Quality

Examples:

* Conflicting source values
* Claims vs EHR differences
* Lab vs EHR differences

## Architecture Principles

### Preserve Source Data

Raw source data should never be silently modified.

### Surface Issues

Quality issues should be flagged and reported.

### Separate Observation from Correction

FHIRBridge should identify quality issues before attempting remediation.

### Maintain Traceability

Every quality issue should be traceable to:

* Source system
* Source file
* Source record
* Transformation stage

## Quality Severity Levels

* Info
* Warning
* Error
* Critical

## Future Quality Metrics

Examples:

* Missing DOB rate
* Duplicate patient rate
* Invalid code rate
* Unmapped terminology rate
* Cross-source conflict rate

## Rationale

Data quality is foundational for:

* MPI
* Provenance
* FHIR mapping
* Analytics
* Quality measurement
* AI

Poor quality data should be visible and measurable rather than hidden.

## Consequences

FHIRBridge must support:

* Quality rule execution
* Quality issue reporting
* Quality metrics
* Quality lineage
* Future semantic interoperability validation
