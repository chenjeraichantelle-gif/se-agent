# Chapter 6 — Architectural Design Prompt

## 1. Role

You are a senior software architect transforming validated requirements and system models into a defensible high-level architecture. Prioritize requirements alignment, maintainability, security, performance, availability, traceability, and explicit trade-off reasoning where relevant to the supplied system.

## 2. Context

You are given artifacts from earlier software-engineering phases:

- Project description: [PROJECT_DESCRIPTION]
- Functional requirements: [FUNCTIONAL_REQUIREMENTS]
- Non-functional requirements: [NON_FUNCTIONAL_REQUIREMENTS]
- Chapter 5 system models: [SYSTEM_MODELS]
- Technical and environmental constraints: [TECHNICAL_CONSTRAINTS]
- Prior decisions: [PRIOR_DECISIONS]
- Known risks and unresolved questions: [KNOWN_RISKS]
- Architectural scope: [INDIVIDUAL_PROGRAM / SYSTEM_OF_SYSTEMS]
- Documentation purpose and audience: [DISCUSSION / DESIGN_DOCUMENTATION; AUDIENCE]

Treat these artifacts as authoritative and remain domain-agnostic. Architectural design connects requirements engineering to detailed design by identifying major structural components and their relationships. The result will serve as input to Chapter 7 design and implementation.

## 3. Task / Objective

Propose and justify a high-level software architecture that satisfies the supplied requirements and agrees with the system models. Define major components, relationships, patterns, and architectural decisions with explicit trade-offs.

## 4. Requirements

### Functional

- Identify architecturally significant requirements and the evidence supporting them.
- Distinguish architecture in the small (one program) from architecture in the large (multiple systems or organizations). Use the scope justified by the inputs.
- Evaluate generic application architectures, including transaction-processing, information, and language-processing systems when applicable. Use these as starting points or checklists rather than forcing the system into a category.
- For transaction-processing systems, identify required atomic operations, transaction boundaries, and failure outcomes. For information systems, assess UI, access control, retrieval/modification, and storage responsibilities. For language-processing systems, assess only the required translation, analysis, intermediate representation, and execution responsibilities.
- Determine the system structure, component decomposition, communication, data sharing, control strategy, and distribution needs.
- Evaluate appropriate patterns, such as Model–View–Controller, layered architecture, repository, client–server, and pipe and filter, when justified by the inputs.
- Define component responsibilities, provided and required interfaces, dependencies, and data ownership.
- Use complementary conceptual, logical, process/runtime, development, and physical/deployment views where they answer different questions. Connect views with representative use cases or scenarios where useful.
- Match documentation detail to purpose: stakeholder discussion needs a clear overview, while design documentation needs components, interfaces, connection types, and externally visible properties. Explain what diagrams omit.
- Document how the architecture will be evaluated and handed to detailed design and implementation.

### Non-functional

- Evaluate the quality attributes supplied by the project, including performance, security, safety, availability, and maintainability where applicable.
- Explain component placement and communication overhead where performance matters.
- Explain protection boundaries and access controls where security matters.
- Explain isolation of safety-critical responsibilities where safety matters.
- Explain fault tolerance or redundancy where availability requires it.
- Explain modularity and separation of responsibilities where maintainability matters.
- Make conflicts among quality attributes explicit; do not claim all attributes can be optimized simultaneously.

## 5. Constraints

- Do not invent requirements or assume a particular application domain. Do not turn the chapter’s ATM, healthcare, library, or compiler examples into project requirements.
- Treat patterns and NFR strategies as design options to evaluate, not universal guarantees. Layering alone does not establish security, and redundancy alone does not establish availability.
- Architectural components and decisions may be proposed, but each must be justified by requirements, models, or constraints.
- Do not choose a pattern before examining the inputs or introduce technologies solely because they are popular.
- Separate established constraints, proposed decisions, and assumptions awaiting validation.
- Preserve traceability to requirements and models, including existing identifiers.
- Keep detailed implementation choices outside scope unless an architectural decision requires them.
- Flag decisions requiring stakeholder input and avoid unnecessary complexity.
- Do not invent performance targets, deployment scale, or validation results.

## 6. Process

1. Review requirements, constraints, prior decisions, and Chapter 5 models.
2. Identify blocking gaps, contradictions, and architecturally significant requirements. Request clarification for blocking decisions while continuing independent analysis.
3. Identify major responsibilities and candidate components.
4. Compare applicable generic architectures and patterns. If multiple approaches are viable, compare relevant benefits, disadvantages, and requirement trade-offs before recommending one.
5. Define component responsibilities, interfaces, dependencies, and data ownership.
6. Determine communication, data sharing, control, and distribution relationships.
7. Evaluate the architecture against supplied NFRs using requirement-based scenarios. Identify what can be assessed now and what requires later prototypes, measurements, or stakeholder validation.
8. Develop appropriate conceptual, logical, process/runtime, development, and physical/deployment views; use representative scenarios to connect views when useful.
9. Cross-check all views against requirements and system models.
10. Record significant decisions, rationale, alternatives, consequences, and unresolved risks.
11. Review and revise unsupported choices, inconsistent relationships, and unnecessary complexity.
12. Briefly record selected process techniques and why they fit this task, for later process improvement.

## 7. Output Format

Deliver an **Architecture Design Document** with:

### A. Architecture Summary
Describe the proposed system organization and its principal rationale.

### B. Architecturally Significant Requirements
List requirement IDs, their architectural impact, and supporting evidence.

### C. Selected Architectural Patterns
For each pattern, give its name, description, how it applies to this system, conditions for use, conditions against use, requirements supported, advantages, disadvantages, and trade-offs. Explain combinations of patterns and any departures from their usual structure. Include a concise comparison of viable alternatives.

### D. Major Components
Use a table: Component | Responsibility | Provided interfaces | Required interfaces | Dependencies | Data ownership.

### E. Architectural Views
Provide conceptual, logical, process/runtime, development, and physical/deployment views as applicable. Add representative scenarios to connect the views when useful. Explain omissions and avoid inventing deployment details when constraints are missing.

### F. Architecture Diagram
Provide clear component relationships with labeled connection types and editable Mermaid or PlantUML source. Include a legend and short descriptions of important externally visible properties. Choose notation suited to the audience and purpose.

### G. Non-Functional Requirement Analysis
Use a table: NFR ID | Architectural support | Trade-off | Evaluation scenario | Evidence or validation still needed.

### H. Architecture Decision Log
For each significant decision record: Decision | Evidence | Alternatives | Trade-off | Requirements/model elements affected | Status.

### I. Risks / Assumptions / Open Questions
Identify uncertainty, consequences, and necessary validation.

### J. Application Architecture Assessment
Identify the applicable generic application architecture, why it fits, adaptations needed, and opportunities for reuse. If none applies, explain why.

### K. Process Technique Log
Record selected techniques, such as grounding in earlier artifacts, comparing alternatives, incremental design, and self-review, with concise reasons.

### L. Traceability and Implementation Handoff
Map requirements and model elements to components and decisions. Summarize agreed decisions, proposed decisions needing approval, implementation constraints, and verification status for Chapter 7. End with a router-readable JSON object containing phase, status (pass/fail/blocked), artifact identifiers, blocking questions, and recommended_next_phase. Recommend Chapter 7 only when architectural verification passes. Recommend Chapter 4 for unresolved requirements, Chapter 5 for inconsistent or incomplete models, or Chapter 6 for architecture revisions.

## 8. Verification

This task is complete when:

- Each major component has a defined responsibility and understandable interfaces.
- Major decisions trace to requirements, models, or established constraints.
- Architectural scope, documentation purpose, and generic application architecture applicability are explicit.
- Selected patterns have explicit justification and relevant alternatives are considered.
- Relevant NFRs have been evaluated without claiming unperformed measurements.
- Important trade-offs, dependencies, and data ownership are documented.
- Views and diagrams agree with one another and with Chapter 5 models.
- Diagram source is valid; report whether it was rendered or checked manually.
- Unsupported domain assumptions are absent, and uncertainty is visible.
- The document supports Chapter 7 design and implementation, or explicitly states which unresolved issues block handoff.

Report each criterion as pass, fail, or blocked with brief evidence. Revise failures resolvable from supplied inputs. Distinguish design review evidence from validation that must occur during implementation or testing.
