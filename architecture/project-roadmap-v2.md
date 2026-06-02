# FHIRBridge Roadmap V2

## Phase 1A - Patient, MPI & Provenance Foundation

Primary FHIR Resource:
- Patient

Architecture Focus:
- Multi-source patient data
- 5+ fictional health systems
- Epic-heavy source strategy
- Clean datasets
- Messy datasets
- Master Patient Index (MPI)
- Provenance tracking
- Data quality framework
- Canonical Patient generation
- Raw source data preservation
- Source-to-target transformation tracking
- Source system lineage

Supporting Real-World Source Context Captured as Attributes:
- Source organization name
- Source facility name
- Source provider name
- Source location information
- Source system identifier

Implementation Note:
These elements often exist as messy source-system data in real healthcare environments. In Phase 1A, they will be captured as source attributes to preserve context without overloading the first implementation step.

Future Promotion to Formal FHIR Resources:
- Organization
- Practitioner
- Location

## Phase 1B - Encounter and Claims Foundation

- Encounter mapping
- Claims ingestion
- Longitudinal patient timeline foundation
- Initial organization/provider/facility relationships

Claims Evolution Strategy:

- Phase 1B: Single claims source
- Phase 2: Add second claims source
- Phase 3: Expand toward a multi-payer ecosystem

## Phase 1C - Native FHIR Ingestion

- Synthea FHIR bundles
- Native FHIR ingestion
- FHIR validation
- Resource relationship exploration

## Phase 1D - Longitudinal Patient Assembly

- Unified patient record
- Multi-source patient history
- Cross-system patient timeline

## Future Expansion Areas

### FHIR R5 Learning Track
- Compare selected R4 and R5 resources
- Evaluate mature R5 capabilities where useful
- Maintain separate R5 examples from the primary R4 implementation
- Document version differences and migration considerations

### OMOP Integration
- OMOP fundamentals
- OMOP-to-FHIR mapping
- Analytics model exploration

### Oncology Module
- Oncology-specific datasets
- Cancer care workflows
- Oncology FHIR resources

### Quality Measurement Module
- Quality measures
- Care gap analytics
- Population health concepts

### Cloud & Deployment
- PostgreSQL
- HAPI FHIR
- Cloud deployment
- Scalable architecture

### AI-Assisted Workflows
- Clinical intelligence
- Analytics support
- Future AI integration

### Data Governance & Lineage
- End-to-end data lineage
- Transformation traceability
- Provenance management
- Auditability
- Source-to-target mapping governance
## Architecture Review Checkpoints

### Phase 3 Source Mix Review

Reassess source system proportions as the platform matures.

Target future state:

- 60% Clinical EHR
- 25% Claims
- 10% FHIR-native
- 5% Other

Rationale:

Claims data becomes increasingly important for population health, quality measurement, analytics, and financial use cases.

### Claims Source Complexity Review

FHIRBridge will start with a single claims feed and progressively evolve toward multiple payer sources.

This allows the project to learn claims ingestion first, then expand into:

- Cross-payer variation
- Duplicate claims
- Coverage differences
- Cost analytics
- Quality measurement
- Population health use cases

FHIR Version Strategy:
- Use FHIR R4 as the primary implementation baseline
- Generate Phase 1A canonical Patient resources using FHIR R4
- Keep FHIR R5 as a future learning and comparison track
- Avoid mixing R4 and R5 resources in the same canonical store