# Business Architecture Knowledge Base

This repository contains all artifacts related to our DVF Business Architecture stored in the turtle (.ttl) format. It serves as the central working space for business architecture management, which includes the management of our logical model (business object / ontology), business rules (SHACL), BON data schemas for our solution as well as the in- and outbound systems and data mappings that power our Business Object Navigator (BON).

## Repository Contents

The repository stores and manages different turtle files for defining our DVF Business Architectures as well as customs scripts needed for the data lineage automation.

### Business Architecture Artifacts

- [Ontologies](./business-architecture-artefacts/ontologies/): foundational ontologies that define the semantics of DVF
- [Business Rules](./business-architecture-artefacts/business-rules/): SHACL constraint shapes created with our SBVR Editor
- [Data Schemas](./business-architecture-artefacts/data-schemas/): BON compliant description of data schemas for DVF as well as in- and outbound systems
- [Data Mappings](./business-architecture-artefacts/data-mappings/): BON compliant data mapping and data request files for building DVFs data lineage
- [Examples](./examples/examples-overview.md): Example *.ttl files for demonstrating the different architecture concepts
  
### Customs scripts

- Data lineage scripts (scripts for creating data lineage .ttl files and merging them into the holistic data mapping file)
- Data schema management scripts (scripts for managing BON compliant data schema creation and BON PO to BO mappings)

## Workflow

We follow a branch based-exploration workflow.

1. Exploration phase
   - Each new exploration (functional epic level) is managed on a separated branch.
   - There are exceptions for the intial setup and migration phase
2. Review and approval
   - When exploration is completed a pull request for merging into main is created
   - The changes are reviewed and the architecture sync meeting and need to be approved latest during our data governance meeting
   - The pull request has to be approved by a member of the DIFA architecture team and a member of the product team
3. Synchronization with Business Object Navigator (BON)
   - Every update on main is published to BON
      - Each *.ttl file will be updated as a named graph
      - Before uploading the updated named graph, we have to delete the old one, otherwise the two named graphs will be merged by BON
      - This repo has therefore also the task of manageing the version control for our BON *.ttl files
   - The updated turtle files are uploaded as an updated named graph using BONs SPARQL endpoint (SPARQL LOAD)

## Contribution Guidelines

- Use branches per exploration topic
  - naming convention "vebs-{VEBS TICKET NUMBER}"-exploration
  - use snake-case
- Ensure that data lineage and data mapping request are mapped correctly
- Ensure that data lineage files are merged correctly before creating a pull request

## Purpose

This repository ensures that DVF remains:

- **Consistent** - Common language within DVF for logical models, linage and rules
- **Traceable** - Link between logical model and data schema as well as data lineage from inbound to DVF to outbound with the corresponding data mapping requests
- **Aligned** - BON compliant models and link to existing ontologies
- **Collaborative** - transparent branching and review workflow
