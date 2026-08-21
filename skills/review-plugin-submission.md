---
name: review-plugin-submission
description: Audit a Cursor plugin for marketplace readiness (manifests, component metadata, discovery paths, submission quality).
---

# Review Plugin submission

Use when a Plugin is implemented and needs a quality check before submission or release.

## Workflow

1. Manifest: file exists; `name` is lowercase kebab-case; `description`, `version`, `author`, `license` cohere.
2. Discoverability: Skills in `skills/*/SKILL.md`; rules, agents, commands, hooks, MCP config in their conventional places.
3. Metadata: Skills include `name` and `description` frontmatter. Rules, agents, and commands include required frontmatter.
4. Repository: marketplace entry exists for multi-plugin repos; `source` resolves; names are unique.
5. Documentation: `README.md` states purpose, installation, and component coverage. Optional logo path is valid and repository-hosted.

## Checklist

- Manifest parses as JSON
- Declared paths exist and are relative
- No broken file references
- No missing frontmatter
- Scope is focused
- Marketplace registration complete when required

## Output

Pass/fail by section, prioritized fix list, submission recommendation.
