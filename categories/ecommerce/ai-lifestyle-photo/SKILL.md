---
name: ai-lifestyle-photo
description: "Generate lifestyle product photography using each::sense AI. Place products in authentic real-world settings showing them being used naturally by people in homes, offices, outdoors, and social situations. Builds emotional connection and shows context of use. Use for: brand storytelling, social media content, Shopify listings, advertising campaigns, influencer-style content. Triggers: lifestyle photo, lifestyle product, product in use, contextual photography, brand lifestyle, product scene, in situ product, lifestyle shot, product in context, use case photo"
allowed-tools: Bash(curl *), WebFetch
---

# AI Lifestyle Photo

Generate lifestyle product photography showing products in authentic real-world settings using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Lifestyle product photo: a woman sitting on a sunlit balcony in the morning, wearing a cozy cardigan, holding a handmade ceramic coffee mug with both hands. Warm golden morning light, plants in the background, relaxed and peaceful mood, shallow depth of field focused on the mug, candid natural photography style"
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
        "content": "Lifestyle product photo: a woman sitting on a sunlit balcony in the morning, wearing a cozy cardigan, holding a handmade ceramic coffee mug with both hands. Warm golden morning light, plants in the background, relaxed and peaceful mood, shallow depth of field focused on the mug, candid natural photography style"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide your actual product to generate lifestyle shots around it:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a lifestyle photo featuring this product. Place it on a bedside table in a cozy bedroom setting, next to a book and a small plant. Warm lamp light, evening relaxation mood, candid photography style, the product should be clearly visible but integrated naturally into the scene."},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-product.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Lifestyle Settings

| Setting | Mood | Product Types |
|---------|------|---------------|
| **Morning Kitchen** | warm, fresh, energized | food, beverages, appliances |
| **Living Room / Couch** | relaxed, cozy, comfortable | blankets, candles, books, tech |
| **Home Office / Desk** | productive, focused, organized | tech, stationery, accessories |
| **Outdoor / Nature** | adventurous, free, natural | fitness, outdoor gear, beverages |
| **Bathroom / Spa** | calm, luxurious, self-care | skincare, bath products, towels |
| **Dining Table** | social, warm, gathering | cookware, food, tableware |
| **Gym / Active** | energetic, powerful, driven | activewear, supplements, gadgets |
| **Travel / Airport** | sophisticated, mobile, worldly | luggage, accessories, tech |

## Prompt Engineering Tips

### Prompt Structure

```
"Lifestyle product photo:" + [person + action] + [product interaction] + [setting] + [lighting and mood] + [photography style] + [focus instruction]
```

### Product Visibility Balance

The product should be prominent but not feel staged:
```
"The product is clearly visible and in focus, but
integrated naturally into the scene — not awkwardly
centered or isolated."
```

### Emotional Mood Keywords

```
cozy and intimate, bright and energetic, calm and serene,
adventurous and bold, sophisticated and premium,
playful and joyful, warm and nostalgic
```

## Examples

### Skincare Routine

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Lifestyle product photo: a woman in a white bathrobe applying face serum from a glass dropper bottle in a bright modern bathroom. Mirror reflection visible, marble countertop with neatly arranged skincare bottles, morning sun through a frosted window, self-care ritual mood, editorial beauty photography, the serum bottle is the hero product in focus."
      }
    ],
    "stream": false
  }'
```

### Tech Product at Work

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Lifestyle product photo: a person at a clean minimalist desk wearing noise-cancelling headphones, typing on a laptop, with a cup of coffee nearby. Modern loft office with exposed brick and large windows, natural afternoon light, focused and productive atmosphere, the headphones are the hero product in sharp focus, shallow depth of field blurring the background."
      }
    ],
    "stream": false
  }'
```

### Outdoor Adventure Gear

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Lifestyle product photo: a hiker sitting on a rocky mountain ledge at sunrise, pouring water from an insulated steel water bottle into a camp cup. Backpack on the ground beside them, mountain panorama in the background, golden hour warm light, adventurous and aspirational mood, outdoor brand campaign photography, the water bottle is prominently visible."
      }
    ],
    "stream": false
  }'
```

### Food and Beverage

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Lifestyle product photo: friends gathered around a rustic farmhouse dining table, reaching for slices of artisan pizza. A bottle of premium olive oil sits prominently in the center of the table alongside fresh herbs and a wooden cutting board. Warm overhead pendant light, convivial social atmosphere, food photography with shallow depth of field, the olive oil bottle is the product in focus."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Product Across Contexts

```bash
PRODUCT="a compact wireless Bluetooth speaker in forest green with a fabric grille"

SCENES=(
  "on a kitchen counter while someone cooks in the background, morning light, domestic comfort"
  "on a beach towel at the seaside, sunglasses and a book nearby, bright summer daylight, vacation mood"
  "on a desk during a home office video call, laptop screen visible, focused work environment"
  "on a camping picnic blanket in a forest clearing, surrounded by snacks and lanterns, evening golden hour"
  "on a bathroom shelf beside rolled towels, steam in the air, relaxing spa-like atmosphere"
)

for SCENE in "${SCENES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Lifestyle product photo: $PRODUCT placed $SCENE. The speaker is clearly visible and in focus. Candid natural photography style, commercial quality.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Product gets lost in the scene** — always include a focus instruction ("the product is the hero, in sharp focus").
- **Too staged / unnatural** — avoid overly perfect symmetry and "advertising pose" language. Use "candid", "natural", "relaxed."
- **Wrong setting for the product** — a camping stove on a corporate desk breaks believability. Match setting to use case.
- **People dominating the frame** — the person should complement the scene, not overpower the product.
- **Text on product labels** renders poorly — describe the label design (colors, shapes) but do not expect readable text.

## Related Skills

- [AI Product Photo](../ai-product-photo/SKILL.md) — Clean studio product shots
- [AI Product Mockup](../ai-product-mockup/SKILL.md) — Products on mockup surfaces
- [AI Product Video Ad](../ai-product-video-ad/SKILL.md) — Video product showcases
- [AI Catalog Generator](../ai-catalog-generator/SKILL.md) — Full catalog imagery

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
