---
name: ai-recipe-visualization
description: "Visualize recipes and dishes using each::sense AI. Generate step-by-step cooking process images, ingredient layouts, finished dish presentations, and recipe card visuals. Create visual guides for cookbooks, food blogs, and cooking tutorials. Use for: recipe visualization, cooking steps, ingredient photos, cookbook images, recipe cards, cooking tutorials. Triggers: recipe visualization, recipe image, cooking visual, recipe card, ingredient layout, cooking steps, dish visualization, recipe photo, cooking guide, meal prep visual"
allowed-tools: Bash(curl *), WebFetch
---

# AI Recipe Visualization

Visualize recipes, cooking processes, and dish presentations using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A recipe visualization showing all ingredients for homemade pasta laid out in a flat lay: a mound of 00 flour with a well in the center, eggs, olive oil, salt, and a fork, all arranged on a rustic wooden cutting board, recipe card style, bright even lighting, cookbook photography"
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
        "content": "A recipe visualization showing all ingredients for homemade pasta laid out in a flat lay: a mound of 00 flour with a well in the center, eggs, olive oil, salt, and a fork, all arranged on a rustic wooden cutting board, recipe card style, bright even lighting, cookbook photography"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a recipe visualization showing what this finished dish looks like before cooking: display all the raw ingredients laid out in small prep bowls arranged neatly, mise en place style, matching the warm lighting and surface of the reference"},
              {"type": "image_url", "image_url": {"url": "https://example.com/finished-dish.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Recipe Visualization

- **List ingredients specifically** — name each ingredient and its form (diced, sliced, measured in a bowl).
- **Describe the arrangement** — "mise en place in small glass bowls," "scattered artfully," or "grid layout."
- **Show the cooking process** — describe specific stages like "dough being kneaded," "sauce simmering."
- **Include cooking tools** — wooden spoons, cast iron pans, mixing bowls for context.
- **Match the recipe mood** — rustic for comfort food, minimalist for modern cuisine, vibrant for tropical dishes.

## Examples

### Mise en Place

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A mise en place photograph for a Thai green curry recipe: small glass prep bowls arranged in a circle containing diced chicken, green curry paste, coconut milk in a measuring cup, sliced bell peppers, Thai basil leaves, fish sauce, palm sugar, and bamboo shoots, clean white marble surface, overhead view, cooking blog photography"
      }
    ],
    "stream": false
  }'
```

### Cooking Process Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A cooking process photograph: hands tossing pasta in a large stainless steel pan with garlic, olive oil, and fresh cherry tomatoes, steam rising, dynamic action shot, warm kitchen lighting, close-up angle showing the pasta mid-toss, authentic Italian cooking moment"
      }
    ],
    "stream": false
  }'
```

### Before and After Plating

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A side-by-side recipe visualization: on the left, raw marinated steak on a cutting board with fresh rosemary and garlic cloves; on the right, the same steak perfectly grilled with char marks, sliced and fanned out on a warm plate with roasted potatoes, consistent lighting and surface across both sides, cookbook tutorial style"
      }
    ],
    "stream": false
  }'
```

## Workflow: Recipe Content Creation

1. **Photograph ingredients** — Generate mise en place flat lay showing all ingredients.
2. **Visualize key steps** — Create images for critical cooking stages.
3. **Capture the finished dish** — Generate the hero presentation shot.
4. **Create serving scene** — Show the dish in a dining context with tableware.
5. **Assemble recipe card** — Combine step images with the final dish for a visual guide.

## Related Skills

- [AI Food Photography](../ai-food-photography/SKILL.md) — Professional dish photography
- [AI Menu Visualization](../ai-menu-visualization/SKILL.md) — Restaurant menu imagery
- [AI Stock Photo](../../photography/ai-stock-photo/SKILL.md) — General stock photography
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic food detail
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Appetizing visual styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick concept shots

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
