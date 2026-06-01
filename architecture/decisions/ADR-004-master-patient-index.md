# ADR-004: Master Patient Index Strategy

## Status

Accepted

## Context

FHIRBridge will ingest patient data from multiple clinical systems, lab systems, claims feeds, and future FHIR-native sources.

The same real-world patient may appear in different systems with different identifiers and demographic values.

Examples:

* Epic MRN
* Cerner patient ID
* Allscripts local patient key
* Lab patient ID
* Claims member ID
* Future FHIR Patient ID

Without identity matching, FHIRBridge would create isolated patient records instead of a unified longitudinal patient view.

## Decision

FHIRBridge will include a Master Patient Index strategy.

Phase 1A will begin with deterministic matching.

Future phases will progressively evaluate more advanced matching strategies.

## MPI Maturity Model

### Level 1: Exact Deterministic Matching

Used in Phase 1A.

Example criteria:

* Exact first name
* Exact last name
* Exact date of birth
* Exact gender
* Exact phone number
* Exact source identifier where available

### Level 2: Rule-Based Matching

Future enhancement.

Examples:

* Same name + same DOB + same ZIP
* Same phone + same DOB
* Same claims member ID + matching name

### Level 3: Fuzzy Matching

Future enhancement.

Examples:

* John vs Jon
* Elizabeth vs Liz
* Address spelling variations
* Typographical differences

### Level 4: Probabilistic Matching

Future enhancement.

Examples:

* Weighted matching rules
* Match scores
* Confidence thresholds
* Human review candidates

### Level 5: Enterprise MPI

Future long-term capability.

Examples:

* Patient merges
* Patient splits
* Name changes
* Shared household phone numbers
* Twins and family members
* Multiple payers
* Multiple labs
* Cross-organization identity resolution

## Phase 1A Matching Strategy

Phase 1A will use simple and explainable deterministic matching.

Initial matching attributes may include:

* First name
* Last name
* Date of birth
* Gender
* Phone number
* Address
* Email
* Source-system identifier
* Claims member ID
* Lab patient ID

The first implementation will prioritize clarity, traceability, and learning over advanced matching complexity.

## Architecture Principle

A matching decision is not absolute patient truth.

FHIRBridge should preserve enough information to understand why a match was made.

Future matching records may include:

* Match rule
* Match reason
* Match confidence
* Match timestamp
* Source records involved
* Enterprise patient identifier

## Rationale

Patient identity is foundational for longitudinal healthcare intelligence.

A realistic interoperability platform must determine when records from multiple systems refer to the same person.

Starting with deterministic matching allows the project to learn identity matching concepts without overwhelming Phase 1 implementation.

Preserving identity attributes and lineage now allows FHIRBridge to evolve toward more advanced MPI capabilities later.

## Consequences

FHIRBridge must preserve patient identity attributes from source systems.

The architecture must support:

* Source identifiers
* Enterprise patient identifiers
* Matching rules
* Matching rationale
* Duplicate patient handling
* Future probabilistic matching

Incorrect matching can create serious downstream issues in longitudinal records, analytics, quality measurement, claims integration, and AI workflows.
