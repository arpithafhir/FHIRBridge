# FHIRBridge Repository Structure

## Purpose

This document defines the intended responsibility of each top-level repository folder.

FHIRBridge is designed as an extensible healthcare interoperability, intelligence, and application platform. Repository organization should support current implementation needs while allowing future growth without major restructuring.

---

# Architecture

architecture/

Contains:

* Architecture diagrams
* Architecture Decision Records (ADRs)
* System overview
* Foundation principles
* Platform vision
* Long-term architecture documentation

---

# Roadmap

roadmap/

Contains:

* Implementation roadmap
* Phase planning
* Milestones
* Future backlog items
* Architecture checkpoints

---

# Synthetic Data

synthetic-data/

Contains source data used for development and testing.

Phase 1A sources include:

* Epic-like CSV
* Cerner-like CSV
* Synthea FHIR R4 bundle

Future sources may include

* HL7 v2 messages
* CCDA documents
* Claims data
* Laboratory data
* Oncology data
* Additional synthetic health systems

---

# Mapping Engine

mapping-engine/

Contains:

* Source-to-canonical mappings
* Canonical transformations
* FHIR mapping logic
* Transformation rules
* Data normalization logic

---

# MPI

mpi/

Contains:

* Master Patient Index logic
* Patient matching rules
* Duplicate detection
* Identity resolution workflows

---

# Data Quality

data-quality/

Contains:

* Data quality rules
* Quality reports
* Completeness checks
* Consistency checks
* Data quality metrics

---

# FHIR Resources

fhir-resources/

Contains:

* Generated FHIR resources
* FHIR bundles
* Canonical FHIR outputs

Phase 1A focuses on:

* FHIR R4 Patient resources

Future phases may include:

* Encounter
* Observation
* Condition
* Medication
* Claim
* Additional resources

---

# Validation

validation/

Contains:

* FHIR validation outputs
* Conformance testing results
* Validation reports
* Quality validation artifacts

---

# Debugging Journal

debugging-journal/

Contains:

* Debugging notes
* Root cause analysis
* Problem resolution history
* Technical troubleshooting documentation

---

# Lessons Learned

lessons-learned/

Contains:

* Engineering lessons
* Architecture lessons
* Retrospectives
* Future improvement opportunities

---

# Documentation

documentation/

Contains:

* Repository documentation
* Implementation guides
* Process documentation
* Project reference materials

---

# Future Modules

## AI Services

ai-services/

Future home for:

* NLP
* Clinical note processing
* Voice processing
* LLM workflows
* Unstructured intelligence

---

## Frontend App

frontend-app/

Future home for:

* SMART on FHIR applications
* User interfaces
* Patient experiences
* Clinician experiences

---

## Financial Module

financial-module/

Future home for:

* Claims analytics
* Financial analytics
* Cost intelligence

---

## Oncology Module

oncology-module/

Future home for:

* Oncology-specific models
* Oncology intelligence
* Cancer care analytics

---

## Quality Engine

quality-engine/

Future home for:

* eCQMs
* Quality measurement
* Population health analytics
* Quality reporting

---

# Repository Evolution Principles

FHIRBridge should evolve through reusable platform capabilities rather than isolated point solutions.

The repository should support future:

* Source systems
* Pipelines
* Interfaces
* Databases
* Cloud architectures
* Data flows
* Terminology sources
* Analytics products
* AI capabilities
* Healthcare domains

without requiring major repository redesign.

---

# Phase 1A Scope

Phase 1A focuses on:

* Epic-like CSV source data
* Cerner-like CSV source data
* Synthea FHIR R4 Bundles
* Canonical Patient models
* MPI
* Provenance
* Data Quality
* FHIR R4 Patient generation
* Validation

Phase 1A intentionally excludes:

* HL7 v2
* CCDA
* Claims
* SMART Applications
* AI Services
* OMOP implementation
* Cloud deployment
* Unstructured intelligence processing

These capabilities are introduced in future phases according to the project roadmap.
