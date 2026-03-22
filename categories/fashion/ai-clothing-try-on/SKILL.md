---
name: ai-clothing-try-on
description: "Virtual clothing try-on using each::sense AI. Upload a photo of a person and a garment to see how the clothing looks on them. Supports dresses, tops, pants, jackets, and accessories with realistic draping and fit. Use for: online shopping preview, fashion retail, personal styling, e-commerce conversion, social media try-on. Triggers: virtual try on, clothing try on, try on clothes, ai fitting room, virtual fitting, dress try on, outfit try on, wear clothes virtually, digital fitting, ai wardrobe"
allowed-tools: Bash(curl *), WebFetch
---

# AI Clothing Try-On

Virtually try clothes on photos of real people using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": [
              {"type": "text", "text": "Put the clothing from the second image onto the person in the first image. Keep the person identity, pose, and background the same. Realistic fit and natural fabric draping."},
              {"type": "image_url", "image_url": {"url": "https://example.com/person-photo.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/garment-photo.jpg"}}
            ]
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
        "content": "Put the clothing from the second image onto the person in the first image. Keep the person identity, pose, and background the same. Realistic fit and natural fabric draping."
    }],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### With Reference Image

This skill is inherently image-driven. Always provide at least one image (the person), and optionally a second image (the garment):

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Dress the person in the first image in a classic black leather biker jacket over a white t-shirt with slim dark jeans. Maintain the original pose and face. Photorealistic result."},
              {"type": "image_url", "image_url": {"url": "https://example.com/person-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Best Practices for Input Photos

### Person Photo

- **Clear, well-lit** front-facing or three-quarter pose
- **Full body or half body** depending on garment type (full body for dresses/pants, half body for tops)
- **Simple background** improves results; busy backgrounds may interfere
- **Neutral pose** with arms at sides gives the cleanest try-on

### Garment Photo

- **Flat lay or mannequin** shots work best
- **Clean background** (white preferred)
- **Single garment** per image, no styling accessories unless you want them included
- **Good lighting** showing fabric texture and color accurately

## Examples

### Dress Try-On with Two Images

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Put this red silk midi dress from the second image onto the woman in the first image. Preserve her face, hairstyle, and the outdoor park background. Natural draping, realistic shadows."},
              {"type": "image_url", "image_url": {"url": "https://example.com/woman-standing-park.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/red-silk-dress-flatlay.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Text-Described Outfit on Person

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Change the outfit on the person in this image to a navy pinstripe three-piece suit with a crisp white shirt and burgundy silk tie. Keep the face, hair, and background identical. Professional photo quality."},
              {"type": "image_url", "image_url": {"url": "https://example.com/man-office.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Jacket Try-On

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Put the denim jacket from the second image onto the person in the first image. Keep everything else the same: face, pose, pants, shoes, background. Only replace the upper body outerwear."},
              {"type": "image_url", "image_url": {"url": "https://example.com/person-casual.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/denim-jacket.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## E-commerce Integration Workflow

```bash
# Try multiple garments on the same person photo
PERSON="https://example.com/model-photo.jpg"
GARMENTS=(
  "https://example.com/product-001-blouse.jpg"
  "https://example.com/product-002-jacket.jpg"
  "https://example.com/product-003-dress.jpg"
)

for GARMENT in "${GARMENTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Put the garment from the second image onto the person in the first image. Preserve identity, pose, and background. Realistic fabric draping, e-commerce quality.\"}],
      \"image_urls\": [\"$PERSON\", \"$GARMENT\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Arms covering torso** make it hard to place upper-body garments. Use photos with arms at the sides.
- **Extreme poses** (jumping, bending) produce less accurate results than standing poses.
- **Multiple people in frame** — the model may not know which person to dress. Crop to a single person.
- **Accessory conflicts** — if the person wears a scarf or bag, specify whether to keep or remove them.
- **Resolution mismatch** — a low-res person photo with a high-res garment (or vice versa) can look unnatural.

## Related Skills

- [AI Fashion Model](../ai-fashion-model/SKILL.md) — Generate virtual models from scratch
- [AI Outfit Generator](../ai-outfit-generator/SKILL.md) — Create complete outfit ideas
- [AI Product Photo](../../ecommerce/ai-product-photo/SKILL.md) — Professional garment photography
- [AI Lifestyle Photo](../../ecommerce/ai-lifestyle-photo/SKILL.md) — Products in real-world settings

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
