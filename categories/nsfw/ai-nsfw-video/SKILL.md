---
name: ai-nsfw-video
description: "Generate NSFW video content with safety checker disabled using each::sense AI. Create adult-oriented animated and video content with explicit generation enabled. Requires enable_safety_checker set to false in the request. Use for: NSFW video generation, adult video content, mature animated content, unrestricted video generation. Triggers: nsfw video, adult video, nsfw animation, mature video, explicit video, nsfw video generation, adult content video, unrestricted video"
allowed-tools: Bash(curl *), WebFetch
---

# AI NSFW Video Generator

Generate NSFW video content with the safety checker disabled using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a short artistic video of a classical figure in motion, Renaissance painting style come to life, dramatic chiaroscuro lighting, flowing fabric and graceful movement, fine art animation"
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
        "content": "Generate a short artistic video of a classical figure in motion, Renaissance painting style come to life, dramatic chiaroscuro lighting, flowing fabric and graceful movement, fine art animation"
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
          {"type": "text", "text": "Animate this artistic image into a short video: gentle movement, flowing fabric, atmospheric lighting changes, fine art video quality, mature artistic content"},
          {"type": "image_url", "image_url": {"url": "https://example.com/art-reference.jpg"}}
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

- **The `enable_safety_checker` parameter must be set to `false`** as a top-level request field to generate NSFW video content.
- Without this parameter, the safety checker is enabled by default and will block explicit content.
- Ensure compliance with your local laws and platform terms of service when generating and distributing adult content.
- This feature is intended for legitimate adult artistic and creative use cases.
- Video generation may take longer than image generation due to the additional frames required.

## Examples

### Artistic Dance Sequence

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A short artistic video of a contemporary dance performance, fluid graceful movements, dramatic stage lighting with deep shadows and spotlight pools, silk fabric in motion, mature artistic expression, cinematic quality"
      }
    ],
    "enable_safety_checker": false,
    "stream": false
  }'
```

### Animated Fine Art

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An animated painting in the style of a Baroque masterpiece, a mythological scene with figures in motion, rich warm oil paint colors, candlelight flickering across the scene, subtle movement bringing the classical painting to life, museum-quality fine art animation"
      }
    ],
    "enable_safety_checker": false,
    "stream": false
  }'
```

### Fantasy Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A short fantasy video of a water nymph emerging from a glowing enchanted pool in a moonlit forest, bioluminescent plants illuminating the scene, ethereal fog, magical atmosphere, fantasy art animation, mature artistic content"
      }
    ],
    "enable_safety_checker": false,
    "stream": false
  }'
```

## Workflow

1. **Define the artistic vision** — Classical, fantasy, photographic, or abstract.
2. **Include the safety checker flag** — Always set `"enable_safety_checker": false`.
3. **Describe motion and composition** — Subject, movement, lighting, and camera.
4. **Generate the video** — Submit the request with explicit content generation enabled.
5. **Review and iterate** — Refine prompts for desired quality and motion.

## Related Skills

- [AI NSFW Image](../ai-nsfw-image/SKILL.md) — NSFW image generation
- [Image to Video Pipeline](../../workflows/image-to-video-pipeline/SKILL.md) — Animate images into video
- [AI Educational Video](../../education/ai-educational-video/SKILL.md) — General video generation (safe mode)
- [AI Testimonial Video](../../marketing/ai-testimonial-video/SKILL.md) — Video content generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-fidelity generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative artistic outputs
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
