---
name: pinterest-pins
description: "Create Pinterest pin images optimized for discovery using each::sense AI. Generate tall vertical pin graphics (1000x1500) that stand out in Pinterest feeds and search results. Supports product pins, recipe pins, DIY tutorials, inspirational quotes, home decor, fashion lookbooks, and travel content. Use for: Pinterest pins, pin images, idea pins, product pins, recipe pins, DIY graphics, Pinterest visuals. Triggers: pinterest pin, pin image, pinterest graphic, idea pin, pinterest design, pin design, pinterest visual, tall pin, pinterest content, product pin, recipe pin, diy pin"
allowed-tools: Bash(curl *), WebFetch
---

# Pinterest Pins

Create Pinterest pin images optimized for discovery and engagement using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a Pinterest pin for a home decor inspiration board. A beautifully styled reading nook with a cozy armchair, knitted throw blanket, floor-to-ceiling bookshelves, warm afternoon light through a window, Scandinavian minimalist interior, warm neutrals with blush accents, vertical 2:3 format."
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
        "content": "Create a Pinterest pin for a home decor inspiration board. A beautifully styled reading nook with a cozy armchair, knitted throw blanket, floor-to-ceiling bookshelves, warm afternoon light through a window, Scandinavian minimalist interior, warm neutrals with blush accents, vertical 2:3 format."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match an existing pin style or board aesthetic:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a Pinterest pin in the same visual style as this reference. Match the color treatment and photography style, but feature a different room — a kitchen with the same cozy Scandinavian aesthetic, natural materials and plants, vertical 2:3 format."},
              {"type": "image_url", "image_url": {"url": "https://example.com/pin-reference.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Pinterest Pin Formats

| Format | Dimensions | Aspect Ratio | Use Case |
|--------|-----------|-------------|----------|
| **Standard Pin** | 1000 x 1500 px | 2:3 | Most common, best performing |
| **Long Pin** | 1000 x 2100 px | 1:2.1 | Step-by-step, lists |
| **Square Pin** | 1000 x 1000 px | 1:1 | Product showcase |
| **Idea Pin Slide** | 1080 x 1920 px | 9:16 | Multi-page stories |
| **Video Pin Cover** | 1000 x 1500 px | 2:3 | Video thumbnail |

## Prompt Engineering Tips

### Keywords That Work

```
Pinterest pin, aspirational lifestyle, beautifully styled, warm natural lighting,
editorial photography, vertical tall format, curated aesthetic, dreamy atmosphere,
inviting and inspiring, styled scene, muted warm tones, cozy and welcoming
```

### Keywords to Avoid

```
corporate professional — Pinterest is aspirational and lifestyle-focused
harsh flash lighting — natural and warm light performs best
cluttered messy scenes — Pinterest rewards curated, styled visuals
cold sterile environments — warmth drives saves and repins
```

### Prompt Structure

```
Pinterest pin for [topic/niche], [scene description], [styling details], [lighting], [color palette], [mood], vertical 2:3 format
```

## Examples

### Recipe Pin

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a Pinterest recipe pin image. Overhead flat lay of a rustic wooden cutting board with a freshly baked sourdough loaf, scattered flour, a bread knife, and a small pot of honey, linen napkin, warm morning window light, food photography style, earthy tones, vertical 2:3 format."
      }
    ],
    "stream": false
  }'
```

### Fashion Outfit Pin

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a Pinterest fashion pin. A carefully arranged autumn outfit flat lay on white bedding: camel wool coat, cream knit sweater, dark jeans, leather ankle boots, a crossbody bag, and gold jewelry. Soft diffused natural light, editorial styling, warm muted tones, vertical 2:3 format."
      }
    ],
    "stream": false
  }'
```

### DIY Craft Pin

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a Pinterest DIY craft pin. Hands holding a handmade macrame plant hanger with a trailing pothos plant, boho workspace in the background with craft supplies neatly arranged, warm golden hour side light, artisan creative mood, earthy greens and natural cotton tones, vertical 2:3."
      }
    ],
    "stream": false
  }'
```

### Travel Destination Pin

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a Pinterest travel pin. A picturesque cobblestone street in Santorini with white and blue buildings, bougainvillea cascading over a doorway, the Aegean Sea visible in the distance, golden hour glow, dreamy and wanderlust-inducing travel photography, vertical 2:3 format."
      }
    ],
    "stream": false
  }'
```

## Pinterest SEO and Discovery Tips

- **Warm, bright images** get 20% more repins than dark images
- **Vertical 2:3 ratio** takes up maximum feed real estate and gets the best engagement
- **Lifestyle context** — show products in use, not isolated on white backgrounds
- **Seasonal content** — pin seasonal content 45 days before the season starts
- **Multiple pins per piece** — create 3-5 different pin designs linking to the same content
- **Text overlay space** — leaving room for a title overlay increases click-through rate

## Top Pinterest Categories

| Category | Style Notes |
|----------|------------|
| **Home Decor** | Warm, styled interiors, natural light |
| **Recipes & Food** | Overhead flat lays, rustic surfaces |
| **Fashion** | Outfit flat lays, styled details |
| **DIY & Crafts** | Process shots, finished projects |
| **Travel** | Scenic destinations, golden hour |
| **Weddings** | Soft, romantic, detail shots |
| **Beauty** | Clean product arrangements, soft tones |

## Workflow

```bash
# Step 1: Generate the hero pin
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Pinterest pin for a self-care routine. A styled bathroom shelf with neatly arranged skincare products, a small eucalyptus bundle, white marble surface, soft bathroom light, spa-like serene atmosphere, clean and minimal, vertical 2:3."
      }
    ],
    "stream": false
  }'

# Step 2: Create a variation for the same content
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Pinterest pin for a self-care routine. A styled bathroom shelf with neatly arranged skincare products, a small eucalyptus bundle, white marble surface, soft bathroom light, spa-like serene atmosphere, clean and minimal, vertical 2:3."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Create a different angle of the same concept. Close-up of hands applying face cream from a small glass jar, the same marble surface and eucalyptus visible in the soft background, same lighting and color palette, vertical 2:3."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Instagram Content](../instagram-content/SKILL.md) — Instagram posts and stories
- [Infographic Design](../../design/infographic-design/SKILL.md) — Data-driven tall pin graphics
- [Social Media Post](../../design/social-media-post/SKILL.md) — General social graphics
- [Book Cover Design](../../design/book-cover-design/SKILL.md) — Vertical visual design

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
