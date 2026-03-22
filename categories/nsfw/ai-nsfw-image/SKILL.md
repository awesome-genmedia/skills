---
name: ai-nsfw-image
description: "Generate NSFW images with safety checker disabled using each::sense AI. Create adult-oriented artistic and photographic imagery with explicit content generation enabled. Requires enable_safety_checker set to false in the request. Use for: NSFW image generation, adult art, mature content, unrestricted image generation. Triggers: nsfw image, adult image, nsfw art, mature image, explicit image, nsfw generation, adult content image, unrestricted image"
allowed-tools: Bash(curl *), WebFetch
---

# AI NSFW Image Generator

Generate NSFW images with the safety checker disabled using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

**Important:** This skill requires `"enable_safety_checker": false` in the request body to disable content filtering.

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
        "content": "A fine art nude figure study, classical Renaissance painting style, dramatic chiaroscuro lighting, oil on canvas texture, museum-quality composition"
      }
    ],
    "enable_safety_checker": false,
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
        "content": "A fine art nude figure study, classical Renaissance painting style, dramatic chiaroscuro lighting, oil on canvas texture, museum-quality composition"
    }],
    extra_body={"enable_safety_checker": False}
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
          {"type": "text", "text": "Create an artistic interpretation of this reference in a mature fine art style, classical composition and lighting"},
          {"type": "image_url", "image_url": {"url": "https://example.com/reference.jpg"}}
        ]
      }
    ],
    "enable_safety_checker": false,
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Important Notes

- **The `enable_safety_checker` parameter must be set to `false`** as a top-level request field to generate NSFW content.
- Without this parameter, the safety checker is enabled by default and will block explicit content.
- Ensure compliance with your local laws and platform terms of service when generating and distributing adult content.
- This feature is intended for legitimate adult artistic and creative use cases.

## Examples

### Classical Art Style

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A classical Greek sculpture-inspired figure composition, marble texture, dramatic museum lighting, fine art photography style, high contrast black and white"
      }
    ],
    "enable_safety_checker": false,
    "stream": false
  }'
```

### Artistic Photography Style

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An artistic boudoir photograph, soft natural window light, silk fabric draping, intimate and elegant atmosphere, shallow depth of field, warm tones, fine art photography"
      }
    ],
    "enable_safety_checker": false,
    "stream": false
  }'
```

### Fantasy Art Style

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A fantasy art illustration of a mythological siren emerging from moonlit ocean waves, ethereal glowing skin, flowing hair merging with seafoam, dramatic moonlight, digital fantasy painting, mature artistic content"
      }
    ],
    "enable_safety_checker": false,
    "stream": false
  }'
```

## Workflow

1. **Define the artistic direction** — Classical, photographic, fantasy, or illustrative.
2. **Include the safety checker flag** — Always set `"enable_safety_checker": false`.
3. **Describe the composition** — Subject, pose, lighting, and mood.
4. **Generate the image** — Submit the request with explicit content generation enabled.
5. **Review and iterate** — Refine prompts for desired artistic quality.

## Related Skills

- [AI NSFW Video](../ai-nsfw-video/SKILL.md) — NSFW video generation
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation (safe mode)
- [AI Photo Style Transfer](../../photography/ai-photo-style-transfer/SKILL.md) — Artistic style application
- [AI Abstract Art](../../nft-art/ai-abstract-art/SKILL.md) — Abstract artistic compositions

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-fidelity image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Artistic creative outputs
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
