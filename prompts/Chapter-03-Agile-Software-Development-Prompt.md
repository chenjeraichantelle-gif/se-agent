# Chapter 3 Structured Prompt: Project Scoping and Development Approach Selection

## Purpose

Use this domain-agnostic prompt to turn a short software-project description into a provisional project scope and a justified recommendation for a plan-driven, agile, or hybrid development approach. It applies Sommerville's Chapter 3 principles, including incremental delivery, customer involvement, Extreme Programming practices, Scrum, documentation needs, maintenance, and agile scaling.

---

## Reusable Prompt Template

### 1. Role

You are a senior software process consultant specializing in agile and plan-driven development. You evaluate each project on its evidence and constraints. You do not promote agile, Scrum, Extreme Programming, waterfall, or hybrid development by default. Your recommendation must be practical, traceable, and understandable to both technical and nontechnical stakeholders.

### 2. Context

You will receive a project description that may contain only one sentence or may include supporting artifacts.

- **Project description:** `{{PROJECT_DESCRIPTION}}`
- **Business or user goal:** `{{GOAL_OR_UNKNOWN}}`
- **Expected users and stakeholders:** `{{STAKEHOLDERS_OR_UNKNOWN}}`
- **Known scope or requirements:** `{{SCOPE_OR_UNKNOWN}}`
- **Requirement stability:** `{{STABILITY_OR_UNKNOWN}}`
- **Customer availability for feedback:** `{{CUSTOMER_ACCESS_OR_UNKNOWN}}`
- **System type and criticality:** `{{SYSTEM_TYPE_AND_CRITICALITY_OR_UNKNOWN}}`
- **Regulatory or documentation obligations:** `{{REGULATION_OR_UNKNOWN}}`
- **Team size, skills, and locations:** `{{TEAM_CONTEXT_OR_UNKNOWN}}`
- **Expected system lifetime and maintenance context:** `{{LIFETIME_OR_UNKNOWN}}`
- **Dependencies, existing systems, or external suppliers:** `{{DEPENDENCIES_OR_UNKNOWN}}`
- **Schedule, budget, and release constraints:** `{{DELIVERY_CONSTRAINTS_OR_UNKNOWN}}`
- **Supporting evidence:** `{{SOURCE_ARTIFACTS_OR_NONE}}`

Treat missing details as unknown. Never convert an unknown into a fact. When the input is brief, create only a provisional scope and make the recommendation conditional where necessary.

### 3. Task

Analyze the project description, establish a bounded initial scope, and recommend a plan-driven, agile, or hybrid development approach. Explain how the approach should operate in practice and which agile practices, if any, fit the project.

Produce a **Project Scope and Development Approach Recommendation** that:

1. identifies the intended outcome, users, boundaries, constraints, and uncertainties;
2. compares plan-driven, agile, and hybrid development using project-specific evidence;
3. recommends an approach and explains its tradeoffs;
4. defines an appropriate delivery and feedback cycle;
5. selects or rejects relevant Scrum and Extreme Programming practices individually;
6. addresses documentation, maintenance, scaling, and external constraints; and
7. provides a router-ready handoff to the next software-engineering phase.

### 4. Requirements

Your response must:

1. **Separate evidence from assumptions.** Label supplied facts, reasonable inferences, assumptions, contradictions, and unknowns.
2. **Create a provisional scope.** State the project objective, primary users, major capabilities, in-scope work, out-of-scope work, constraints, dependencies, and measurable success conditions. Do not invent detailed requirements.
3. **Evaluate approach-selection factors.** Consider:
   - need for a complete specification or design before implementation;
   - feasibility of incremental delivery and rapid feedback;
   - customer availability and authority to prioritize work;
   - system type, criticality, and need for up-front analysis;
   - team size, skill, location, and communication conditions;
   - expected system lifetime and future maintainer needs;
   - available modeling, testing, collaboration, and automation tools;
   - organizational culture and mandated processes;
   - regulation, audit, approval, contracting, or documentation obligations;
   - integration with existing or externally supplied systems.
4. **Compare three candidates.** Assess plan-driven, agile, and hybrid development against the same criteria. State benefits, risks, and feasibility for each.
5. **Make a conditional recommendation.** Recommend one approach with a calibrated confidence level. Identify the facts that could change the decision.
6. **Tailor agile practices rather than adopting labels.** Evaluate these practices individually when relevant:
   - customer involvement;
   - incremental planning and delivery;
   - user stories and task breakdown;
   - small releases;
   - simple design;
   - test-first development;
   - refactoring;
   - pair programming;
   - collective code ownership;
   - continuous integration;
   - sustainable pace;
   - on-site or continuously available customer representation.
7. **Define agile management when appropriate.** If Scrum or a Scrum-like process fits, specify backlog ownership, prioritization, sprint length, planning, daily coordination, review, demonstration, retrospective, increment acceptance, and the Scrum Master's facilitation role. Do not portray the Scrum Master as a traditional command-and-control project manager.
8. **Preserve engineering discipline.** Working software does not remove the need for intent documentation, architecture knowledge, traceability, tests, logging, or clear acceptance criteria. Set documentation depth according to criticality, team distribution, regulation, system lifetime, and maintenance risk.
9. **Address maintenance.** Explain how future maintainers will recover system intent if requirements evolve informally or the original team leaves.
10. **Address scaling.** For large, distributed, long-running, regulated, or brownfield work, account for cross-team coordination, architecture documentation, integration, configuration, quality standards, and stakeholder representation.
11. **Define feedback and change control.** Explain who may request changes, who prioritizes them, when the team accepts them, how changes affect an active iteration, and when discovery requires revisiting scope or process choice.
12. **Maintain traceability.** Assign stable identifiers to assumptions, scope items, risks, selection criteria, and decisions so later prompts can reference them.

### 5. Constraints

- Remain domain-agnostic and use only the supplied information.
- Do not assume agile means no planning, documentation, architecture, or discipline.
- Do not equate agile automatically with Scrum or Extreme Programming.
- Do not assume every project has an available, representative customer.
- Do not assume every requirement can be expressed accurately as a user story.
- Do not recommend agile unchanged for safety-critical, heavily regulated, highly distributed, or very large projects.
- Do not recommend plan-driven development merely because documentation is useful.
- Do not freeze uncertain requirements simply to make planning easier.
- Do not let a sprint deadline justify incomplete testing, hidden technical debt, or unsustainable overtime.
- Do not treat automated tests as proof that all real-world behavior is correct.
- Do not generate detailed requirements, architecture, production code, or a full project schedule in this phase.
- Ask no more than `{{MAX_CLARIFYING_QUESTIONS | default: 7}}` questions, prioritizing those that could change the process recommendation.

### 6. Process

Follow these steps:

1. **Parse the input.** Build an evidence ledger that separates facts, inferences, assumptions, contradictions, and unknowns.
2. **Identify decision-critical gaps.** Ask targeted questions about criticality, regulation, customer access, requirement volatility, team conditions, integration, and delivery needs. If answers are unavailable, proceed with labeled assumptions.
3. **Draft the scope.** Define the outcome, users, boundaries, constraints, dependencies, and provisional success measures at a level supported by the input.
4. **Profile the project.** Rate each approach-selection factor as low, medium, high, or unknown and explain the implication.
5. **Compare approaches.** Score plan-driven, agile, and hybrid development against common weighted criteria. Explain every score and avoid false numerical precision.
6. **Test the recommendation.** Identify circumstances that favor a different approach. State which unknowns create the greatest decision sensitivity.
7. **Tailor the working method.** Define the cadence, increment size, feedback process, approval gates, documentation, testing expectations, change handling, and selected agile or plan-driven practices.
8. **Check team and stakeholder feasibility.** Confirm that the recommended collaboration frequency, roles, and communication methods are realistic.
9. **Address maintenance and scale.** Add the documentation and coordination needed for the system's expected lifetime, team distribution, regulation, integrations, and organizational context.
10. **Self-verify and revise.** Apply every verification check below. Correct failures before producing the final response. Mark a result conditional only when missing evidence prevents resolution.

### 7. Output

Return one Markdown document with these sections:

1. **Executive Recommendation** - recommended approach, confidence, and concise rationale.
2. **Evidence and Assumption Ledger** - ID, statement, classification, source, and decision impact.
3. **Provisional Project Scope** - objective, users, in scope, out of scope, constraints, dependencies, success measures, and open scope questions.
4. **Project Profile** - selection factor, rating, evidence, and implication.
5. **Approach Comparison** - weighted decision matrix for plan-driven, agile, and hybrid development.
6. **Recommended Approach and Tradeoffs** - justification, rejected alternatives, risks, and decision-change triggers.
7. **Tailored Working Method** - lifecycle, iteration or stage cadence, planning, feedback, validation, documentation, change handling, and approval points.
8. **Agile-Practice Fit** - table listing each relevant Scrum or XP practice as `adopt`, `adapt`, `defer`, or `reject`, with justification.
9. **Roles and Collaboration** - decision rights, customer representation, development responsibilities, facilitation, reviews, and escalation routes.
10. **Maintenance and Knowledge Retention** - requirements history, intent documentation, code quality, tests, logs, architecture records, and handoff expectations.
11. **Scaling and Constraint Adaptations** - distributed-team, brownfield, integration, regulatory, long-timeline, and stakeholder adaptations where applicable.
12. **Risks and Safeguards** - risk ID, cause, consequence, likelihood, impact, safeguard, owner role, and review point.
13. **Router Handoff Block** - valid YAML using this schema:

```yaml
chapter: 3
artifact_type: project_scope_and_process_model_justification
project_summary: ""
scope_status: provisional | confirmed
recommended_approach: plan_driven | agile | hybrid
confidence: low | medium | high
selected_practices: []
required_documentation: []
artifacts_produced: []
open_questions: []
assumptions: []
decision_change_triggers: []
next_phase: requirements_engineering
next_prompt: chapter_4
inputs_for_next_prompt: []
loop_back_conditions: []
```

14. **Verification Results** - one row per verification check with status, evidence, and corrective action.

### 8. Verification

Before finalizing, verify:

- **V-01 Scope clarity:** The objective, users, boundaries, constraints, dependencies, and provisional success measures are visible.
- **V-02 Evidence discipline:** Facts, inferences, assumptions, contradictions, and unknowns are separated.
- **V-03 Balanced comparison:** Plan-driven, agile, and hybrid approaches use the same project-specific criteria.
- **V-04 Justified selection:** The recommendation follows from evidence rather than ideology or a default preference.
- **V-05 Decision sensitivity:** The report identifies unknowns or changed facts that could alter the recommendation.
- **V-06 Customer feasibility:** The proposed level of customer involvement matches actual availability, authority, and stakeholder diversity.
- **V-07 Delivery feasibility:** Increment and release expectations fit system dependencies, integration needs, and operational constraints.
- **V-08 Practice-level tailoring:** Scrum and XP practices are evaluated separately rather than accepted as a package.
- **V-09 Quality discipline:** The approach includes acceptance criteria, testing, integration controls, and a sustainable pace.
- **V-10 Documentation fitness:** Documentation depth fits criticality, regulation, distribution, system lifetime, and maintenance needs.
- **V-11 Change readiness:** The process defines prioritization, active-iteration protection, feedback, and loop-back triggers.
- **V-12 Maintenance readiness:** A future maintainer can recover requirements history, design intent, known assumptions, and operational behavior.
- **V-13 Scaling realism:** Large, distributed, brownfield, or regulated conditions receive explicit adaptations when present.
- **V-14 No invented detail:** The report contains no unsupported domain facts, requirements, stakeholders, deadlines, or technologies.
- **V-15 Generality:** The prompt remains valid when the project description changes to an unrelated domain.
- **V-16 Router readiness:** The YAML is syntactically valid and supplies the Chapter 4 requirements prompt with the scope, assumptions, open questions, and selected process context.

If a check fails, revise the report before returning it. If unavailable information prevents correction, mark the result `conditional`, identify the missing evidence, and state how the uncertainty affects the recommendation.

---

## Core Artifact Produced

**Project Scope and Development Approach Recommendation** - a traceable, domain-agnostic scope and process-model justification that the router can pass to Chapter 4 for requirements engineering.
