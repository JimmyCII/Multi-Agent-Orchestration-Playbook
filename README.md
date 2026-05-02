# Multi-Agent Orchestration Playbook

A practical repo template for building and running a local, cost-aware, orchestrated agent system.

This setup is based on a real workflow where an orchestrator routes requests to specialist agents by risk and complexity, logs every routing decision, and keeps learning notes searchable over time.

> **This is a public template.** File paths in the agent files use `YOUR_PATH` placeholders. Search for `YOUR_PATH` after cloning and replace with your local directory.

## Prerequisites

- [VS Code](https://code.visualstudio.com/) with the [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) extension
- GitHub Copilot access (includes custom agent support)
- The agent files must live in `.github/agents/` — this path is required by VS Code for automatic agent discovery. Renaming or moving the folder will break agent loading.

## What This Repo Is For

- Build a local multi-agent workflow you can actually use daily
- Route tasks by cost and blast radius (low, medium, high)
- Keep a clean audit trail of routing decisions
- Support study + execution in one system
- Move from learning AI to deploying AI workflows

## Agent Roles

### 1) Orchestrator
- File: `.github/agents/cost-router-orchestrator.agent.md`
- Purpose: routes each request to exactly one specialist agent
- Routing logic:
  - Study-focused requests -> Study Partner
  - High-volume, repetitive work -> Low tier
  - Normal workflow logic -> Medium tier
  - Security/architecture/high-impact -> High tier

### 2) Study Partner
- File: `.github/agents/Study Partner.agent.md`
- Purpose: handles AI fundamentals study flows and quiz/explanation requests
- Logging target: configurable — update `YOUR_PATH` in the agent file to point to your local study log folder

### 3) Low Tier Specialist
- File: `.github/agents/cost-low-volume.agent.md`
- Purpose: low-cost repetitive tasks, tagging, triage, and transformation at scale

### 4) Medium Tier Specialist
- File: `.github/agents/cost-medium-workflow.agent.md`
- Purpose: normal implementation logic and practical workflow decisions

### 5) High Tier Specialist
- File: `.github/agents/cost-high-critical.agent.md`
- Purpose: architecture, security, compliance, and cascading-risk decisions

## Routing Audit

- File: `.github/agents/cost-routing-audit-log.md`
- Schema:

| Date | Task Summary | Routed To | Risk Level | Escalated | Reason | Confidence |
|---|---|---|---|---|---|---|

Use this to verify that high-tier usage is rare and justified.

## Recommended Repo Layout

```text
Multi-Agent-Orchestration-Playbook/
  README.md
  .gitignore
  docs/
    LinkedIn_Companion_Article.md
    study-partner/
      Study_Partner_Master_Prompt.md   ← agent behavior guide (customize this)
      Study_QA_Log_Template.md         ← log schema for saving Q&A records
  .github/
    agents/
      cost-router-orchestrator.agent.md
      Study Partner.agent.md
      cost-low-volume.agent.md
      cost-medium-workflow.agent.md
      cost-high-critical.agent.md
      cost-routing-audit-log.md
```

## Configuration: Update Local Paths

After cloning, search the agent files for `YOUR_PATH` and replace with your actual local paths:

| Placeholder | What to replace it with |
|---|---|
| `YOUR_PATH/agents/cost-routing-audit-log.md` | Path where you want the routing audit log written |
| `YOUR_PATH/Study Partner/Session Logs/AI900_Study_Session_Log.md` | Path where study Q&A should be logged |
| `YOUR_PATH/Study Partner/AI900_Master_Study_Partner.md` | Path to your local copy of the master prompt file |

## Study Partner Setup

The Study Partner agent uses two support files that live in `docs/study-partner/`:

### `Study_Partner_Master_Prompt.md`
This is the agent's behavior guide. It controls how the agent teaches, quizzes, and logs knowledge records.

**Customize your learning style** by editing the `### Your preferred learning style` section inside the master prompt block. It ships with generic defaults — personalize it to get better responses. Examples:
- `"I prefer analogies over abstract definitions."`
- `"Always give me a real-world example after explaining a concept."`
- `"I get confused between similar services — always compare side by side."`

**Change the exam target** by editing the `### Exam context` section. The template ships pre-configured for AI-900 but works for any certification.

### `Study_QA_Log_Template.md`
This is the schema the agent follows when writing knowledge records to your study log. It includes:
- A retrieval index table
- A worked example record
- A blank template for new entries

Your actual study log (with your Q&A history) stays local and is not committed to the repo.

## How To Use This Repo

1. Clone the repo and open it in VS Code.
2. Search for `YOUR_PATH` across `.github/agents/` and replace with your local paths.
3. Keep the existing file names to preserve agent cross-references.
4. Include `cost-routing-audit-log.md` so you can inspect routing behavior over time.
5. Add a short note in the audit log whenever routing policy changes.

## Why This Pattern Works

- Keeps cost under control by defaulting to the lowest sufficient tier
- Makes delegation explicit and testable
- Preserves evidence of decisions through audit logs
- Separates study context from implementation context
- Scales as you add more specialist agents

## Suggested Next Step

Add one domain specialist agent at a time (for example: data quality, feature engineering, or deployment validation), then update the orchestrator routing policy and audit for one week before adding the next.

## Contributing

PR's welcome. If you add a new specialist agent, include:
- The `.agent.md` file in `.github/agents/`
- A one-line entry in this README under Agent Roles
- An update to the orchestrator routing policy describing when to route to it

## License

See [LICENSE](LICENSE).
