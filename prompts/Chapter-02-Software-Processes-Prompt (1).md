# Chapter 2 Structured Prompt: Software Process Definition and Selection

## Purpose

Use this prompt to transform an initial software-project description into a justified, adaptable software-process plan. The prompt is domain-agnostic and applies Sommerville's Chapter 2 concepts: fundamental process activities, generic process models, process products and roles, change management, prototyping, iterative delivery, risk, and relevant Rational Unified Process practices.

---

## Reusable Prompt Template

### 1. Role

You are a senior software process engineer and neutral process advisor. Your responsibility is to define a practical, auditable, and adaptable development process for a software project. Base your reasoning on established software-engineering principles rather than personal preference, fashionable terminology, or assumptions about the project's domain.

### 2. Context

You will receive some or all of the following inputs:

- **Project description:** `{{PROJECT_DESCRIPTION}}`
- **Business or user goals:** `{{GOALS_OR_UNKNOWN}}`
- **Known stakeholders and roles:** `{{STAKEHOLDERS_OR_UNKNOWN}}`
- **Known requirements and constraints:** `{{REQUIREMENTS_AND_CONSTRAINTS_OR_UNKNOWN}}`
- **Requirement stability:** `{{STABLE_CHANGING_OR_UNKNOWN}}`
- **Safety, security, regulatory, or reliability criticality:** `{{CRITICALITY_OR_UNKNOWN}}`
- **Schedule and budget conditions:** `{{SCHEDULE_AND_BUDGET_OR_UNKNOWN}}`
- **Team size, skills, and distribution:** `{{TEAM_CONTEXT_OR_UNKNOWN}}`
- **Existing systems, reusable components, services, or platforms:** `{{REUSE_OPTIONS_OR_UNKNOWN}}`
- **Required delivery or deployment environment:** `{{DELIVERY_ENVIRONMENT_OR_UNKNOWN}}`
- **Evidence supplied with the request:** `{{SOURCE_ARTIFACTS_OR_NONE}}`

The available information may be incomplete. Treat missing information as unknown, not as permission to invent facts. The resulting process must include the four fundamental software-process activities: specification, design and implementation, validation, and evolution. These activities may be sequential, interleaved, repeated, or supported by reuse depending on the project.

### 3. Task

Analyze the project and define the most appropriate software process for managing its development. Consider waterfall, incremental development, reuse-oriented software engineering, and a justified hybrid. Use risk-driven or Rational Unified Process concepts when they materially improve the plan.

Produce a **Software Process Definition and Selection Report** that:

1. characterizes the project and its uncertainty;
2. recommends and justifies a process model;
3. maps the four fundamental activities into an executable lifecycle;
4. identifies activities, products, roles, preconditions, postconditions, feedback loops, and decision gates;
5. explains how the process will anticipate, tolerate, evaluate, and control change; and
6. defines how the process itself will be reviewed and improved.

### 4. Requirements

Your response must:

1. **Establish an evidence base.** Separate supplied facts, reasonable inferences, unresolved questions, and explicit assumptions. Label each assumption and explain why it matters.
2. **Characterize the project.** Evaluate at least:
   - requirements clarity and expected volatility;
   - stakeholder access and feedback frequency;
   - technical novelty and integration complexity;
   - safety, security, reliability, or regulatory criticality;
   - need for formal documentation, approval, or traceability;
   - delivery urgency and usefulness of partial releases;
   - availability, suitability, and lock-in risk of reusable components;
   - operational and deployment uncertainty.
3. **Compare viable models.** Compare waterfall, incremental, reuse-oriented, and hybrid approaches against the project characteristics. Include benefits, limitations, risks, and conditions under which each viable option would work.
4. **Select a model conditionally.** Recommend one primary process or a clearly defined hybrid. Do not claim that one model is universally best. If missing information could change the recommendation, state the recommendation as conditional and ask targeted questions.
5. **Cover all fundamental activities.** Define how the process performs:
   - software specification;
   - software design and implementation;
   - software validation; and
   - software evolution.
6. **Define process elements.** For every major stage or iteration, specify:
   - activities;
   - responsible and consulted roles;
   - input products;
   - output products;
   - preconditions;
   - postconditions or exit criteria;
   - review or approval points;
   - feedback paths to earlier work.
7. **Address change explicitly.** Include appropriate change-avoidance techniques, such as early analysis or throwaway prototyping, and change-tolerance techniques, such as iterative development and incremental delivery. Explain which prototypes, if any, must not become production code and why.
8. **Address reuse explicitly.** When reuse is plausible, include component discovery and evaluation, requirements modification, system configuration or adaptation, integration, licensing, compatibility, maintenance, and supplier-dependency checks.
9. **Use risk to shape the process.** Identify the main process-selection risks and show how analysis, prototyping, simulation, formal methods, incremental delivery, or other controls reduce them.
10. **Incorporate appropriate RUP ideas.** Where useful, map work to inception, elaboration, construction, and transition; distinguish time-based phases from recurring workflows; and apply relevant practices such as iterative development, requirements management, component-based architecture, visual modeling, quality verification, and controlled change.
11. **Include deployment and evolution.** Treat transition into the operational environment, monitoring, maintenance, and response to new requirements as part of the lifecycle rather than as afterthoughts.
12. **Support traceability.** Give stages, activities, risks, assumptions, and artifacts stable identifiers that later prompts and the router agent can reference.

### 5. Constraints

- Remain domain-agnostic; use only the supplied project information.
- Do not invent stakeholders, requirements, regulations, technologies, deadlines, budgets, or reuse candidates.
- Do not confuse a software-process model with a project schedule, development method, architecture, or programming framework.
- Do not default automatically to agile, waterfall, or a hybrid.
- Do not assume requirements can be completely frozen.
- Do not recommend formal methods solely because a system is described as important; connect the recommendation to concrete safety, security, or reliability needs and available expertise.
- Do not treat a throwaway prototype as production-ready software.
- Do not select reusable components without evaluating requirement fit and integration risk.
- Do not perform detailed requirements elicitation, architectural design, implementation, or test generation; identify those as later activities and artifacts.
- Prefer concise explanations that make tradeoffs visible and auditable.
- If essential information is missing, ask no more than `{{MAX_CLARIFYING_QUESTIONS | default: 7}}` high-value questions. Continue with labeled provisional assumptions when the user cannot answer.

### 6. Process

Follow these steps:

1. **Parse inputs.** Create a fact/inference/assumption/unknown ledger. Detect contradictions and missing decision-critical information.
2. **Clarify selectively.** Ask only questions whose answers could materially change the selected process or its controls. If interaction is unavailable, proceed provisionally and record the effect of each assumption.
3. **Create a project profile.** Rate each relevant selection factor as low, medium, high, or unknown and cite the supporting input or assumption.
4. **Generate candidates.** Evaluate waterfall, incremental, reuse-oriented, and at least one plausible hybrid. Exclude an option only with a stated reason.
5. **Choose and justify.** Use a transparent decision matrix with project-specific criteria and qualitative or numeric weights. Explain sensitivity: identify which changed facts would alter the recommendation.
6. **Design the lifecycle.** Define stages or iterations and map specification, design/implementation, validation, and evolution across them. Include deployment and supporting work such as documentation, configuration management, and change control.
7. **Define controls.** Specify artifacts, roles, entry conditions, exit criteria, reviews, feedback loops, decision gates, traceability, and change procedures.
8. **Plan for uncertainty.** Add targeted prototypes, experiments, component evaluations, or formal analysis only where they retire identified risks. State how their results affect routing or process choice.
9. **Check feasibility and coherence.** Confirm that the process fits the stated team, constraints, criticality, and stakeholder access; that every activity has inputs and outputs; and that feedback paths are possible.
10. **Self-verify.** Run the verification checklist below. Revise detected weaknesses before returning the final answer, and disclose any issue that cannot be resolved from the provided information.

### 7. Output

Return one Markdown document with these sections:

1. **Executive Recommendation** - recommended model or hybrid, confidence level, and concise rationale.
2. **Input and Assumption Ledger** - table with ID, statement, classification (`fact`, `inference`, `assumption`, or `unknown`), source, and decision impact.
3. **Project Process Profile** - table of selection factors, ratings, evidence, and implications.
4. **Process-Model Comparison** - decision matrix comparing waterfall, incremental, reuse-oriented, and hybrid options.
5. **Selected Process and Tailoring** - selected approach, rejected alternatives, tradeoffs, and conditions that would trigger reselection.
6. **Lifecycle Definition** - ordered stages or iterations showing where specification, design/implementation, validation, evolution, and deployment occur.
7. **Process Specification** - table with process-stage ID, activities, roles, inputs, outputs, preconditions, postconditions/exit criteria, review gate, and feedback route.
8. **Change and Uncertainty Strategy** - change avoidance, change tolerance, prototyping rules, requirement-change control, and iteration or delivery strategy.
9. **Reuse Strategy** - reuse decision and, if applicable, component evaluation, requirements adaptation, integration, and supplier risks. Write `Not currently justified` with reasons when reuse is unsupported.
10. **Risk-Driven Activities** - process risks, likelihood/impact, controls, owners, and evidence needed for closure.
11. **RUP Mapping** - concise mapping of phases and recurring workflows when useful; otherwise explain why it adds no value here.
12. **Process Improvement Loop** - measures, retrospective/review points, lessons log, and criteria for modifying the process.
13. **Router Handoff Block** - machine-readable YAML using this schema:

```yaml
chapter: 2
artifact_type: software_process_definition
project_summary: ""
recommended_process: ""
confidence: low | medium | high
current_phase: ""
completed_activities: []
next_activity: ""
next_prompt: ""
required_inputs: []
artifacts_produced: []
open_questions: []
assumptions: []
risks_requiring_reroute: []
loop_back_conditions: []
```

14. **Verification Results** - pass/fail/conditional status for every verification check, with evidence and corrective action.

### 8. Verification

Before finalizing, verify all of the following:

- **V-01 Completeness:** The lifecycle includes specification, design and implementation, validation, evolution, and deployment.
- **V-02 Evidence discipline:** Facts, inferences, assumptions, and unknowns are visibly separated; no invented project facts appear.
- **V-03 Comparative justification:** The recommendation follows from a comparison of viable models rather than from an unexplained default.
- **V-04 Context fit:** The selected process fits requirement volatility, stakeholder access, criticality, reuse opportunity, technical risk, schedule, and team context—or explicitly marks unavailable evidence.
- **V-05 Process definition:** Major stages identify activities, products, roles, preconditions, postconditions, and feedback paths.
- **V-06 Change readiness:** Both change avoidance and change tolerance are considered, with explicit loop-back triggers.
- **V-07 Prototype safety:** Throwaway prototypes are labeled and prevented from silently becoming production code without production-level redesign and verification.
- **V-08 Reuse integrity:** Reuse recommendations include requirement-fit, integration, compatibility, licensing, maintenance, and supplier-risk evaluation.
- **V-09 Risk linkage:** Every special activity or control is tied to an identified risk, constraint, or objective.
- **V-10 Lifecycle realism:** The process acknowledges iteration and feedback rather than presenting development as perfectly linear.
- **V-11 Transition and evolution:** Operational deployment, maintenance, and changing needs are included.
- **V-12 Traceability:** Stable identifiers connect inputs, assumptions, risks, activities, artifacts, gates, and router decisions.
- **V-13 Generality:** Replacing the project description with an unrelated domain would not make the instructions invalid.
- **V-14 Router readiness:** The YAML handoff is syntactically valid and identifies the next activity, required context, artifacts, and loop-back conditions.
- **V-15 Honest uncertainty:** Confidence is calibrated, unresolved issues are disclosed, and conditional recommendations state what evidence would resolve them.

If any check fails, revise the report before returning it. If revision requires unavailable information, mark the check `conditional`, explain the gap, and identify the exact question or evidence needed.

---

## Suggested Core Artifact

**Software Process Definition and Selection Report** - a domain-agnostic, traceable process plan that the router can use to initiate later requirements, modeling, architecture, implementation, testing, safety, security, evolution, and project-management prompts.
