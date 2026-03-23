# DuelPlan

Adversarial plan review for Claude Code. Claude drafts a plan, Codex CLI tears it apart, Claude revises, repeat until stable.

## How It Works

Instead of drafting a plan once and hoping for the best, DuelPlan runs an automated critique loop:

1. **Claude drafts** an implementation plan based on your prompt and repo context
2. **Codex critiques** the plan adversarially — finding gaps, bad assumptions, missing edge cases
3. **Claude revises** based on the critique
4. **Repeat** until the plan converges (max 5 rounds)

Issues are rated by severity (CRITICAL / MAJOR / MINOR). The loop exits when only minor feedback remains. You get the full critique history so you can see how the plan evolved.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Codex CLI](https://github.com/openai/codex) installed and configured

## Installation

### Claude Code (Official Marketplace)

```bash
/plugin install duelplan@claude-plugins-official
```

### Claude Code (Self-Hosted Marketplace)

Register the marketplace first:

```bash
/plugin marketplace add DevStrategist/duelplan
```

Then install:

```bash
/plugin install duelplan@duelplan
```

## Usage

Ask for extra rigor on any plan:

- "use duelplan"
- "I want adversarial review on this plan"
- "give this plan extra scrutiny"

The skill activates automatically when Claude detects you want a more rigorous planning process.

## Works Great With

We recommend [Superpowers](https://github.com/obra/superpowers) to level up the planning and development stages for both Codex and Claude Code. DuelPlan handles adversarial review of plans; Superpowers handles the broader workflow — brainstorming, TDD, execution, code review. They complement each other well.

## What's Inside

### Skills

- **duelplan** — Adversarial critique loop between Claude and Codex CLI

## License

MIT License — see [LICENSE](LICENSE) for details.
