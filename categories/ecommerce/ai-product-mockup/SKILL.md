---
name: ai-product-mockup
description: "Generate product mockups on various surfaces and contexts using each::sense AI. Place products, packaging, labels, and branding on realistic mockup scenes including t-shirts, mugs, boxes, devices, and signage. Use for: brand presentations, client approvals, Etsy listings, print-on-demand previews, packaging mockups, pitch decks. Triggers: product mockup, mockup generator, packaging mockup, tshirt mockup, mug mockup, box mockup, label mockup, brand mockup, device mockup, mockup design"
allowed-tools: Bash(curl *), WebFetch
---

# AI Product Mockup

Generate realistic product mockups on various surfaces and in real-world contexts using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a product mockup: a kraft paper coffee bag with a minimalist mountain logo standing on a rustic wooden shelf next to a ceramic pour-over dripper and a small potted succulent. Warm morning light from the right, cozy coffee shop atmosphere, commercial mockup photography quality"
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
        "content": "Generate a product mockup: a kraft paper coffee bag with a minimalist mountain logo standing on a rustic wooden shelf next to a ceramic pour-over dripper and a small potted succulent. Warm morning light from the right, cozy coffee shop atmosphere, commercial mockup photography quality"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide your design or product to place into a mockup scene:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Place this product design onto a realistic mockup. Show the product on a clean marble countertop with soft studio lighting, lifestyle context props (a small plant and a glass of water), and a blurred modern kitchen background. Commercial mockup quality."},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-product-design.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Mockup Categories

| Category | Mockup Types | Use Case |
|----------|-------------|----------|
| **Apparel** | t-shirt, hoodie, hat, tote bag | print-on-demand, merch |
| **Drinkware** | mug, tumbler, water bottle, glass | print-on-demand, gifts |
| **Packaging** | box, bag, bottle, jar, tube, pouch | CPG brands, food/beverage |
| **Print** | business card, poster, book, magazine | branding, publishing |
| **Devices** | phone screen, laptop, tablet, monitor | app/web design |
| **Signage** | storefront sign, banner, billboard | retail, OOH advertising |
| **Stationery** | letterhead, envelope, notebook, pen | corporate branding |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a product mockup:" + [product description with design] + [surface/placement] + [scene context and props] + [lighting] + [atmosphere/mood] + [quality keywords]
```

### Surface and Placement Keywords

```
on a flat marble surface, hanging on a clothesline,
displayed on a retail shelf, held in a person's hand,
standing on a desk, mounted on a wall, placed on grass,
floating with soft shadow, arranged in a flat lay
```

### Scene Mood Keywords

```
clean and minimal, cozy and warm, rustic artisan,
modern corporate, outdoor adventure, luxury premium,
playful and colorful, dark and moody
```

## Examples

### T-Shirt Mockup

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a t-shirt mockup: a black crew-neck t-shirt with a large vintage-style retro sunset graphic on the front, displayed on an invisible mannequin form. Clean light grey background, soft studio lighting, slight wrinkle detail for realism, front view, print-on-demand listing quality."
      }
    ],
    "stream": false
  }'
```

### Candle Packaging Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a product mockup: a luxury soy candle in an amber glass jar with a minimal white label, sitting on a raw-edge wooden tray alongside dried pampas grass, a matchbox, and a linen napkin. Warm soft candlelight glow, dark moody background, shallow depth of field, premium lifestyle mockup photography."
      }
    ],
    "stream": false
  }'
```

### Mobile App on Device

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a device mockup: a modern smartphone displaying a fitness tracking app with green and dark UI elements on the screen. The phone is placed on a light wooden desk next to wireless earbuds, a smartwatch, and a water bottle. Morning light, clean modern aesthetic, tech product mockup quality."
      }
    ],
    "stream": false
  }'
```

### Book Cover Mockup

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a book mockup: a hardcover book with a dark navy cover and gold foil abstract design, standing upright on a walnut bookshelf. Two more copies stacked flat behind it. A reading lamp and small vintage clock as props. Warm golden library lighting, shallow depth of field, publisher marketing mockup quality."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Brand Touchpoints

```bash
BRAND="a minimalist skincare brand with clean white packaging, sans-serif typography, and sage green accent color"

MOCKUPS=(
  "a tube of face cream on a white marble bathroom shelf, morning light, clean minimal"
  "a serum bottle held in a woman's hand with a blurred spa background, natural lighting"
  "a gift set box with three products inside, displayed on a white bed with linen sheets, bright and airy"
  "the brand's shopping bag on a store counter with tissue paper peeking out, boutique atmosphere"
  "a flat lay of all products arranged symmetrically on a sage green background with botanical props, overhead shot"
)

for MOCKUP in "${MOCKUPS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a product mockup for $BRAND: $MOCKUP. Commercial mockup photography quality.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Text and logos on products** will not render accurately. AI struggles with specific words and fine typography. Use the mockup as a base and composite your real design in post.
- **Brand consistency** — AI generates different products each time. Describe the product identically for each mockup.
- **Unrealistic scale** — a product that is too large or small for the scene looks fake. Mention size relative to props.
- **Busy backgrounds** competing with the product — the product should always be the clear focal point.
- **Shadow and reflection mismatches** — specify light direction to keep shadows consistent with the scene.

## Related Skills

- [AI Product Photo](../ai-product-photo/SKILL.md) — Clean studio product shots
- [AI Lifestyle Photo](../ai-lifestyle-photo/SKILL.md) — Products in real-world settings
- [AI Product Video Ad](../ai-product-video-ad/SKILL.md) — Animated product showcases
- [AI Catalog Generator](../ai-catalog-generator/SKILL.md) — Full catalog imagery

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
