---
name: text-to-image
description: "Generate images from text descriptions using each::sense AI. Create photorealistic scenes, illustrations, concept art, digital paintings, and any visual from a text prompt. Supports all styles from hyperrealism to anime, abstract to architectural. Use for: concept art, illustrations, marketing visuals, social media images, creative exploration, storyboarding. Triggers: text to image, generate image, create image, ai image, image generation, txt2img, prompt to image, ai art, generate picture, create visual, image from text, ai illustration"
allowed-tools: Bash(curl *), WebFetch
---

# Text to Image

Generate images from text descriptions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A lone astronaut standing on a red desert planet, looking up at a sky filled with three massive moons, cinematic lighting, photorealistic, wide shot"
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
        "content": "A lone astronaut standing on a red desert planet, looking up at a sky filled with three massive moons, cinematic lighting, photorealistic, wide shot"
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Prompt Engineering Guide

### Prompt Structure

```
[subject] + [action/pose] + [environment] + [style] + [lighting] + [camera/composition]
```

### Style Keywords

| Style | Keywords |
|-------|----------|
| **Photorealistic** | photorealistic, ultra-realistic, DSLR photo, 8K, raw photo |
| **Illustration** | digital illustration, vector art, hand-drawn, watercolor |
| **Cinematic** | cinematic, film still, movie scene, dramatic lighting, anamorphic |
| **Anime** | anime style, manga, cel shading, Studio Ghibli |
| **3D Render** | 3D render, octane render, unreal engine, isometric |
| **Oil Painting** | oil painting, impasto, classical art, Renaissance |
| **Pixel Art** | pixel art, 16-bit, retro game, 8-bit |

### Quality Boosters

```
masterpiece, highly detailed, sharp focus, professional,
studio quality, award-winning, 8K resolution, HDR
```

## Examples

### Photorealistic Landscape

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A misty fjord in Norway at sunrise, mirror-like water reflecting snow-capped mountains, a small red fishing cabin on the shore, photorealistic, 8K, golden hour lighting"
      }
    ],
    "stream": false
  }'
```

### Digital Illustration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A cozy bookstore interior with a cat sleeping on a stack of old books, warm lamp light, plants hanging from the ceiling, digital illustration, Studio Ghibli style, soft colors"
      }
    ],
    "stream": false
  }'
```

### Concept Art

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A floating cyberpunk city above the clouds, neon lights reflecting off chrome towers, flying vehicles streaming between buildings, concept art, matte painting, epic scale, dramatic perspective"
      }
    ],
    "stream": false
  }'
```

### Product Visualization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A sleek wireless earbud case on a marble surface, soft studio lighting, product photography, shallow depth of field, clean minimalist background, commercial quality"
      }
    ],
    "stream": false
  }'
```

## Common Pitfalls

- **Vague prompts** produce generic results. Be specific about subject, style, and mood.
- **Too many subjects** in one prompt cause confusion. Focus on one main subject.
- **Text rendering** is unreliable in AI-generated images. Avoid asking for specific words.
- **Hands and fingers** can be distorted. Crop or hide hands if they are not the focus.
- **Contradictory styles** (e.g., "photorealistic watercolor") confuse the model.

## Batch Generation Workflow

```bash
# Generate multiple variations by iterating prompts
PROMPTS=(
  "A medieval castle on a cliff at sunset, oil painting style"
  "A medieval castle on a cliff at sunset, photorealistic"
  "A medieval castle on a cliff at sunset, anime style"
)

for PROMPT in "${PROMPTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$PROMPT\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Related Skills

- [Image to Image](../image-to-image/SKILL.md) — Transform existing images with style transfer
- [AI Image Editor](../ai-image-editor/SKILL.md) — Edit generated images with natural language
- [Image Upscaling](../image-upscaling/SKILL.md) — Enhance resolution of generated images
- [AI Wallpaper Generator](../ai-wallpaper-generator/SKILL.md) — Generate device-ready wallpapers

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
