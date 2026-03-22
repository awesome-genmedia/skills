---
name: packaging-design
description: "Design product packaging and label art using each::sense AI. Generate compelling packaging visuals for consumer products, food and beverage labels, cosmetics packaging, subscription boxes, retail packaging, and specialty product containers. Supports various styles from minimal to ornate across all product categories. Use for: product packaging, label design, box design, bottle labels, food packaging, cosmetics packaging, subscription box art, retail packaging. Triggers: packaging design, product packaging, label design, box design, bottle label, food label, cosmetic packaging, package art, retail packaging, subscription box, product label, wrapper design"
allowed-tools: Bash(curl *), WebFetch
---

# Packaging Design

Design compelling product packaging and label art using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a premium coffee bag packaging illustration. A detailed mountain landscape at sunrise with coffee plants in the foreground, hand-drawn engraving style, rich brown and copper ink tones on cream background, vintage artisanal aesthetic, suitable for wrapping around a 12oz bag."
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
        "content": "Design a premium coffee bag packaging illustration. A detailed mountain landscape at sunrise with coffee plants in the foreground, hand-drawn engraving style, rich brown and copper ink tones on cream background, vintage artisanal aesthetic, suitable for wrapping around a 12oz bag."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide existing packaging or brand assets for consistency:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Design new packaging art that extends this brand's visual language. Match the illustration style and color palette, but create a new variation featuring different botanical elements for a new product line. Suitable for a rectangular box panel."},
              {"type": "image_url", "image_url": {"url": "https://example.com/existing-packaging.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Packaging Categories

| Category | Common Formats | Design Focus |
|----------|---------------|-------------|
| **Food & Beverage** | Bags, boxes, cans, bottles | Appetite appeal, freshness |
| **Cosmetics & Beauty** | Jars, tubes, boxes | Elegance, luxury |
| **Health & Supplements** | Bottles, pouches, boxes | Trust, clean ingredients |
| **Craft & Artisanal** | Bags, wraps, labels | Handmade, authentic |
| **Tech & Electronics** | Boxes, sleeves | Premium, minimal |
| **Subscription Boxes** | Mailer boxes | Unboxing experience |
| **Spirits & Wine** | Bottles, labels | Heritage, sophistication |

## Prompt Engineering Tips

### Keywords That Work

```
packaging illustration, product label art, premium surface design,
artisanal hand-drawn, botanical illustration, pattern tile, wrap-around art,
shelf-ready design, brand-consistent, high detail illustration, print-ready
```

### Keywords to Avoid

```
product name and text — add typography in design software
3D mockup rendering — generate flat art, mockup separately
blurry or soft backgrounds — packaging needs crisp detail
generic clip art style — packaging must feel unique and premium
```

### Prompt Structure

```
packaging [art/illustration/pattern] for [product type], [visual subject], [artistic style], [color palette], [mood/brand feel], suitable for [packaging format]
```

## Examples

### Craft Beer Label

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a craft beer label illustration. A majestic grizzly bear standing in a mountain stream, detailed line art with limited color fills in forest green and amber, Pacific Northwest aesthetic, rugged and adventurous, illustration suitable for a 12oz bottle label."
      }
    ],
    "stream": false
  }'
```

### Skincare Product Box

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create packaging art for a luxury skincare line. Delicate botanical watercolor illustrations of chamomile flowers and eucalyptus leaves, soft blush pink and sage green on white background, refined and spa-like, seamless pattern suitable for wrapping around a product box."
      }
    ],
    "stream": false
  }'
```

### Chocolate Box

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design artisan chocolate box packaging art. Rich dark brown background with elegant gold filigree patterns and illustrated cocoa pods with leaves, baroque luxury style, deep chocolate tones with metallic gold highlights, pattern suitable for a gift box lid."
      }
    ],
    "stream": false
  }'
```

### Tea Tin Design

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create packaging illustration for a Japanese green tea tin. Serene mountain landscape with terraced tea fields, traditional Japanese woodblock print style, limited palette of indigo blue and matcha green on off-white, tranquil and authentic, wrap-around illustration for a cylindrical tin."
      }
    ],
    "stream": false
  }'
```

## Packaging Design Considerations

- **Wrap-around artwork** — design with edges that can seamlessly connect
- **Color consistency** — specify exact colors; CMYK printing may shift tones
- **Scalability** — the art should look good on both small labels and large boxes
- **Shelf impact** — packaging competes with dozens of products at eye level
- **Die-cut awareness** — consider how the flat art maps onto the 3D package
- **Regulatory space** — leave areas for nutrition facts, barcodes, and legal text

## Workflow

```bash
# Step 1: Generate the primary packaging illustration
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Packaging illustration for an organic honey jar label. A detailed illustration of a beehive in a wildflower meadow, golden hour lighting, hand-drawn botanical illustration style, warm honey gold and soft green palette, circular composition suitable for a round label."
      }
    ],
    "stream": false
  }'

# Step 2: Create a matching pattern for the gift box
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Packaging illustration for an organic honey jar label. A detailed illustration of a beehive in a wildflower meadow, golden hour lighting, hand-drawn botanical illustration style, warm honey gold and soft green palette, circular composition suitable for a round label."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create a repeating pattern using the wildflower and bee elements from this illustration. Same color palette and hand-drawn style, but as a seamless tile pattern suitable for wrapping a gift box. Smaller scale, more abstract."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Logo Design](../logo-design/SKILL.md) — Brand logos for packaging
- [Menu Design](../menu-design/SKILL.md) — Restaurant and food branding
- [Social Media Post](../social-media-post/SKILL.md) — Product launch promotion
- [Book Cover Design](../book-cover-design/SKILL.md) — Illustrated cover art techniques

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
