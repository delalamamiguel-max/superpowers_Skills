# Superpowers

Superpowers is a complete software development workflow for your coding agents, built on top of a set of composable "skills" and some initial instructions that make sure your agent uses them.

## How it works

It starts from the moment you fire up your coding agent. As soon as it sees that you're building something, it *doesn't* just jump into trying to write code. Instead, it steps back and asks you what you're really trying to do. 

Once it's teased a spec out of the conversation, it shows it to you in chunks short enough to actually read and digest. 

After you've signed off on the design, your agent puts together an implementation plan that's clear enough for an enthusiastic junior engineer with poor taste, no judgement, no project context, and an aversion to testing to follow. It emphasizes true red/green TDD, YAGNI (You Aren't Gonna Need It), and DRY. 

Next up, once you say "go", it launches a *subagent-driven-development* process, having agents work through each engineering task, inspecting and reviewing their work, and continuing forward. It's not uncommon for Claude to be able to work autonomously for a couple hours at a time without deviating from the plan you put together.

There's a bunch more to it, but that's the core of the system. And because the skills trigger automatically, you don't need to do anything special. Your coding agent just has Superpowers.


## Sponsorship

If Superpowers has helped you do stuff that makes money and you are so inclined, I'd greatly appreciate it if you'd consider [sponsoring my opensource work](https://github.com/sponsors/obra).

Thanks! 

- Jesse


## Installation

**Note:** Installation differs by platform. Claude Code or Cursor have built-in plugin marketplaces. Codex and OpenCode require manual setup.

### Claude Code Official Marketplace

Superpowers is available via the [official Claude plugin marketplace](https://claude.com/plugins/superpowers)

Install the plugin from Claude marketplace:

```bash
/plugin install superpowers@claude-plugins-official
```

### Claude Code (via Plugin Marketplace)

In Claude Code, register the marketplace first:

```bash
/plugin marketplace add obra/superpowers-marketplace
```

Then install the plugin from this marketplace:

```bash
/plugin install superpowers@superpowers-marketplace
```

### Cursor (via Plugin Marketplace)

In Cursor Agent chat, install from marketplace:

```text
/add-plugin superpowers
```

or search for "superpowers" in the plugin marketplace.

### Codex

Tell Codex:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

**Detailed docs:** [docs/README.codex.md](docs/README.codex.md)

### OpenCode

Tell OpenCode:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

**Detailed docs:** [docs/README.opencode.md](docs/README.opencode.md)

### GitHub Copilot CLI

```bash
copilot plugin marketplace add obra/superpowers-marketplace
copilot plugin install superpowers@superpowers-marketplace
```

### Gemini CLI

```bash
gemini extensions install https://github.com/obra/superpowers
```

To update:

```bash
gemini extensions update superpowers
```

### Verify Installation

Start a new session in your chosen platform and ask for something that should trigger a skill (for example, "help me plan this feature" or "let's debug this issue"). The agent should automatically invoke the relevant superpowers skill.

## The Basic Workflow

1. **brainstorming** - Activates before writing code. Refines rough ideas through questions, explores alternatives, presents design in sections for validation. Saves design document.

2. **using-git-worktrees** - Activates after design approval. Creates isolated workspace on new branch, runs project setup, verifies clean test baseline.

3. **writing-plans** - Activates with approved design. Breaks work into bite-sized tasks (2-5 minutes each). Every task has exact file paths, complete code, verification steps.

4. **subagent-driven-development** or **executing-plans** - Activates with plan. Dispatches fresh subagent per task with two-stage review (spec compliance, then code quality), or executes in batches with human checkpoints.

5. **test-driven-development** - Activates during implementation. Enforces RED-GREEN-REFACTOR: write failing test, watch it fail, write minimal code, watch it pass, commit. Deletes code written before tests.

6. **requesting-code-review** - Activates between tasks. Reviews against plan, reports issues by severity. Critical issues block progress.

7. **finishing-a-development-branch** - Activates when tasks complete. Verifies tests, presents options (merge/PR/keep/discard), cleans up worktree.

**The agent checks for relevant skills before any task.** Mandatory workflows, not suggestions.

## What's Inside

### Skills Library

**Testing**
- **test-driven-development** - RED-GREEN-REFACTOR cycle (includes testing anti-patterns reference)

**Debugging**
- **systematic-debugging** - 4-phase root cause process (includes root-cause-tracing, defense-in-depth, condition-based-waiting techniques)
- **verification-before-completion** - Ensure it's actually fixed

**Collaboration** 
- **brainstorming** - Socratic design refinement
- **writing-plans** - Detailed implementation plans
- **executing-plans** - Batch execution with checkpoints
- **dispatching-parallel-agents** - Concurrent subagent workflows
- **requesting-code-review** - Pre-review checklist
- **receiving-code-review** - Responding to feedback
- **using-git-worktrees** - Parallel development branches
- **finishing-a-development-branch** - Merge/PR decision workflow
- **subagent-driven-development** - Fast iteration with two-stage review (spec compliance, then code quality)

**Meta**
- **writing-skills** - Create new skills following best practices (includes testing methodology)
- **using-superpowers** - Introduction to the skills system

## Philosophy

- **Test-Driven Development** - Write tests first, always
- **Systematic over ad-hoc** - Process over guessing
- **Complexity reduction** - Simplicity as primary goal
- **Evidence over claims** - Verify before declaring success

Read more: [Superpowers for Claude Code](https://blog.fsck.com/2025/10/09/superpowers/)

## Contributing

Skills live directly in this repository. To contribute:

1. Fork the repository
2. Create a branch for your skill
3. Follow the `writing-skills` skill for creating and testing new skills
4. Submit a PR

See `skills/writing-skills/SKILL.md` for the complete guide.

## Updating

Skills update automatically when you update the plugin:

```bash
/plugin update superpowers
```

## License

MIT License - see LICENSE file for details

## Community

Superpowers is built by [Jesse Vincent](https://blog.fsck.com) and the rest of the folks at [Prime Radiant](https://primeradiant.com).

- **Discord**: [Join us](https://discord.gg/35wsABTejz) for community support, questions, and sharing what you're building with Superpowers
- **Issues**: https://github.com/obra/superpowers/issues
- **Release announcements**: [Sign up](https://primeradiant.com/superpowers/) to get notified about new versions


---

# Owned checkout guide

## Purpose and status

`superpowers_Skills` is the owned reference fork of [obra/superpowers](https://github.com/obra/superpowers). The original upstream README, Jesse Vincent's attribution/sponsorship material and license links above are preserved unchanged. This guide maps the inspected checkout; it does not assert that a harness has installed or activated it.

## Repository map

- `skills/`, `commands/`, `agents/`: behavior instructions and agent/workflow definitions.
- `hooks/`: session-start registration and hook wrappers.
- `.claude-plugin/`, `.cursor-plugin/`, `.codex/`, `.opencode/`, `gemini-extension.json`: harness integrations.
- `tests/`: harness, triggering, explicit-request and workflow test scenarios.
- `docs/`, `scripts/`: supporting guides and tooling.
- `AGENTS.md`, `LICENSE`, release/change logs: contribution rules, MIT terms and history.

## Architecture and integrations

Superpowers is a composable agent workflow/plugin. The Claude session-start hook emits skill instructions; Codex setup uses native discovery through a skill-directory symlink. Other harnesses have their own adapters. The root package is ESM metadata with no npm script suite; it is not a standalone product server.

## Setup and environments

Follow the preserved platform-specific documentation only for separately approved installation. Cloning, symlinking, marketplace registration and updates modify installed agent behavior. Codex symlinks make changes to their target immediately visible to discovery; restart/discovery behavior still requires verification in the chosen harness. No repository provider credentials are required merely to read the instructions.

## Safe commands

For this documentation review use `git status --short`, `git diff -- README.md` and `git diff --check`. Upstream install, update, build, test and deployment examples above are retained reference material, not commands executed or authorized by this README rollout.

Do not invoke session hooks, plugin installers, agent tests or skill workflows for README review. In particular, descriptions of subagent-driven development are library content, not a request to launch agents during this task.

## Testing and validation

Test directories exercise real harness behavior and can launch agents or consume model usage. Static documentation review is not a harness evaluation. No skill text, hooks or adapters changed, so this update makes no behavioral improvement claim or test-pass claim.

## Deployment and rollback

No hosted application is deployed by this fork README. Installed plugin versions or symlink targets must be managed separately; restore the approved prior version/target without deleting user projects or unrelated configuration. This local documentation branch has not been published or installed.

## Risks and guardrails

Preserve MIT notices and upstream voice/behavior-shaping instructions. The contributor rules reject fork-specific upstream submissions and require human review before submission. This guide is for the owned fork only, with no upstream PR prepared or submitted. Do not represent a static review as human readiness approval or tested agent behavior.

## Related documentation

- [Contributor rules](AGENTS.md)
- [Codex installation reference](.codex/INSTALL.md)
- [Codex guide](docs/README.codex.md)
- [OpenCode guide](docs/README.opencode.md)
- [License](LICENSE)

This owned-checkout guide was checked statically only. No installation, application build/test, agent invocation, provider call, target acquisition, database operation or deployment was performed. Installed state, upstream freshness, external URLs and runtime behavior remain unverified.
