# Contributing

## Skill Structure

Each skill is a directory with a `SKILL.md` file:

```
skill-name/
└── SKILL.md
```

## SKILL.md Format

```yaml
---
name: skill-slug
description: "What this skill does. Use for: use cases. Triggers: keyword1, keyword2"
allowed-tools: Bash(curl *), WebFetch
---

# Skill Title

Content, examples, and commands.
```

## Adding a Model Skill

1. Create `models/<model-slug>/SKILL.md`
2. Use the exact API slug as directory name
3. Document all input parameters with types and defaults
4. Include 2-3 working curl examples using the Prediction API
5. Add Related Models links

## Adding a Category Skill

1. Create `categories/<domain>/<skill-name>/SKILL.md`
2. Include a Recommended Models table
3. Use each::sense API for all examples
4. Include `image_urls` example where relevant
5. Add streaming note
6. Include prompt engineering tips
7. Add Related Skills and Related Models links

## Adding a Default Skill

1. Create `<skill-name>/SKILL.md` at the repo root
2. These are core generative capabilities (image-generation, video-generation, etc.)
3. Use each::sense API
4. Include Available Models table with all relevant models

## Style Guide

- kebab-case for all directory names
- Model dirs must match API slugs exactly
- All curl examples use `$EACHLABS_API_KEY`
- Include streaming note in every category/default skill

## Testing

```bash
export EACHLABS_API_KEY="your-key"
# Run any curl example from a SKILL.md
```
