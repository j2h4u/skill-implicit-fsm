# Evaluation

The workflow is a working hypothesis, not an empirically validated audit method.

## Assignment for the evaluating agent

Use the skill to discover implicit FSMs, refine their contracts and deliver justified explicit implementations when requested, while evaluating the method. Deliver the FSM map and candidate decisions, behavioral-contract audit, authorized project changes and their verification, and actionable feedback on the skill. Evaluate both axes: useful state-machine reconstruction and implementation, and justified contract refinement. Finding counts and conversion counts alone do not measure quality. Preserve discovery-only or audit-only scope when that is what the user requested.

Before running, record the skill version or file fingerprints as well as the target snapshot. Keep the skill unchanged during the run so findings can be attributed to that version. Capture instruction ambiguities, missing guidance, unnecessary work, tool limitations and departures from the prescribed workflow as they occur; do not reconstruct a friction-free story afterward.

Alongside requested project work, save `evaluation.md` beside the artifacts. Include:

- Project and discovery scope, target and skill snapshots, completed/skipped stages and resource use.
- FSM candidates, reconstruction evidence and gaps, links to properties, and the reason for converting or retaining each candidate. For each implemented machine, record the model-to-runtime mapping, runnable generated stateful PBT/MBT commands, actual results, coverage or explored bounds and retained failure cases, formal-check readiness and obligations actually checked, including assumptions, bounds and code correspondence. Compare old and new representations; do not label conversion complete when required outputs are missing.
- What research changed in R0, what adversarial review added, and what whole-contract review found; link concrete property IDs, reports and evidence. Distinguish useful corrections, unsupported objections, duplication and unresolved product questions.
- Project changes derived from those findings, before/after scenarios and checks actually run; distinguish implemented, verified, deployed and deferred work. Assess whether the audit helped deliver useful changes or created unnecessary work.
- Instruction problems: wording or missing anchor → observed consequence → smallest proposed correction. Distinguish a skill defect from unavailable tooling, missing project information or an execution mistake.
- Recommended skill changes and what needs another trial. A successful case is not evidence of universal effectiveness.

If the user requested evaluation only, return the report and proposed edits. If the user also requested improving the skill, apply evidence-supported corrections after preserving the evaluated version, validate the updated skill, and record each change and its basis in `evaluation.md`. Keep cross-project applicability; do not encode incidental project details as general rules. Recheck the affected scenario and state whether it was actually rerun. Project improvement and skill improvement are distinct deliverables; complete both when requested.

## Method validation

Real-project feedback is useful on its own. For a separate method validation, use isolated known-defect and correct controls with expected outcomes hidden from auditing agents: a cross-property deadlock; a constraint contrary to a confirmed product goal; late discovery under a tight budget; a conditional property whose trigger never occurred; and a model that passes while its runtime adapter or effects are wrong. Assess detection and unsupported objections; repeat on another project before generalizing.

For comparative efficacy claims, run a fresh-context no-skill baseline matched on task, target snapshot, model and effort, available information, authorization and comparable budget. Independently assess correctness, useful FSM, code and test outcomes, unsupported constraints and costs. Without that baseline, state that comparative benefit was not measured. One case does not establish universal effectiveness.

## Open before execution

Target projects and workflows; numeric budget and candidate limit; available isolated agents; appropriate safe test commands; output location; who accepts proposed contract changes. Languages and test libraries remain project-specific. Markdown is the initial storage choice, not a required infrastructure standard.

Example request, after filling the scope and budget:

> Use $implicit-fsm to discover implicit state machines in [workflow] in [repository], refine their contracts and implement justified explicit FSMs, while evaluating and improving the skill. Read EVALUATION.md in the skill directory. Bound discovery to [boundary] and deep property review to [number] initial properties, within [budget]. Trace selected properties across the product. Save both snapshots, the FSM map, R0/R1/R2/Rfinal, independent reports and journal in [directory]. After adjudication, implement justified FSM conversions and confirmed fixes, verify the affected behavior and explain retained candidates; separate unresolved requirement changes. Save evaluation.md with project outcomes and skill feedback, apply evidence-supported skill improvements, and report changes, checks and remaining work separately for the project and skill.

## Evidence behind the method

The invariant-mining sources below received a bounded primary-source review on 2026-11-07; newest dated source in that review was 2026-09-01. Coverage is not exhaustive through November. Selected primary sources were checked directly.

- [Daikon manual, v5.9.0, 2026-09-01](https://plse.cs.washington.edu/daikon/download/doc/daikon.html): dynamic candidates, overfitting, additional-trace checking, conditional properties and logical suppression. Reserving independent validation executions is our workflow adaptation, not an established universal split protocol.
- [Vacuity detection, 2003](https://cris.huji.ac.il/en/publications/vacuity-detection-in-temporal-model-checking-14/): a conditional temporal property can pass because its triggering condition never occurs. Check activation as well as violations.
- [ICE, CAV 2014](https://publications.rwth-aachen.de/record/444203): invariant learning distinguishes examples, counterexamples and implication constraints. Adapting this to audit refinement is our inference; failed inductiveness alone is not a reachable defect.
- [Quokka, revised 2026-08-08](https://arxiv.org/abs/2509.21629): experimental LLM invariant generation checked against target assertions. It supports external checking, not the efficacy of our multiagent process or product-level justification.
- [LISA, submitted 2026-07-21](https://arxiv.org/abs/2607.18711): experimental invariant-based functional testing reports bug candidates for developer confirmation. This supports checking generated claims against executions and intended semantics, not automatically accepting inferred behavior as requirements.

These sources inform candidate validation. They do not validate one-property-per-agent, two review passes, completeness of the registry, or the usefulness of any mined requirement. No specific inference tool, solver or confidence threshold is required.

## Python tooling review — 2026-11-07

Parallel Research and direct primary-source checks support Hypothesis stateful as the initial Python option, with Schemathesis for linked API workflows. Complementary tools have distinct roles:

- [CrossHair](https://crosshair.readthedocs.io/en/latest/introduction.html): symbolic counterexample search for typed functions with contracts, useful for pure transitions and guards. Its [limitations](https://crosshair.readthedocs.io/en/latest/limitations.html) explicitly exclude treating absence of a counterexample as a guarantee.
- [Atheris](https://github.com/google/atheris): coverage-guided fuzzing for Python and native extensions, especially parsers and decoders; it needs a harness and semantic assertions, not a replacement for FSM models.
- [GraphWalker RS](https://graphwalker.github.io/graphwalker-rs/getting-started.html): graph-based path generation with coverage objectives; a Python adapter must execute actions and check results. Assess integration before adoption. The [older Java repository](https://github.com/GraphWalker/graphwalker-project) was archived on 2026-10-17.
- [AltWalker](https://pypi.org/project/altwalker/): Python-capable graph MBT runner using GraphWalker; latest listed PyPI release at review was 0.4.0, dated 2023-09-20. Check compatibility rather than inferring either abandonment or suitability from the release date.

Check scenario isolation against [Hypothesis fixture semantics](https://hypothesis.readthedocs.io/en/latest/reference/api.html#hypothesis.HealthCheck.function_scoped_fixture) and durable regressions against its [replay guidance](https://hypothesis.readthedocs.io/en/latest/tutorial/replaying-failures.html). Test sequential and concurrent claims separately. Tool status is a dated snapshot, not a permanent recommendation; this review did not install tools or establish comparative performance.
