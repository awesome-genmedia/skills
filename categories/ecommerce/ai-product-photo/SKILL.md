---
name: ai-product-photo
description: "Generate professional product photography using each::sense AI. Create studio-quality product shots with perfect lighting, backgrounds, and compositions for e-commerce listings, catalogs, and marketing materials. Supports white background, lifestyle, hero shots, and detail close-ups. Use for: e-commerce listings, Amazon product photos, catalog photography, product marketing, web store images. Triggers: product photo, product photography, ecommerce photo, product shot, studio product photo, white background product, catalog photo, product image, commercial photography, packshot"
allowed-tools: Bash(curl *), WebFetch
---

# AI Product Photo

Generate professional product photography for e-commerce and marketing using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Professional product photo of a matte black ceramic coffee mug on a pure white background. Studio lighting with soft shadow underneath, sharp focus, center frame, commercial product photography, clean and minimal, suitable for e-commerce listing"
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
        "content": "Professional product photo of a matte black ceramic coffee mug on a pure white background. Studio lighting with soft shadow underneath, sharp focus, center frame, commercial product photography, clean and minimal, suitable for e-commerce listing"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide your actual product photo to generate improved or alternative shots:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Take this product and create a professional studio product photo. Place it on a clean white background with perfect studio lighting, soft shadows, and sharp focus. E-commerce ready, high resolution quality."
      }
    ],
    "image_urls": ["https://example.com/my-product.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Shot Types for E-commerce

| Shot | Description | Platform Requirement |
|------|-------------|---------------------|
| **Hero / Main** | front-facing, white background, full product | Amazon main image, all platforms |
| **Angle Shot** | three-quarter view showing depth | secondary listing image |
| **Detail Close-Up** | macro on texture, material, or feature | feature highlight |
| **Scale Shot** | product next to common object for size | size communication |
| **Group / Bundle** | multiple products or variants together | bundle listings |
| **In-Use / Lifestyle** | product being used naturally | lifestyle gallery |
| **Flat Lay** | top-down arrangement with props | social media, Pinterest |

## Prompt Engineering Tips

### Prompt Structure

```
"Professional product photo of [product description]" + [background] + [lighting] + [composition] + [camera details] + [quality keywords]
```

### Background Keywords

```
pure white background (Amazon requirement),
light grey seamless, dark moody background,
marble surface, wooden tabletop, concrete surface,
gradient background, colored backdrop
```

### Lighting Setups

```
soft studio lighting with diffused shadows,
dramatic side lighting with hard shadow,
backlit with rim light, overhead flat lighting,
natural window light from the left,
product photography three-point lighting
```

## Examples

### White Background E-commerce (Amazon-Ready)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Professional product photo of a pair of wireless over-ear headphones in matte white with rose gold accents. Pure white background, product fills 85% of the frame, soft even studio lighting, tiny contact shadow underneath, three-quarter angle showing the ear cup and headband, sharp focus throughout, commercial product photography, Amazon listing quality."
      }
    ],
    "stream": false
  }'
```

### Hero Shot with Dramatic Lighting

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Hero product photo of a luxury men's wristwatch with a dark blue dial, silver case, and brown leather strap. The watch sits on a dark slate surface, dramatic side lighting from the left creating specular highlights on the polished case, deep shadows on the right. Shallow depth of field, close-up, premium advertising photography."
      }
    ],
    "stream": false
  }'
```

### Skincare Flat Lay

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Flat lay product photography of a skincare routine: a glass bottle of serum, a white tube of moisturizer, and a round tin of balm arranged on a marble surface with fresh eucalyptus sprigs and a cotton towel as props. Overhead view, soft natural light, clean minimal aesthetic, editorial beauty photography, pastel tones."
      }
    ],
    "stream": false
  }'
```

### Food Product Packaging

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Professional product photo of a jar of artisanal honey with a cork lid and a rustic kraft paper label. Placed on a weathered wooden surface with a honey dipper, scattered honeycomb pieces, and dried lavender sprigs. Warm golden backlight suggesting sunlight, shallow depth of field, gourmet food photography."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Multi-Angle Product Shoot

```bash
PRODUCT="a sleek stainless steel water bottle with a bamboo cap, 750ml, brushed metal finish"

SHOTS=(
  "front view on pure white background, centered, product fills 85% frame, soft studio lighting, e-commerce main image"
  "three-quarter angle on white background showing the cap detail and bottle curve, studio lighting, secondary listing image"
  "close-up detail shot of the bamboo cap texture and logo area, shallow depth of field, macro product photography"
  "the bottle on a gym bench next to a towel and dumbbells, lifestyle context, natural indoor lighting"
  "overhead flat lay: the bottle with its packaging box, user manual card, and cleaning brush laid out neatly, unboxing arrangement"
)

for SHOT in "${SHOTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Professional product photo of $PRODUCT. $SHOT.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Amazon Image Requirements Checklist

- Main image: pure white background (RGB 255,255,255)
- Product fills 85% or more of the image frame
- No text, logos, watermarks, or borders
- No accessories not included in purchase
- Sharp, well-lit, realistic color representation

## Common Pitfalls

- **Text and logos on products** render poorly. Describe shape, color, and position of labels but do not rely on specific words appearing correctly.
- **Reflective products** (glass, chrome, jewelry) need careful lighting descriptions to avoid blown highlights.
- **White product on white background** — add "subtle shadow" or "slight gradient" so the product does not disappear.
- **Multiple products** of different sizes in one shot — specify relative positioning and scale.
- **Color accuracy** — describe exact colors (e.g., "Pantone coral 16-1546" or "hex #2C3E50") when precision matters.

## Related Skills

- [AI Product Mockup](../ai-product-mockup/SKILL.md) — Products on mockup surfaces
- [AI Lifestyle Photo](../ai-lifestyle-photo/SKILL.md) — Products in lifestyle settings
- [AI Product Video Ad](../ai-product-video-ad/SKILL.md) — Video product showcases
- [AI Catalog Generator](../ai-catalog-generator/SKILL.md) — Full catalog imagery

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
