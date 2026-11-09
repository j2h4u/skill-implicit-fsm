# Implicit FSM

An agent skill for discovering implicit finite-state machines (FSMs), auditing and refining their behavioral contracts, and implementing explicit machines where justified. It treats existing code as evidence rather than the final specification.

**Status:** experimental. Comparative benefit over working without this skill has not been established.

## Install

Clone into a skill directory supported by your host. For hosts that discover `~/.agents/skills`, run:

```sh
git clone https://github.com/j2h4u/skill-implicit-fsm.git ~/.agents/skills/implicit-fsm
```

The destination must not already exist. If it is already installed, update that installation instead. The skill has no runtime package dependency of its own; project-specific analysis and tests may require tools.

## Update

```bash
git -C ~/.agents/skills/implicit-fsm pull --ff-only
```

The host controls skill discovery and whether a reload or new session is needed.

## Use

> Use $implicit-fsm to audit this repository.

To request implementation as well:

> Use $implicit-fsm to audit this repository and implement justified explicit state machines.

See [SKILL.md](SKILL.md) for the workflow and requirements. Evaluation or improvements to the skill itself are separate work performed when requested; see [EVALUATION.md](EVALUATION.md).

## License

The [PolyForm Noncommercial License 1.0.0](LICENSE.md) permits use for the purposes described in its terms. Commercial use requires separate written permission or a license from the owner, subject to the license's terms and exceptions. To request permission, [open an issue](https://github.com/j2h4u/skill-implicit-fsm/issues/new) or contact the owner through [GitHub](https://github.com/j2h4u).
