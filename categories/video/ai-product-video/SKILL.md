---
name: ai-product-video
description: "Create product showcase and demo videos using each::sense AI. Generate professional product reveal animations, 360-degree turntables, lifestyle context videos, and unboxing-style sequences. Supports clean studio shots, environmental placements, and dynamic product reveals. Use for: e-commerce product videos, Amazon listings, social media product ads, product launches, packaging reveals, feature highlights. Triggers: product video, product showcase, product demo, product animation, product reveal, e-commerce video, product ad, unboxing video, product commercial, product launch, product turntable"
allowed-tools: Bash(curl *), WebFetch
---

# AI Product Video

Create product showcase and demo videos using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a video: a premium wireless headphone floating in mid-air, slowly rotating 360 degrees. Clean white studio background, soft directional lighting highlighting the matte black finish and brushed metal accents. Subtle shadow beneath. Premium product commercial quality, smooth rotation."
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
        "content": "Generate a video: a premium wireless headphone floating in mid-air, slowly rotating 360 degrees. Clean white studio background, soft directional lighting highlighting the matte black finish and brushed metal accents. Subtle shadow beneath. Premium product commercial quality, smooth rotation."
    }]
)

print(response.choices[0].message.content)
```

### With Product Image

Animate an existing product photo into a video:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Turn this product photo into a premium video. The product slowly emerges from the bottom of frame, rises to center, and rotates gently. Studio lighting shifts to reveal different angles. Particles of light sparkle around it. Premium commercial quality."},
              {"type": "image_url", "image_url": {"url": "https://example.com/product-hero-shot.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Product Video Types

| Type | Description | Best For |
|------|-------------|----------|
| **360 Turntable** | Product rotates on a clean background | All products, e-commerce |
| **Hero Reveal** | Dramatic entrance with effects | Product launches, ads |
| **Lifestyle Context** | Product in a real-world setting | Social media, brand content |
| **Feature Callout** | Zoom into specific details | Tech products, features |
| **Unboxing Sequence** | Package opens to reveal product | Launch campaigns |
| **Comparison** | Side-by-side or morph between variants | Color options, sizes |

## Examples

### Skincare Product in Lifestyle Setting

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: a luxury skincare serum bottle on a marble bathroom counter, morning sunlight streaming through a frosted window, gentle steam from a shower visible in the background. Camera slowly dollies toward the product with subtle rack focus. Fresh green leaves and water droplets around the base. Premium beauty commercial aesthetic."
      }
    ],
    "stream": false
  }'
```

### Tech Product Launch

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: a new smartphone emerging from darkness. A beam of white light reveals the device edge-first, then rotates to show the full screen. The screen illuminates with a colorful abstract wallpaper. Reflections on the glass surface, Apple-style product reveal, dark background, dramatic lighting, premium tech commercial."
      }
    ],
    "stream": false
  }'
```

### Food Product

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: a craft chocolate bar being unwrapped in slow motion. Gold foil peels back to reveal dark chocolate with visible cocoa nibs. Steam-like wisps rise from the surface. Camera close-up, shallow depth of field, warm amber lighting, artisanal food photography style, decadent and luxurious."
      }
    ],
    "stream": false
  }'
```

### Multi-Variant Showcase

```bash
VARIANTS=(
  "Generate a video: a sneaker in midnight black colorway, rotating slowly on a minimalist pedestal, studio lighting, product commercial"
  "Generate a video: the same sneaker now in arctic white colorway, rotating slowly on a minimalist pedestal, studio lighting, product commercial"
  "Generate a video: the same sneaker now in forest green colorway, rotating slowly on a minimalist pedestal, studio lighting, product commercial"
)

for VARIANT in "${VARIANTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$VARIANT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Prompt Tips

- **Specify the product material and finish**: "matte black aluminum," "frosted glass," "brushed gold" — materials drive lighting
- **Camera movement sells products**: "slow orbit," "dolly push in," "rack focus" adds commercial feel
- **Match the environment to the brand**: Luxury products need marble and soft light; tech products need dark backgrounds and edge lighting
- **Mention "commercial quality"** to push toward polished, professional output
- **Keep backgrounds simple**: The product should be the star, not the environment

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — General video generation
- [AI Explainer Video](../ai-explainer-video/SKILL.md) — Product tutorial videos
- [Image to Video](../image-to-video/SKILL.md) — Animate product photos
- [AI Video Loop](../ai-video-loop/SKILL.md) — Looping product displays

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
