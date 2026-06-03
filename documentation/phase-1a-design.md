# Status

Approved

# Version

1.0

# Official Reference

This document is the authoritative design specification for FHIRBridge Phase 1A.

If implementation notes, conversations, or older planning documents conflict with this document, this document takes precedence.

# FHIRBridge Phase 1A Design

## Purpose

Phase 1A establishes the foundational interoperability capabilities of FHIRBridge.

The focus is learning and implementing core healthcare interoperability concepts while building reusable platform capabilities.

Phase 1A intentionally prioritizes simplicity, traceability, and architectural correctness over scale and advanced features.

---

# Phase 1A Objectives

Build an end-to-end pipeline that demonstrates:

* Source data ingestion
* Canonical modeling
* Master Patient Index (MPI)
* Provenance capture
* Data quality evaluation
* FHIR R4 Patient generation
* FHIR validation

---

# Phase 1A Architecture

```text
Epic CSV
          \
           \
            → CanonicalPatient
           /
          /
Cerner CSV

                    ↓

              MPI Resolution

                    ↓

             CanonicalPatient

                    ↓

             FHIR R4 Patient

                    ↓

               Validation

                    ↓

         Provenance + Quality
```

FHIR-native flow:

```text
Synthea FHIR Patient

            ↓

      CanonicalPatient

            ↓

      FHIR R4 Patient

            ↓

         Validation
```

---

# Phase 1A Source Systems

## Epic-like Source

Format:

* CSV

Records:

* 18 patient records

Purpose:

* Simulate Epic-style source data

---

## Cerner-like Source

Format:

* CSV

Records:

* 18 patient records

Purpose:

* Simulate Cerner-style source data

---

## Synthea Source

Format:

* FHIR R4 Bundle

Records:

* 10 Patient resources

Purpose:

* FHIR-native source ingestion
* FHIR normalization
* FHIR interoperability learning

Synthea resources will not participate in MPI matching during Phase 1A.

---

# Dataset Design

## Epic + Cerner

Total source records:

* 36

Composition:

* 18 Epic records
* 18 Cerner records

Overlap:

* 8 patients appear in both systems

Expected output:

* 20 CanonicalPatients

---

## Synthea

Input:

* 10 FHIR Patient resources

Expected output:

* 10 CanonicalPatients

---

## Total Expected Output

* 30 CanonicalPatients
* 30 FHIR R4 Patient resources

---

# MPI Strategy

## Phase 1A Scope

MPI applies only to:

* Epic-like source
* Cerner-like source

Synthea is excluded from MPI matching.

---

## Matching Method

Deterministic matching:

* First Name
* Last Name
* Birth Date

Future phases may introduce:

* Fuzzy matching
* Probabilistic matching
* Address matching
* Phone matching
* Enterprise MPI

---

# MPI Test Scenarios

The 8 overlapping patients intentionally test:

1. Exact match
2. Nickname variation
3. Shortened name
4. Middle initial difference
5. Phone format difference
6. Address format difference
7. Missing value
8. Gender normalization

---

# CanonicalPatient Strategy

CanonicalPatient is an internal platform model.

CanonicalPatient is not a FHIR Patient resource.

Transformation:

```text
Source Data
      ↓
CanonicalPatient
      ↓
FHIR Patient
```

---

# CanonicalPatient Fields

## Identity

* canonical_patient_id

## Source Identifiers

* source_system
* source_identifier_type
* source_identifier_value

## Demographics

* first_name
* middle_name
* last_name
* birth_date
* gender

## Future Demographics

Stored but not actively processed:

* race
* ethnicity
* preferred_language

## Contact

* phone
* email

## Address

* address_line_1
* city
* state
* zip

## Lightweight Care Context

* source_organization_id
* source_organization_name
* source_practitioner_id
* source_practitioner_name
* source_location_id
* source_location_name

## Provenance

* provenance_ids
* source_record_ids

## Data Quality

* data_quality_flags
* data_quality_score

---

# Provenance Scope

Phase 1A provenance captures:

* Source system
* Source record ID
* Load timestamp
* Transformation timestamp
* FHIR generation timestamp

---

# Data Quality Scope

Phase 1A evaluates:

* Required fields present
* Valid birth date
* Valid gender
* Valid identifier
* Duplicate detection

Examples of flags:

* missing_phone
* missing_email
* gender_normalized
* address_normalized

---

# FHIR Scope

Phase 1A generates:

* FHIR R4 Patient resources

Only.

Future resources:

* Encounter
* Observation
* Condition
* Procedure
* Medication
* Claim

---

# Out of Scope

Phase 1A does not include:

* HL7 v2
* CCDA
* Claims
* OMOP implementation
* SMART Applications
* AI services
* Clinical notes
* Voice processing
* Cloud deployment
* Multi-source MPI
* Probabilistic MPI

---

# Success Criteria

FHIRBridge successfully:

1. Ingests Epic CSV data
2. Ingests Cerner CSV data
3. Ingests Synthea FHIR data
4. Creates CanonicalPatient records
5. Resolves MPI matches between Epic and Cerner
6. Generates valid FHIR R4 Patient resources
7. Produces provenance records
8. Produces data quality reports
9. Validates generated FHIR resources

Phase 1A is complete when all objectives are demonstrated end-to-end.

