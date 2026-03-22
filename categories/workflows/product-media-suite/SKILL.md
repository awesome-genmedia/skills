---
name: product-media-suite
description: "Generate a full product media package using each::sense AI. Create product photography, lifestyle shots, video content, and social media assets for a single product in one workflow. Produce hero shots, context scenes, detail close-ups, unboxing sequences, and promotional videos. Use for: product photography, product media, e-commerce assets, product launch media, complete product visuals. Triggers: product media, product suite, product photography, product video, product assets, e-commerce media, product launch, product visuals, full product media, product package"
allowed-tools: Bash(curl *), WebFetch
---

# Product Media Suite

Generate a complete product media package — photography, lifestyle shots, video, and social assets — using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Step 1: Hero Product Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A hero product photograph of a premium wireless speaker: cylindrical brushed aluminum body with a fabric mesh grille, placed on a white marble surface, soft studio lighting with a gentle shadow, clean white background, three-quarter angle showing the top controls and front grille, commercial product photography"
      }
    ],
    "stream": false
  }'
```

### Step 2: Lifestyle Context Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A lifestyle product photograph of a premium wireless speaker on a wooden side table in a modern living room, soft afternoon light from large windows, a person relaxing on a couch in the background reading a book, warm inviting atmosphere, the speaker as the subtle hero of the scene, editorial lifestyle photography"
      }
    ],
    "stream": false
  }'
```

### Step 3: Product Video

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A short product reveal video: a premium wireless speaker slowly rotating on a turntable, dramatic lighting highlighting the brushed aluminum finish and fabric mesh texture, soft reflections, dark background, smooth 360-degree rotation, commercial product video style"
      }
    ],
    "image_urls": ["IMAGE_URL_FROM_STEP_1"],
    "stream": false
  }'
```

### Full Pipeline in Python

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

PRODUCT = "premium wireless speaker, cylindrical brushed aluminum body with fabric mesh grille"
STYLE = "clean modern, warm tones, commercial quality"

media_suite = {
    "hero_shot": f"Hero product photo: {PRODUCT} on white marble, soft studio lighting, white background, three-quarter angle, {STYLE}",
    "detail_closeup": f"Detail close-up: extreme macro of the {PRODUCT} fabric mesh texture and aluminum edge, shallow depth of field, studio lighting, {STYLE}",
    "lifestyle_living": f"Lifestyle shot: {PRODUCT} on a side table in a modern living room, person reading on couch, afternoon window light, {STYLE}",
    "lifestyle_outdoor": f"Lifestyle shot: {PRODUCT} on a patio table during a summer gathering, friends in background, golden hour, {STYLE}",
    "flat_lay": f"Flat lay: {PRODUCT} with charging cable, user manual, and packaging arranged on a clean surface, overhead view, unboxing aesthetic, {STYLE}",
    "social_square": f"Instagram post: {PRODUCT} in a minimal setting with a coffee cup and plant, warm light, square composition, {STYLE}",
    "social_story": f"Instagram Story: hand reaching to tap the top of the {PRODUCT}, close-up vertical format, warm light, {STYLE}"
}

for asset_name, prompt in media_suite.items():
    print(f"Generating {asset_name}...")
    response = client.chat.completions.create(
        model="eachsense/beta",
        messages=[{"role": "user", "content": prompt}]
    )
    print(f"  {asset_name}: {response.choices[0].message.content}")
    print("---")
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Product Media Suites

- **Define the product precisely once** — Create a reusable product description string.
- **Maintain visual consistency** — Same product appearance, lighting temperature, and color grading.
- **Cover all e-commerce needs** — Hero shot, detail, lifestyle, group, and size comparison.
- **Plan for each platform** — Amazon (white background), Shopify (lifestyle), social media (engaging).
- **Generate video last** — Use the best still image as a reference for animation.

## Examples

### E-Commerce Complete Package

```bash
PRODUCT="matte black ceramic coffee mug with a wooden handle"

# White background (Amazon/Shopify)
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d "{
    \"messages\": [{\"role\": \"user\", \"content\": \"A $PRODUCT centered on pure white background, soft even studio lighting, no shadows, product isolated, e-commerce product photo, front view\"}],
    \"stream\": false
  }"

# Lifestyle (brand website)
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d "{
    \"messages\": [{\"role\": \"user\", \"content\": \"A $PRODUCT filled with steaming coffee on a rustic wooden desk next to an open book, morning sunlight streaming in, cozy home office atmosphere, lifestyle product photography\"}],
    \"stream\": false
  }"

# Detail close-up
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d "{
    \"messages\": [{\"role\": \"user\", \"content\": \"Extreme close-up detail shot of a $PRODUCT showing the matte ceramic texture and the grain of the wooden handle, shallow depth of field, studio macro photography\"}],
    \"stream\": false
  }"
```

## Workflow: Product Media Suite Pipeline

1. **Define the product** — Create a precise product description string.
2. **Generate hero shots** — White background and styled product photography.
3. **Create detail close-ups** — Texture, material, and feature close-ups.
4. **Produce lifestyle scenes** — Product in real-world usage contexts.
5. **Generate social media variants** — Platform-specific crops and compositions.
6. **Create product video** — Use hero shot as reference for animated reveal.
7. **Prepare for platforms** — Export in required formats for each sales channel.

## Related Skills

- [Social Media Batch](../social-media-batch/SKILL.md) — Multi-platform social content
- [Image to Video Pipeline](../image-to-video-pipeline/SKILL.md) — Animate product shots
- [Text to Multimedia](../text-to-multimedia/SKILL.md) — Full multimedia from text
- [AI Ad Creative](../../marketing/ai-ad-creative/SKILL.md) — Ad creatives for product promotion

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic product renders
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Lifestyle and creative shots
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast product iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
