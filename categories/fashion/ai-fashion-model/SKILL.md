---
name: ai-fashion-model
description: "Generate AI fashion model imagery using each::sense AI. Create photorealistic virtual models wearing garments for lookbooks, catalogs, and e-commerce. Supports diverse body types, ethnicities, poses, and studio or outdoor settings. Use for: fashion lookbooks, catalog photography, e-commerce product pages, social media campaigns, editorial spreads. Triggers: ai fashion model, virtual model, fashion photography, ai model photo, lookbook model, catalog model, virtual mannequin, fashion shoot, model generation, ai clothing model"
allowed-tools: Bash(curl *), WebFetch
---

# AI Fashion Model

Generate photorealistic AI fashion model imagery for lookbooks, catalogs, and campaigns using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A professional fashion model wearing a tailored navy blazer and cream trousers, standing in a minimalist white studio, soft diffused lighting, full body shot, editorial fashion photography"
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
        "content": "A professional fashion model wearing a tailored navy blazer and cream trousers, standing in a minimalist white studio, soft diffused lighting, full body shot, editorial fashion photography"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a garment photo to generate a model wearing that specific item:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Generate a fashion model wearing the garment shown in the image. Full body shot, clean white studio background, natural pose, e-commerce photography style"},
              {"type": "image_url", "image_url": {"url": "https://example.com/garment-flat-lay.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Prompt Engineering Tips

### Prompt Structure

```
[model description] + [garment details] + [pose] + [setting/background] + [lighting] + [camera angle] + [photography style]
```

### Model Diversity Keywords

| Attribute | Keywords |
|-----------|----------|
| **Build** | slim, athletic, plus-size, petite, tall |
| **Age** | young adult, mid-thirties, mature, teen |
| **Ethnicity** | diverse — specify skin tone, hair texture, or features as needed |
| **Hair** | short cropped, long flowing, braids, curly, straight, bob |

### Photography Style Keywords

```
editorial fashion, high fashion, commercial photography,
e-commerce product shot, street style, catalog photography,
studio portrait, lifestyle fashion, runway look
```

## Examples

### Editorial Studio Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A female fashion model with short curly hair, wearing an oversized beige linen shirt and wide-leg white pants. Standing with one hand in pocket, relaxed posture. Clean white cyclorama background, soft key light from the left, fashion editorial photography, full body, shot on Canon EOS R5"
      }
    ],
    "stream": false
  }'
```

### Outdoor Lifestyle

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A male model in a fitted olive green bomber jacket and dark jeans, walking through a sun-dappled European cobblestone street in autumn. Golden hour lighting, shallow depth of field, candid street style photography, three-quarter body shot"
      }
    ],
    "stream": false
  }'
```

### E-commerce Product Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A South Asian female model wearing a floral print midi wrap dress in burgundy tones. Standing facing camera with a slight turn, neutral smile. Seamless light grey background, even studio lighting, e-commerce catalog photo, full body shot, sharp detail on fabric texture"
      }
    ],
    "stream": false
  }'
```

### Activewear Campaign

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An athletic female model in a black sports bra and high-waisted leggings with mesh panels, mid-stride running pose. Urban rooftop at dawn, dramatic backlighting, cinematic activewear campaign photography, dynamic composition"
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Multiple Poses

```bash
POSES=(
  "standing with arms crossed, confident pose"
  "walking toward camera, natural stride"
  "seated on a stool, relaxed casual pose"
  "leaning against a wall, one leg bent"
)

GARMENT="wearing a black turtleneck and tailored grey trousers"

for POSE in "${POSES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"A fashion model $GARMENT, $POSE, white studio background, commercial fashion photography, full body shot\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Hands and fingers** can distort. Use poses that keep hands relaxed or partially hidden (in pockets, behind back).
- **Brand logos or text on garments** will not render correctly. Describe the garment design without specific text.
- **Inconsistent model across shots** — AI generates a new model each time. For consistency across a lookbook, describe the model identically in every prompt.
- **Over-specifying** garment construction details (stitching type, exact button count) rarely helps. Focus on silhouette, color, and fabric.

## Related Skills

- [AI Clothing Try-On](../ai-clothing-try-on/SKILL.md) — Virtually try garments on real photos
- [AI Fashion Lookbook](../ai-fashion-lookbook/SKILL.md) — Generate complete lookbook layouts
- [AI Outfit Generator](../ai-outfit-generator/SKILL.md) — Create outfit combinations
- [AI Product Photo](../../ecommerce/ai-product-photo/SKILL.md) — Professional product shots

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
