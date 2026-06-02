# FHIRBridge Unstructured Intelligence Layer

## Purpose

The long-term vision of FHIRBridge is to evolve from a healthcare interoperability platform into a healthcare intelligence platform.

FHIRBridge should eventually support structured and unstructured healthcare data to generate trusted, actionable intelligence for patients, clinicians, providers, payers, researchers, operations teams, and oncology care teams.

## Vision

FHIRBridge will transform fragmented structured and unstructured healthcare data into meaningful, traceable, and trustworthy insights.

Unstructured data may include:

* Clinical notes
* Oncology notes
* Pathology reports
* Radiology reports
* Tumor board notes
* Discharge summaries
* Referral documents
* Patient messages
* Call center transcripts
* Voice transcripts
* Care management notes
* Prior authorization documents

## Architecture Principle

Unstructured data should not replace canonical FHIR.

Instead:

```text
Unstructured data
        ↓
NLP / AI extraction
        ↓
Extracted clinical concepts
        ↓
Canonical FHIR resources
        ↓
Analytics / SQL on FHIR / OMOP / AI applications
```

FHIR remains the trusted interoperability layer for extracted clinical meaning.

## Core Design Principles

### Preserve Original Source

Original notes, documents, reports, and transcripts should be preserved.

### Preserve Extracted Concepts

FHIRBridge should store extracted concepts separately from the original source.

### Preserve Provenance

Every extracted insight should be traceable back to:

* Original document
* Source system
* Extraction method
* Extraction timestamp
* Model or rule version
* Confidence score

### Preserve Human Review Path

For high-risk clinical use cases, AI-extracted concepts should support human review before being treated as trusted clinical facts.

## Future Intelligence Capabilities

### Clinical Notes Intelligence

Extract problems, symptoms, medications, care plans, social factors, and clinical reasoning from notes.

### Oncology Intelligence

Extract:

* Cancer type
* Stage
* Biomarkers
* Treatment response
* Disease progression
* ECOG performance status
* Toxicities
* Treatment intent
* Patient preferences

### Voice Intelligence

Convert voice recordings into transcripts and extract clinical or operational meaning.

### Administrative Intelligence

Support prior authorization, referral processing, documentation burden reduction, and operational workflow optimization.

### Patient Journey Intelligence

Generate longitudinal patient stories across structured and unstructured data.

### Population Health Intelligence

Use extracted concepts to support risk identification, care gaps, quality measurement, and cohort discovery.

## Relationship to FHIR

Extracted concepts may become canonical FHIR resources such as:

* Patient
* Condition
* Observation
* DiagnosticReport
* DocumentReference
* Composition
* MedicationRequest
* MedicationStatement
* Procedure
* CarePlan
* Provenance

FHIRBridge should preserve the original note while also generating structured FHIR representations of extracted concepts.

## Future Roadmap Placement

This capability should not be implemented in Phase 1A.

Recommended placement:

* Phase 1A: Structured Patient, MPI, Provenance, Data Quality, FHIR Patient
* Phase 1B/1C: Encounters, Claims, Synthea, Validation
* Phase 2/3: Terminology, SQL on FHIR, OMOP, Analytics
* Phase 4+: Unstructured Intelligence Layer
* Phase 5+: Oncology Intelligence and AI-assisted workflows

## Success Criteria

FHIRBridge should eventually answer:

* What happened to the patient?
* Why did it happen?
* What changed over time?
* What information is missing?
* What clinical meaning is hidden in notes?
* What insights matter to patients, clinicians, payers, and operations teams?

## Guardrails

FHIRBridge should treat AI-generated insights as traceable interpretations, not automatic truth.

The platform should support:

* Provenance
* Confidence scores
* Human review
* Source traceability
* Model versioning
* Bias and safety review
* Future PHI governance
