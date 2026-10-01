---
name: skill-installer-satno
description: Install and configure SATNO skill bundles from the local SATNO skill repository and vetted upstream GitHub repositories. Use when setting up Codex/compatible coding agents for SATNO CRM, Bale Market, Tender Radar, satnoco.ir, or when refreshing project-level skills.
---

# SATNO Skill Installer

## Goal
Install only the skills relevant to the target SATNO project, keeping local SATNO instructions and vetted upstream skills separate.

## Before installation
1. Identify the target project.
2. Read `skills-bank/registry.json`.
3. Read `skills-bank/PROJECT-BUNDLES.md`.
4. Check whether the agent/runtime supports Agent Skills and which local directory it uses.
5. Prefer project-scoped installation for shared repositories.
6. Do not overwrite a SATNO-local skill with an upstream skill of the same name without review.

## Open ecosystem CLI
When available, the open `skills` CLI can install skills from GitHub:

```bash
npx skills add OWNER/REPO --skill SKILL_NAME
```

Use `--list` before installing a large upstream repository.

## Recommended upstream installs

### SATNO CRM
```bash
npx skills add supabase/agent-skills --skill supabase
npx skills add vercel-labs/agent-skills --skill react-best-practices
```

### WordPress / Tender Radar
```bash
npx skills add WordPress/agent-skills --list
npx skills add WordPress/agent-skills --skill wordpress-router wp-project-triage wp-plugin-development wp-rest-api wp-wpcli-and-ops wp-performance
```

### Playwright
Use the Playwright CLI skill matching the installed Playwright version. Prefer the official Playwright installation mechanism rather than copying a stale SKILL.md.

## SATNO-local skills
Install/link relevant local folders from this repository alongside upstream skills:
- satno-crm-developer
- satno-bale-market
- satno-tender-radar
- satno-brand
- satno-solar-engineering
- frontend-design
- webapp-testing
- mcp-builder

## Verification
After installation:
1. Confirm every expected skill directory contains `SKILL.md`.
2. Check for duplicate names.
3. Confirm referenced scripts/references were installed with upstream skills.
4. Run a small trigger prompt for each critical skill.
5. Record the installed upstream revision when reproducibility matters.

## Updates
Do not blindly overwrite local adaptations. Update upstream packages first, review changes, then re-test project workflows.
