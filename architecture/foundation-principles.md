# FHIRBridge Foundation Principles

## Foundation #1: Standards Exist Because They Solve Different Problems

Healthcare standards should not be evaluated by asking:

"Which standard is best?"

Instead, architects should ask:

"What problem am I solving?"

Different healthcare interoperability standards exist because they were created to solve different business and workflow problems.

## Architect Rule

Never ask:

"Which standard is best?"

Always ask:

"What problem am I solving?"

Then determine which standard best fits that problem.

## Standards Overview

| Standard | Primary Purpose | Typical Use Case |
|-----------|-----------------|------------------|
| HL7 v2 | Real-time event messaging | ADT, Orders, Results |
| CCDA | Clinical document exchange | Referrals, discharge summaries, continuity of care |
| FHIR | API-based granular access | Apps, portals, analytics APIs, SMART on FHIR |

## FHIRBridge Architect Mantra

HL7 v2 moves events.

CCDA moves clinical stories.

FHIR exposes data as services.

Architects choose based on the problem, not the popularity of the standard.

## FHIRBridge Mental Model

Hospital Operations
        ↓
HL7 v2
        ↓
FHIRBridge
        ↓
FHIR Canonical Model
        ↓
Analytics / OMOP / AI

Clinical Summaries
        ↓
CCDA
        ↓
FHIRBridge
        ↓
FHIR Canonical Model

Modern Applications
        ↓
FHIR APIs
        ↓
FHIRBridge
        ↓
FHIR Canonical Model

## Canonical Architecture Principle

FHIRBridge uses FHIR as the canonical interoperability model.

This does not mean every source system must be FHIR-native.

FHIRBridge should support multiple input patterns:

- HL7 v2-style operational feeds
- CCDA-style document summaries
- FHIR API data
- Legacy CSV extracts
- Claims data
- Future OMOP datasets
- Future Synthea FHIR bundles

These source formats can converge into a canonical FHIR model for downstream analytics, longitudinal patient records, AI-assisted workflows, and future applications.