---
name: ai-stock-photo
description: "Generate stock photography using each::sense AI. Create professional, commercially viable photographs for business, lifestyle, technology, nature, food, and editorial use. Produce realistic, diverse imagery without licensing restrictions. Use for: stock photos, commercial photography, business imagery, lifestyle photos, editorial photography. Triggers: stock photo, stock image, commercial photo, business photo, lifestyle photo, stock photography, royalty free, editorial photo, professional photo, generic photo"
allowed-tools: Bash(curl *), WebFetch
---

# AI Stock Photo Generator

Generate professional stock photography for commercial and editorial use using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A diverse team of four professionals collaborating around a conference table with laptops and coffee cups, modern glass-walled office, natural daylight streaming in, candid moment of someone presenting an idea, warm and productive atmosphere, professional business stock photography"
      }
    ],
    "stream": false
  }'
```

### Using Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": "A diverse team of four professionals collaborating around a conference table with laptops and coffee cups, modern glass-walled office, natural daylight streaming in, candid moment of someone presenting an idea, warm and productive atmosphere, professional business stock photography"
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Stock Photo Generation

- **Aim for authenticity** — describe candid, natural moments rather than stiff posed scenes.
- **Include diversity** — specify varied ages, ethnicities, and body types for inclusive imagery.
- **Leave space for copy** — add "with negative space on the left for text" for editorial and marketing use.
- **Specify lighting** — "natural window light," "golden hour," or "studio softbox" for professional quality.
- **Think commercially** — describe scenes that could work for multiple industries and contexts.
- **Avoid branded items** — do not reference specific brands, logos, or recognizable trademarks.

## Examples

### Technology / SaaS

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A software developer working at a standing desk with dual monitors showing code, modern minimalist home office, plants and natural light, focused and calm expression, cup of coffee nearby, authentic work-from-home stock photography"
      }
    ],
    "stream": false
  }'
```

### Healthcare

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A friendly female doctor in a white coat having a conversation with a patient in a clean modern examination room, warm overhead lighting, reassuring body language, medical equipment subtly visible in the background, professional healthcare stock photography"
      }
    ],
    "stream": false
  }'
```

### Nature / Environment

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An aerial view of a winding river cutting through an autumn forest, vibrant fall foliage in orange, red, and gold, morning mist rising from the water, dramatic landscape photography, editorial quality nature stock photo"
      }
    ],
    "stream": false
  }'
```

### Batch Stock Generation

```bash
# Generate a set of related stock photos for a wellness brand
SCENES=(
  "A woman practicing yoga on a wooden deck overlooking a calm lake at sunrise, serene and peaceful, warm golden light, wellness stock photo"
  "A colorful smoothie bowl topped with fresh berries and granola on a marble countertop, overhead flat lay, bright natural light, healthy lifestyle stock photo"
  "Hands holding a small potted succulent plant, soft focus background, natural skin tones, mindfulness and self-care concept, stock photography"
)

for SCENE in "${SCENES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$SCENE\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Workflow: Stock Photo Library

1. **Identify themes** — Business, technology, health, nature, food, lifestyle, education.
2. **Plan shot lists** — Define specific scenes, compositions, and subjects for each theme.
3. **Generate images** — Create a batch of photos per theme with consistent quality.
4. **Add editorial variants** — Generate versions with negative space for text overlay.
5. **Organize and tag** — Categorize by theme, mood, color, and subject for easy retrieval.

## Related Skills

- [AI Photo Style Transfer](../ai-photo-style-transfer/SKILL.md) — Apply artistic styles to stock photos
- [AI HDR Enhancement](../ai-hdr-enhancement/SKILL.md) — Enhance dynamic range and detail
- [AI Photo Restoration](../ai-photo-restoration/SKILL.md) — Restore vintage-style photography
- [Text to Image](../../image/text-to-image/SKILL.md) — General-purpose image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic high-quality outputs
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Natural, authentic imagery
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid photo generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
