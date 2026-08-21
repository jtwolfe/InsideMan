---
name: create-plugin-scaffold
description: Create a new Cursor plugin scaffold with a valid manifest, component directories, and marketplace wiring.
---

# Create Plugin scaffold

Use when starting a new Plugin or adding a Plugin to a multi-plugin repository.

## Inputs

- Plugin name (lowercase kebab-case)
- Purpose and target operators
- Component set: `rules`, `skills`, `agents`, `commands`, `hooks`, `mcpServers`
- Repository style: single-plugin or multi-plugin marketplace

## Output location

Default: the operator's local Plugin directory on the Operator computer, placeholder `<operator-computer>/plugins/local/<plugin-name>/`. If the operator names another directory, use that. Do not write a real home path.

## Workflow

1. Validate the name: lowercase kebab-case, starts and ends alphanumeric.
2. Create the target directory if needed.
3. Create base files: Plugin manifest, `README.md`, `LICENSE`, optional `CHANGELOG.md`.
4. Manifest fields: required `name`; recommended `version`, `description`, `author`, `license`, `keywords`. Add explicit component paths only when discovery defaults are not enough.
5. Component files with frontmatter:
   - Skills: `skills/<skill-name>/SKILL.md` with `name`, `description`
   - Rules, agents, commands: `name` + `description` as required by the Plugin format
6. If the repository uses a marketplace manifest, add a Plugin entry with `name`, `source`, optional metadata.
7. All manifest paths are relative. No absolute paths. No parent traversal.

## Guardrails

- One use case per Plugin.
- Concise Skill and rule text.
- Do not reference files that do not exist.
- Keep managed / plugin Skills read-only; this Skill writes a new user Plugin.

## Output

File tree, final manifest, marketplace entry if any, short validation report.
