# Implicit FSM

An agent skill for discovering implicit finite-state machines (FSMs), refining their behavioral contracts, and implementing explicit machines where justified. It treats existing code as evidence rather than the final specification.

The workflow maps states and transitions, extracts and challenges properties, then independently researches and red-teams them. A separate whole-contract review looks for interactions and missing requirements. For an authorized conversion, the skill requires a formally checkable specification and generated stateful property-based and model-based tests that are actually run against the implementation. It records which formal obligations were checked; a checkable specification is not a proof of the implementation.

The skill supports discovery and audit without changing target code, as well as implementation when requested. Set a discovery boundary, property limit, and resource budget before review. The full process requires an agent with suitable code and test tools and isolated delegation; if independent review is unavailable, the agent must report the limitation.

**Status:** experimental. Comparative benefit over working without this skill has not been established.

## Install

Clone into a skill directory supported by your host. For hosts that discover `~/.agents/skills`, run:

```sh
git clone https://github.com/j2h4u/skill-implicit-fsm.git ~/.agents/skills/implicit-fsm
```

The destination must not already exist. If it is already installed, update that installation instead. The host controls skill discovery and whether a reload or new session is needed. The skill has no runtime package dependency of its own; project-specific analysis and tests may require tools.

## Use

For a complete, bounded workflow, adapt this request:

> Use $implicit-fsm on the order lifecycle in this repository. Discover its implicit state machines, refine their contracts and implement justified explicit machines. Limit discovery to the order workflow, review at most 10 initial properties and use a budget of 24 agent tasks. Save the audit outside the source tree, run the required generated tests and report checked formal obligations and remaining gaps.

For an audit without implementation:

> Use $implicit-fsm to audit the order lifecycle in this repository. Limit discovery to the order workflow, review at most 5 initial properties and use a budget of 12 agent tasks. Save the audit outside the source tree and report findings and proposed actions; do not modify target code.

See [SKILL.md](SKILL.md) for the workflow and requirements. Evaluation or improvements to the skill itself are separate work performed when requested; see [EVALUATION.md](EVALUATION.md).

## License

The [PolyForm Noncommercial License 1.0.0](LICENSE.md) permits use for the purposes described in its terms. Commercial use requires separate written permission or a license from the owner, subject to the license's terms and exceptions. To request permission, [open an issue](https://github.com/j2h4u/skill-implicit-fsm/issues/new) or contact the owner through [GitHub](https://github.com/j2h4u).
