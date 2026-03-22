---
name: ai-outfit-generator
description: "Generate outfit combinations and styling suggestions using each::sense AI. Create complete looks from scratch or build around key pieces with color coordination, seasonal styling, and occasion-based recommendations. Use for: outfit inspiration, personal styling, wardrobe planning, fashion content creation, style guides. Triggers: outfit generator, outfit ideas, styling suggestions, ai stylist, wardrobe combinations, outfit creator, fashion combinations, mix and match, capsule wardrobe, what to wear"
allowed-tools: Bash(curl *), WebFetch
---

# AI Outfit Generator

Create complete outfit combinations and styling suggestions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a complete autumn casual outfit: layered look with earth tones, including outerwear, top, bottoms, shoes, and accessories. Flat lay arrangement on a wooden surface, styled fashion photography"
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
        "content": "Generate a complete autumn casual outfit: layered look with earth tones, including outerwear, top, bottoms, shoes, and accessories. Flat lay arrangement on a wooden surface, styled fashion photography"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Build an outfit around an existing garment:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a complete outfit built around this jacket. Show the full look on a model: matching pants or skirt, complementary shoes, and accessories. Street style photography, full body shot"
      }
    ],
    "image_urls": ["https://example.com/my-jacket.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Prompt Engineering Tips

### Prompt Structure

```
[occasion] + [season] + [style direction] + [color palette] + [garment list] + [presentation format] + [photography style]
```

### Occasion Keywords

| Occasion | Keywords |
|----------|----------|
| **Casual** | everyday, weekend, relaxed, off-duty, brunch |
| **Business** | office, business casual, smart casual, boardroom |
| **Formal** | black tie, gala, cocktail party, evening event |
| **Date Night** | dinner date, romantic, evening out, chic |
| **Travel** | airport, versatile, packable, comfortable |
| **Activewear** | gym, athleisure, hiking, yoga, running |

### Presentation Formats

```
flat lay on white background — clean e-commerce style
flat lay on textured surface — lifestyle editorial
on a model full body shot — shows fit and drape
outfit grid collage — each item separately displayed
mood board layout — includes color swatches and textures
```

## Examples

### Business Casual Monday

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a business casual outfit for a woman: tailored blazer in camel, white silk blouse, high-waisted navy trousers, pointed-toe nude heels, minimal gold jewelry. Shown on a model in a modern office lobby, natural lighting, three-quarter body shot, professional fashion photography"
      }
    ],
    "stream": false
  }'
```

### Summer Festival Look

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a summer music festival outfit for a man: linen camp-collar shirt in dusty pink, relaxed chino shorts in sand, woven leather sandals, straw bucket hat, round sunglasses. Flat lay arrangement on sun-bleached wood, overhead shot, styled fashion photography"
      }
    ],
    "stream": false
  }'
```

### Capsule Wardrobe Grid

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a minimalist capsule wardrobe grid showing 12 essential pieces: 3 tops (white tee, striped breton, black turtleneck), 3 bottoms (blue jeans, black trousers, khaki chinos), 2 outerwear (navy peacoat, beige trench coat), 2 shoes (white sneakers, brown chelsea boots), 2 accessories (leather belt, canvas tote). Each item in its own cell, clean white background, organized grid layout, catalog style photography"
      }
    ],
    "stream": false
  }'
```

## Styling Color Rules

- **Monochromatic** — shades of one color, add interest with textures and silhouettes
- **Complementary** — opposite on the color wheel (navy + burnt orange, olive + burgundy)
- **Analogous** — adjacent hues (camel, rust, terracotta for warm earth tones)
- **Neutral base + one accent** — safest formula (grey suit, white shirt, red tie)

## Batch Workflow: Outfit-of-the-Week

```bash
DAYS=("Monday:business casual, structured blazer and slacks" \
      "Tuesday:smart casual, knit polo and chinos" \
      "Wednesday:relaxed office, cable-knit sweater and tailored jeans" \
      "Thursday:client meeting, charcoal suit and white shirt" \
      "Friday:casual Friday, denim jacket and joggers")

for DAY_OUTFIT in "${DAYS[@]}"; do
  DAY="${DAY_OUTFIT%%:*}"
  DESC="${DAY_OUTFIT#*:}"
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate an outfit for $DAY: $DESC. Show on a male model, full body shot, clean background, commercial fashion photography\"}],
      \"stream\": false
    }"
  echo "--- $DAY ---"
done
```

## Common Pitfalls

- **Too many patterns** in one outfit creates visual noise. Stick to one patterned piece with solid companions.
- **Ignoring proportions** — oversized top pairs with slim bottom and vice versa.
- **Season mismatch** — specifying "wool coat" with "linen shorts" confuses the model.
- **Flat lay with too many items** — more than 8 pieces becomes cluttered. Keep flat lays focused.

## Related Skills

- [AI Fashion Model](../ai-fashion-model/SKILL.md) — Generate model imagery for outfits
- [AI Clothing Try-On](../ai-clothing-try-on/SKILL.md) — Try outfits on real photos
- [AI Fashion Lookbook](../ai-fashion-lookbook/SKILL.md) — Full lookbook layouts
- [AI Fabric Pattern](../ai-fabric-pattern/SKILL.md) — Custom textile patterns

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
