---
name: ai-abstract-art
description: "Generate abstract digital artwork using each::sense AI. Create non-representational compositions with bold colors, dynamic shapes, textures, and expressive brushwork. Produce gallery-quality abstract pieces in styles from minimalist to maximalist, geometric to organic. Use for: abstract art, digital paintings, gallery art, wall art, expressive art, contemporary art. Triggers: abstract art, abstract painting, digital abstract, contemporary art, non-representational art, abstract expressionism, color field, geometric abstract, minimalist art, modern art"
allowed-tools: Bash(curl *), WebFetch
---

# AI Abstract Art Generator

Generate abstract digital artwork and contemporary compositions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create an abstract expressionist painting: bold sweeping brushstrokes of cadmium red and ultramarine blue colliding across the canvas, thick impasto texture, splashes of gold and white, raw emotional energy, large scale gallery piece, inspired by the gestural abstraction movement"
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
        "content": "Create an abstract expressionist painting: bold sweeping brushstrokes of cadmium red and ultramarine blue colliding across the canvas, thick impasto texture, splashes of gold and white, raw emotional energy, large scale gallery piece, inspired by the gestural abstraction movement"
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
              {"type": "text", "text": "Create an abstract interpretation inspired by the color palette and energy of this reference image, transform it into a fully non-representational composition with flowing organic forms and layered transparent color fields"},
              {"type": "image_url", "image_url": {"url": "https://example.com/color-reference.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Abstract Art Generation

- **Describe texture and medium** — "oil paint," "acrylic pour," "watercolor bleed," "digital glitch," "ink wash."
- **Reference art movements** — Abstract Expressionism, Color Field, Suprematism, De Stijl, Lyrical Abstraction.
- **Focus on mood and energy** — "serene and meditative," "chaotic and explosive," "contemplative and quiet."
- **Specify color relationships** — complementary, analogous, monochromatic, or high contrast.
- **Describe composition dynamics** — "centered vortex," "diagonal tension," "floating forms," "layered depth."

## Examples

### Color Field Painting

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A color field abstract painting: large soft-edged rectangles of deep burgundy and burnt orange floating on a warm ochre background, subtle color bleeding at the boundaries, meditative and warm, Rothko-inspired luminous depth, oil on canvas texture"
      }
    ],
    "stream": false
  }'
```

### Geometric Abstraction

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A geometric abstract composition: overlapping translucent circles, triangles, and rectangles in primary colors — red, blue, and yellow — with black outlines and white negative space, Bauhaus-inspired, clean hard edges, balanced asymmetric layout, modern graphic art"
      }
    ],
    "stream": false
  }'
```

### Organic Abstract

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An organic abstract artwork: flowing biomorphic shapes in moss green and sage, interlocking amoeba-like forms with delicate tendrils, subtle texture like handmade paper, earthy natural palette with touches of terracotta, calm and grounded, contemporary art gallery quality"
      }
    ],
    "stream": false
  }'
```

### Minimalist Abstract

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A minimalist abstract piece: a single bold black brushstroke sweeping diagonally across a pure white canvas, zen calligraphy energy, negative space as the dominant element, ink on paper texture, Japanese-inspired simplicity, museum-quality contemporary art"
      }
    ],
    "stream": false
  }'
```

## Workflow: Abstract Art Series

1. **Choose the aesthetic direction** — Gestural, geometric, color field, organic, or minimalist.
2. **Define the palette** — Select a cohesive color strategy for the series.
3. **Generate the anchor piece** — Create the primary work that sets the tone.
4. **Create variations** — Shift colors, scale, and composition for series cohesion.
5. **Curate the collection** — Select pieces that work together for exhibition or NFT drops.

## Related Skills

- [AI Generative Art](../ai-generative-art/SKILL.md) — Algorithmic and mathematical art
- [AI NFT Collection](../ai-nft-collection/SKILL.md) — NFT collection generation
- [AI Pixel Art](../ai-pixel-art/SKILL.md) — Retro pixel-based art
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Gallery-quality high-resolution art
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Expressive artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick style exploration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
