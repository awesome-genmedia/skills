---
name: ai-catalog-generator
description: "Generate e-commerce catalog imagery using each::sense AI. Create consistent product photo sets for online stores, print catalogs, and wholesale lookbooks with matching style, lighting, and composition across an entire product line. Use for: e-commerce catalog, Shopify store images, wholesale lookbooks, product line photography, category pages, seasonal catalog. Triggers: catalog generator, product catalog, ecommerce catalog, catalog photography, product line photos, store imagery, wholesale catalog, product collection, catalog layout, category images"
allowed-tools: Bash(curl *), WebFetch
---

# AI Catalog Generator

Generate consistent e-commerce catalog imagery across entire product lines using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "E-commerce catalog photo: a navy blue backpack with tan leather straps and brass buckles, front view on a pure white background, product centered filling 85% of the frame, soft studio lighting with minimal shadow, sharp focus, consistent e-commerce catalog style, product photography"
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
        "content": "E-commerce catalog photo: a navy blue backpack with tan leather straps and brass buckles, front view on a pure white background, product centered filling 85% of the frame, soft studio lighting with minimal shadow, sharp focus, consistent e-commerce catalog style, product photography"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a product photo to generate additional catalog angles:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an e-commerce catalog photo of this product from a different angle. Show a three-quarter view from the left side. Match the same white background, lighting style, and product framing as a professional e-commerce catalog. Consistent with standard catalog photography."
      }
    ],
    "image_urls": ["https://example.com/product-front.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Catalog Image Types

| Type | Purpose | Description |
|------|---------|-------------|
| **Main / Hero** | primary listing image | front view, white background, product fills frame |
| **Alternate Angle** | secondary views | side, back, three-quarter, top-down |
| **Detail / Close-Up** | feature highlights | zoom on texture, hardware, stitching |
| **Color Variants** | show available colors | same angle, different product colors |
| **Scale / Size** | size communication | product next to a common reference object |
| **Group / Collection** | category overview | multiple products arranged together |
| **Lifestyle Context** | emotional connection | product in use or styled setting |

## Consistency Framework

For a professional catalog, every image must share:

| Element | Keep Consistent |
|---------|----------------|
| **Background** | same color and gradient (or pure white) |
| **Lighting** | same setup: direction, intensity, softness |
| **Camera Angle** | same default angle across products |
| **Framing** | same product-to-frame ratio (e.g., 85%) |
| **Shadow** | same shadow type: drop, contact, or none |
| **Color Grading** | same warmth, saturation, contrast |

## Prompt Engineering Tips

### Template Prompt (Reuse for Consistency)

Create a base prompt and swap only the product description:

```
"E-commerce catalog photo: [PRODUCT DESCRIPTION], [ANGLE] on a pure white background, product centered filling 85% of the frame, soft studio lighting with minimal contact shadow, sharp focus throughout, consistent e-commerce catalog photography style."
```

### Angle Specifications

```
front view — straight-on from the front
back view — straight-on from the back
left side profile — 90 degrees left
right three-quarter — 45 degrees from right
top-down — directly overhead
low angle — slightly below eye level looking up
```

## Examples

### Footwear Collection

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "E-commerce catalog photo: a men's brown leather oxford dress shoe with brogue detailing and a Goodyear welt sole. Right shoe only, three-quarter front-right angle on a pure white background. Product centered, fills 80% of the frame, soft studio lighting from the upper left, subtle contact shadow, sharp focus. Clean consistent catalog photography."
      }
    ],
    "stream": false
  }'
```

### Kitchenware Detail Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "E-commerce catalog detail photo: close-up of a chef knife blade showing the Damascus steel wave pattern, the edge bevel, and the bolster where blade meets the pakkawood handle. Shallow depth of field, soft studio lighting emphasizing the steel texture, white background, professional catalog photography."
      }
    ],
    "stream": false
  }'
```

### Color Variant Grid

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "E-commerce catalog photo showing 4 color variants of a canvas tote bag arranged in a 2x2 grid: top-left in natural cream, top-right in olive green, bottom-left in dusty rose, bottom-right in navy blue. Each bag shown at the same angle (front view), same size, white background, soft studio lighting. Consistent catalog photography style across all four."
      }
    ],
    "stream": false
  }'
```

### Collection Overview

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "E-commerce catalog collection photo: a complete men's grooming kit arranged as a styled flat lay on a dark charcoal background. Items: a safety razor, shaving brush, tin of shaving soap, aftershave bottle, and a leather dopp kit. Neatly arranged with equal spacing, overhead view, warm directional lighting from the top-left, premium brand catalog aesthetic."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Full Product Line Catalog

```bash
STYLE="pure white background, product centered filling 85% of frame, soft studio lighting with minimal contact shadow, sharp focus, consistent e-commerce catalog photography"

PRODUCTS=(
  "a stainless steel insulated water bottle in arctic white, 750ml, front view"
  "a stainless steel insulated water bottle in midnight black, 750ml, front view"
  "a stainless steel insulated water bottle in sage green, 750ml, front view"
  "a stainless steel insulated water bottle in coral pink, 750ml, front view"
  "a stainless steel insulated water bottle in arctic white, 750ml, three-quarter right view showing the cap and spout"
  "a stainless steel insulated water bottle in arctic white, 750ml, close-up detail of the vacuum lid mechanism"
)

for PRODUCT in "${PRODUCTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"E-commerce catalog photo: $PRODUCT. $STYLE.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Catalog Planning Checklist

For each product in your catalog, generate:

1. **Main image** — front view, white background (required for all platforms)
2. **Alternate angle** — three-quarter or side view (shows depth/shape)
3. **Detail close-up** — material, craftsmanship, or key feature
4. **Scale reference** — optional, product next to common object
5. **Lifestyle shot** — product in use or styled context
6. **Color variants** — one shot per available color (same angle)

## Common Pitfalls

- **Inconsistent lighting** across products — use the exact same lighting description in every prompt.
- **Product size varies** across images — always specify "product fills 85% of the frame" (or your target ratio).
- **Background color shifts** — "white background" can vary slightly. Specify "pure white (RGB 255,255,255)" for strict consistency.
- **Text and brand names** on labels will render incorrectly. Plan to composite labels in post or accept generic placeholder designs.
- **Too many products in one grid** — more than 4-6 items per composite image reduces quality per product.
- **Mixed angles** across a product line — use the same default angle for all main images.

## Related Skills

- [AI Product Photo](../ai-product-photo/SKILL.md) — Individual studio product shots
- [AI Product Mockup](../ai-product-mockup/SKILL.md) — Products on mockup surfaces
- [AI Lifestyle Photo](../ai-lifestyle-photo/SKILL.md) — Products in real settings
- [AI Product Video Ad](../ai-product-video-ad/SKILL.md) — Video product showcases

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
