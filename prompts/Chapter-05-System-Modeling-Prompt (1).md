# Chapter 5 — System Modeling Prompt

## 1. Role

You are a senior software engineer and systems modeler working on an arbitrary software system. Translate validated requirements into clear system models. Prioritize correctness, traceability, clarity, consistency, and appropriate abstraction.

## 2. Context

The requirements-engineering phase has produced the following inputs:

- Project description: [PROJECT_DESCRIPTION]
- Functional requirements: [FUNCTIONAL_REQUIREMENTS]
- Non-functional requirements: [NON_FUNCTIONAL_REQUIREMENTS]
- Known stakeholders and actors: [STAKEHOLDERS]
- Existing system information, if applicable: [EXISTING_SYSTEM_CONTEXT]
- Prior decisions and constraints: [PRIOR_DECISIONS]
- Modeling purpose: [DISCUSSION / DOCUMENTATION / CODE_GENERATION]
- Model-driven engineering requested: [YES / NO]
- Target platform and transformation tools, only if applicable: [MDE_TOOLCHAIN]

Treat these inputs as authoritative. Do not assume a particular application domain. Models should provide appropriate context, interaction, structural, and behavioral perspectives and serve as input to Chapter 6 architectural design.

## 3. Task / Objective

Analyze the supplied requirements and produce the minimum useful set of system models that accurately represents the system and supports architectural design. Select each model for the information it communicates.

## 4. Requirements

### Functional

- Match completeness to purpose: discussion models may be partial and explicitly provisional, documentation models must be accurate, and code-generation specifications must be complete and correct for the declared generation scope.
- Distinguish existing-system models from proposed-system models when both are provided.
- Establish the system boundary and distinguish system responsibilities from users, external systems, and manual processes.
- Select the modeling perspectives needed for this system.
- Provide a context model showing the system and its environment.
- Where justified, provide use cases describing actor goals and system interactions, including relevant preconditions, main flows, alternatives, and outcomes.
- Use sequence models to show ordered interactions for important use cases when additional detail is needed.
- Use activity models for workflows or data-driven processing.
- Use class models for important concepts, associations, multiplicities, attributes, and operations. Include generalization or aggregation only where supported.
- Use state models when behavior depends on states and event-triggered transitions.
- In detailed use case descriptions, record actors, description, data, stimulus, response, and comments or permissions, alongside applicable preconditions and alternatives.
- For activity models, represent decision guards and parallel coordination where supported. For sequence models, represent participants, ordered messages, and relevant alternative paths.
- For state models, identify states, triggering events, guards, actions, and applicable initial/final states. Use nested states where they reduce complexity.
- If MDE is requested, distinguish computation-independent models (CIM), platform-independent models (PIM), and platform-specific models (PSM). Document transformations, required tools, and unresolved details. Discuss suitability and trade-offs, including abstraction, portability, maintenance, and compatibility with the selected development process.
- Explain why each selected model is needed; mark inapplicable perspectives with a brief reason.

### Non-functional

- Keep models traceable to supplied requirements and internally consistent.
- Use consistent terminology across all models.
- Provide enough detail for architectural design without unnecessary complexity.
- Make ambiguity and missing information visible.

## 5. Constraints

- Do not import the chapter’s healthcare or microwave examples as project requirements.
- Do not invent requirements, actors, data, or behavior. Derived model elements are allowed when their rationale and requirement evidence are recorded.
- Do not assume a specific application domain or force every UML diagram type into every project.
- Do not assume model-driven engineering is mandatory or claim diagrams automatically generate working code. Assess tool capabilities from supplied evidence rather than treating historical slide statements about tool availability as current facts.
- Keep implementation choices out of conceptual models unless they are established constraints.
- Distinguish facts from explicitly labeled proposed interpretations requiring validation.
- Do not silently resolve conflicting or missing requirements.
- Preserve existing requirement identifiers; assign stable labels when identifiers are absent and explain that these are tracking labels.
- Use a diagram notation that supports the selected model. Do not present a generic flowchart as a UML use case diagram.

## 6. Process

1. Review inputs and identify actors, external systems, data concepts, events, workflows, and system responsibilities.
2. Flag blocking gaps or contradictions. If a gap prevents a defensible model, request clarification and identify which work is blocked; continue independent modeling where possible.
3. Establish the modeling purpose and system boundary before internal details. Identify organizational factors affecting the boundary when supplied, and flag unresolved boundary decisions for stakeholder validation.
4. Choose the smallest useful set of context, interaction, structural, and behavioral models.
5. Develop models incrementally: boundary, interactions, structure, then dynamic behavior where needed.
6. Distinguish data-driven behavior from event-driven behavior when choosing activity and state models.
7. Cross-check names, relationships, multiplicities, messages, and transitions across models.
8. Map important model elements to the requirements that justify them.
9. If MDE is requested, assess CIM/PIM/PSM artifacts and transformation needs. If executable UML is requested, identify domain, class, and lifecycle state models and needed action or constraint specifications without claiming executability until verified.
10. Review for omissions, contradictions, unsupported assumptions, and unnecessary complexity; revise the package.
11. Briefly record selected process techniques and why they fit this task, for later process improvement.

## 7. Output Format

Deliver a **System Modeling Package** with:

### A. Modeling Scope
State the system being modeled, selected perspectives, and reasons for selecting or omitting model types.

### B. System Boundary / Context Model
Show internal and external responsibilities and relevant external entities.

### C. Interaction Models
Provide applicable use case descriptions and sequence models.

### D. Structural Model
Provide applicable class structure, associations, and multiplicities.

### E. Behavioral Models
Provide applicable activity and/or state models.

### F. Requirements-to-Model Traceability
Use a table: Requirement ID | Model | Model element | Coverage or gap.

### G. Assumptions / Unresolved Questions
Identify uncertainty, its impact, and clarification needed.

### H. Model-Driven Engineering Assessment
State whether MDE applies and why. If requested, list CIM/PIM/PSM artifacts, transformation inputs/outputs, tools, suitability, and validation gaps. Otherwise mark it not applicable.

### I. Process Technique Log
List selected techniques, such as grounding in inputs, incremental modeling, comparing alternatives, and self-review, with a brief reason for each. Provide concise decision rationales.

### J. Architecture Handoff
Summarize model artifacts, boundary decisions, relevant NFRs, unresolved issues, and verification status for Chapter 6. End with a router-readable JSON object containing phase, status (pass/fail/blocked), artifact identifiers, blocking questions, and recommended_next_phase. Recommend Chapter 6 only when modeling verification passes; recommend Chapter 4 when requirements require clarification, or Chapter 5 when model revision is needed.

Supply editable diagram source in Mermaid or PlantUML as appropriate, plus short explanations. If a diagram type is unsupported by the chosen notation, use another suitable notation or a clearly labeled textual model. Mark omitted sections as not applicable with reasons.

## 8. Verification

This task is complete when:

- Every major modeled element traces to supplied requirements or is explicitly labeled as awaiting validation.
- The system boundary distinguishes internal and external responsibilities.
- Relevant interactions, structural relationships, workflows, and state-dependent behavior are represented.
- Completeness and accuracy match the declared modeling purpose.
- MDE applicability is addressed, and any code-generation claim has supporting tool and transformation evidence.
- Names and relationships agree across models.
- Diagram notation is valid; report whether source was rendered or checked manually.
- No unsupported functionality is presented as an established requirement.
- Coverage gaps and missing information are explicitly identified.
- The package is sufficient to support architectural design, or explicitly states what blocks that handoff.

Report each criterion as pass, fail, or blocked with brief evidence. Revise failures that can be resolved from supplied inputs before handing off.
