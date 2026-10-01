---
name: skill-creator-openai
description: Create, revise, test, and document Agent Skills for ChatGPT or Codex. Use when the user wants to turn a recurring workflow into a reusable skill, improve an existing SKILL.md, define triggering behavior, add tool requirements, or build evaluation cases for a skill.
---

# Skill Creator for OpenAI Agent Skills

## Objective
Turn repeatable workflows into compact, reliable Agent Skills that can be versioned, tested, and reused.

## Workflow
1. Capture the intent from the current conversation before asking for information already available.
2. Define the trigger conditions, expected inputs, expected outputs, required tools, and failure conditions.
3. Keep the skill narrow enough to have a clear job.
4. Write `SKILL.md` with YAML frontmatter containing at least `name` and `description`.
5. Put trigger guidance in the description; put execution procedure in the body.
6. Add explicit checks for permissions, missing tools, external credentials, and destructive actions.
7. When outputs are objectively testable, create representative test prompts and expected properties.
8. Revise the skill after failures or user corrections.

## Writing rules
- Prefer imperative, operational instructions.
- Avoid model-specific references unless the skill truly depends on them.
- Do not hard-code secrets, API keys, tokens, passwords, or private identifiers.
- Do not promise background work unless an automation tool is actually available.
- Reuse known project context instead of repeatedly asking the user to restate it.
- Make tool prerequisites explicit.

## Minimum quality checks
Before considering a skill ready, verify:
- The description clearly explains when it should trigger.
- The skill has a single primary responsibility.
- Tool dependencies are realistic for the target environment.
- Failure paths are defined.
- The output format is clear.
- No confidential values are embedded.

## Suggested repository layout
```
skill-name/
  SKILL.md
  references/      # optional
  scripts/         # optional
  examples/        # optional
```
