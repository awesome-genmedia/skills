---
name: ai-food-photography
description: "Generate professional food photography using each::sense AI. Create appetizing, restaurant-quality images of dishes, ingredients, beverages, and culinary scenes. Supports overhead flat lays, 45-degree angles, close-up macro shots, and lifestyle dining scenes. Use for: food photography, restaurant menus, food blogs, cookbook visuals, food marketing. Triggers: food photography, food photo, dish photo, restaurant photography, culinary photo, food styling, food shot, meal photo, plate photo, food image"
allowed-tools: Bash(curl *), WebFetch
---

# AI Food Photography Generator

Generate professional, appetizing food photography for menus, blogs, and marketing using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A professional food photograph of a perfectly seared salmon fillet on a bed of wild rice with roasted asparagus and a drizzle of lemon butter sauce, ceramic plate on a dark slate surface, soft side lighting with gentle shadows, shallow depth of field, restaurant-quality plating, editorial food photography"
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
        "content": "A professional food photograph of a perfectly seared salmon fillet on a bed of wild rice with roasted asparagus and a drizzle of lemon butter sauce, ceramic plate on a dark slate surface, soft side lighting with gentle shadows, shallow depth of field, restaurant-quality plating, editorial food photography"
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
              {"type": "text", "text": "Create a professional food photograph in the same style and lighting as this reference: match the color temperature, depth of field, and surface texture, but feature a different dish — a bowl of ramen with a soft-boiled egg, nori, and green onions"},
              {"type": "image_url", "image_url": {"url": "https://example.com/food-style-reference.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Food Photography

- **Describe the plating** — arrangement, garnishes, sauces, and plate style.
- **Specify the angle** — "overhead flat lay," "45-degree angle," "eye level," or "close-up macro."
- **Include the surface** — marble, wood, slate, linen, rustic table.
- **Define the lighting** — "soft natural window light," "moody side lighting," "bright and airy."
- **Add props** — utensils, napkins, herbs, ingredients, glasses for a styled scene.
- **Mention texture** — "crispy crust," "glistening glaze," "steam rising" for appetite appeal.

## Examples

### Overhead Flat Lay

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An overhead flat lay food photograph of a full breakfast spread: avocado toast with poached eggs, a bowl of fresh berries, a cup of latte with art, fresh orange juice, and a croissant, all arranged on a white marble surface with linen napkins and small potted herbs, bright natural morning light, food blog aesthetic"
      }
    ],
    "stream": false
  }'
```

### Dessert Close-Up

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A dramatic close-up food photograph of a chocolate lava cake being cut open, molten chocolate flowing out onto the white plate, a dusting of powdered sugar, a single mint leaf, dark moody background with a single warm spotlight, macro detail showing the cake texture, fine dining dessert photography"
      }
    ],
    "stream": false
  }'
```

### Beverage Photography

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A professional beverage photograph of a craft cocktail: a copper Moscow mule mug with condensation droplets, fresh lime wedge and mint sprig garnish, crushed ice visible at the top, dark bar counter background with warm ambient bokeh lights, commercial beverage photography"
      }
    ],
    "stream": false
  }'
```

## Workflow: Food Photography Production

1. **Plan the dish and composition** — Choose the dish, angle, and styling approach.
2. **Generate the hero shot** — Create the primary food image.
3. **Create angle variants** — Overhead, 45-degree, and close-up for different placements.
4. **Add lifestyle context** — Generate dining scene versions with hands, settings, and ambiance.
5. **Batch for the menu** — Generate matching-style images for all menu items.

## Related Skills

- [AI Recipe Visualization](../ai-recipe-visualization/SKILL.md) — Visualize recipes and cooking steps
- [AI Menu Visualization](../ai-menu-visualization/SKILL.md) — Menu item imagery for restaurants
- [AI Stock Photo](../../photography/ai-stock-photo/SKILL.md) — General stock photography
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic food detail
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Appetizing visual styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick concept shots

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
