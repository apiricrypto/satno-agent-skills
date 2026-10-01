# SATNO Agent Skills v1

A curated set of Agent Skills for ChatGPT/Codex workflows used by SATNO projects.

## Included skills

- `skill-creator-openai` — create, review, test, and improve new skills.
- `satno-crm-developer` — develop and test SATNO CRM with Persian-first/RTL conventions.
- `satno-brand` — enforce SATNO visual and copy standards.
- `satno-tender-radar` — maintain the SATNO Tender Radar workflow and outputs.
- `satno-bale-market` — develop the Bale market-intelligence collector and dashboard.
- `satno-solar-engineering` — structure solar engineering calculations, checks, and deliverables.
- `frontend-design` — design polished Persian/RTL interfaces for SATNO web products.
- `webapp-testing` — run browser-based regression and release-readiness checks.
- `mcp-builder` — build secure MCP integrations for SATNO systems and agents.

## Skill format

Each skill lives in its own folder and contains a required `SKILL.md` file with YAML frontmatter and operational instructions.

## Usage

Keep this repository under version control. Install or register individual skill folders in the environment that supports Agent Skills. Review tool names and permissions for the target ChatGPT/Codex workspace before relying on automation actions.

## Design principles

1. Persian is the default user-facing language for SATNO workflows unless explicitly overridden.
2. Prefer deterministic, testable workflows over vague instructions.
3. Never assume external access; check the available tools before acting.
4. Preserve project-specific conventions, repositories, data formats, and safety constraints.
5. Use small, focused skills rather than one oversized instruction file.
