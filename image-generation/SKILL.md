---
name: image-generation
description: "Generate images from text descriptions using each::sense AI. Create photorealistic photos, illustrations, concept art, digital paintings, logos, and any visual from a text prompt. Supports all styles from hyperrealism to anime, abstract to architectural. 7 specialized models including flux-2-max, gemini-imagen-4, and seedream-v4-5. Use for: concept art, illustrations, marketing visuals, social media images, product shots, storyboarding, creative exploration. Triggers: generate image, create image, text to image, ai image, image generation, txt2img, ai art, generate picture, create visual, image from text, ai illustration, make image, draw, render"
allowed-tools: Bash(curl *), WebFetch
---

# Image Generation

Generate images from text descriptions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A lone astronaut standing on a red desert planet, looking up at a sky filled with three massive moons, cinematic lighting, photorealistic, wide shot"}],
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
    messages=[{"role": "user", "content": "A lone astronaut standing on a red desert planet, looking up at a sky filled with three massive moons, cinematic lighting, photorealistic, wide shot"}]
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate an image in the same style as this reference, but change the setting to a futuristic Tokyo street at night"}],
    "image_urls": ["https://example.com/reference-style.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

| Model | Strengths | Best For |
|-------|-----------|----------|
| **flux-2-max** | Highest quality, exceptional detail | Hero images, print-ready visuals, portfolio work |
| **flux-2-pro** | Fast with balanced quality | Rapid iteration, production workflows |
| **flux-kontext-pro** | Accurate text rendering in images | Posters, signs, logos with readable text |
| **nano-banana-pro** | Fastest generation speed | Prototyping, bulk generation, real-time previews |
| **gemini-imagen-4** | Outstanding photorealism | Product photography, lifestyle shots, realistic scenes |
| **seedream-v4-5** | Artistic and stylized outputs | Illustrations, fantasy art, painterly styles |
| **kling-text-to-image** | Versatile across styles | General-purpose generation, mixed media |

> each::sense automatically picks the optimal model based on your prompt. You do not need to specify a model unless you want to override the selection.

## Prompt Engineering Guide

### Prompt Structure

```
[subject] + [action/pose] + [environment] + [style] + [lighting] + [camera/composition]
```

### Style Keywords

| Style | Keywords |
|-------|----------|
| **Photorealistic** | photorealistic, ultra-realistic, DSLR photo, 8K, raw photo, unedited |
| **Illustration** | digital illustration, vector art, hand-drawn, watercolor, ink drawing |
| **Cinematic** | cinematic, film still, movie scene, dramatic lighting, anamorphic lens |
| **Anime** | anime style, manga, cel shading, Studio Ghibli, Makoto Shinkai |
| **3D Render** | 3D render, octane render, unreal engine, isometric, blender render |
| **Oil Painting** | oil painting, impasto, classical art, Renaissance, Baroque |
| **Pixel Art** | pixel art, 16-bit, retro game, 8-bit, sprite art |
| **Minimalist** | minimalist, flat design, simple, clean lines, geometric |

### Aspect Ratios

Specify aspect ratio in your prompt to control image dimensions:

```
"... landscape format, 16:9 aspect ratio"
"... square format, 1:1"
"... portrait format, 9:16, vertical"
"... ultrawide, 21:9 cinematic"
```

### Quality Boosters

```
masterpiece, highly detailed, sharp focus, professional,
studio quality, award-winning, 8K resolution, HDR
```

### Negative Guidance

Describe what you do not want to improve results:

```
"... avoid blurry, no watermarks, no text overlays, avoid distorted faces"
```

## Examples

### Photorealistic Landscape

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A misty fjord in Norway at sunrise, mirror-like water reflecting snow-capped mountains, a small red fishing cabin on the shore, photorealistic, 8K, golden hour lighting, shot on Hasselblad"}],
    "stream": false
  }'
```

### Digital Illustration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A cozy bookstore interior with a cat sleeping on a stack of old books, warm lamp light, plants hanging from the ceiling, digital illustration, Studio Ghibli style, soft colors, whimsical atmosphere"}],
    "stream": false
  }'
```

### Product Photography

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A sleek wireless earbud case on a marble surface, soft studio lighting, product photography, shallow depth of field, clean minimalist background, commercial quality, 1:1 square format"}],
    "stream": false
  }'
```

### Concept Art

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A floating cyberpunk city above the clouds, neon lights reflecting off chrome towers, flying vehicles streaming between buildings, concept art, matte painting, epic scale, dramatic perspective, 16:9 cinematic"}],
    "stream": false
  }'
```

### Text-in-Image (Poster)

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "A vintage concert poster for a band called SOLAR DRIFT, playing at The Echo Lounge, June 15th. Retro psychedelic style with swirling colors, 60s typography, orange and purple palette, portrait format"}],
    "stream": false
  }'
```

## Batch Generation Workflow

```bash
# Generate multiple style variations of the same subject
PROMPTS=(
  "A medieval castle on a cliff at sunset, oil painting style"
  "A medieval castle on a cliff at sunset, photorealistic, drone shot"
  "A medieval castle on a cliff at sunset, anime style, Makoto Shinkai"
  "A medieval castle on a cliff at sunset, pixel art, 16-bit"
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

## Common Pitfalls

- **Vague prompts** produce generic results. Be specific about subject, style, and mood.
- **Too many subjects** in one prompt cause confusion. Focus on one main subject per image.
- **Text rendering** can be unreliable in most models. Use flux-kontext-pro for text-heavy images.
- **Hands and fingers** can be distorted. Crop or pose hands carefully if they are the focus.
- **Contradictory styles** (e.g., "photorealistic watercolor") confuse the model. Pick one.
- **Overloaded prompts** with 50+ words often degrade quality. Aim for 15-40 words of focused description.

## Related Skills

- [Image Editing](../image-editing/SKILL.md) — Edit and modify generated images with natural language
- [Image Upscaling](../image-upscaling/SKILL.md) — Enhance resolution of generated images
- [Background Removal](../background-removal/SKILL.md) — Remove backgrounds from generated images
- [Video Generation](../video-generation/SKILL.md) — Animate your images into video

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
