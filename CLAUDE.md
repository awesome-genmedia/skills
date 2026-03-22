# awesome-genmedia/skills

Generative media skills for AI agents, powered by each::labs.

## Repository Structure

- Root level (`image-generation/`, `video-generation/`, etc.) — Default skills for core generative media capabilities
- `categories/` — Use-case skills organized by domain (design, fashion, gaming, etc.)
- `models/` — Standalone skills for each of the 431 AI models
- `guides/` — Educational content (planned)

## API Patterns

### Default skills & categories → each::sense Agent API

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "..."}],
    "image_urls": ["https://example.com/photo.jpg"],
    "stream": false
  }'
```

- `image_urls` is a top-level parameter (not inside messages). Maximum 4 images.
- `stream`: `true` for SSE streaming, `false` for single response.

### models/ → Prediction API

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{"model": "<slug>", "version": "0.0.1", "input": {...}}'
```

## Environment Variable

All skills expect `EACHLABS_API_KEY` to be set. Get one at https://eachlabs.ai.

## Conventions

- SKILL.md files use YAML frontmatter: `name`, `description` (with triggers), `allowed-tools`
- Model directory names match API slugs exactly
- Category skills include a "Recommended Models" or model comparison table
- All curl examples use `$EACHLABS_API_KEY`
