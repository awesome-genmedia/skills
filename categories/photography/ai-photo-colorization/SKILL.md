---
name: ai-photo-colorization
description: "Colorize black and white photos using each::sense AI. Add realistic, historically accurate colors to grayscale photographs, vintage images, and archival materials. Supports portraits, landscapes, street scenes, and historical documentation. Use for: photo colorization, black and white to color, vintage photo coloring, historical photo colorization, grayscale to color. Triggers: colorize photo, black and white to color, photo colorization, add color, grayscale to color, colorize, vintage color, historical colorization, BW to color, monochrome to color"
allowed-tools: Bash(curl *), WebFetch
---

# AI Photo Colorization

Colorize black and white photographs with realistic, natural colors using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Colorize this black and white photograph with realistic natural colors: accurate skin tones, believable clothing colors appropriate to the era, natural sky and vegetation colors, maintain the original photographic quality and composition"
      }
    ],
    "image_urls": ["https://example.com/black-and-white-photo.jpg"],
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
        "content": "Colorize this black and white photograph with realistic natural colors: accurate skin tones, believable clothing colors appropriate to the era, natural sky and vegetation colors, maintain the original photographic quality and composition"
    }],
    extra_body={"image_urls": ["https://example.com/black-and-white-photo.jpg"]}
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Photo Colorization

- **Always provide the source image** via `image_urls` — colorization requires the grayscale original.
- **Specify the era** — "1940s wartime," "1960s," "Victorian era" helps the model choose period-appropriate colors.
- **Guide specific colors** when known — "the car was red," "she wore a blue dress," "the house had green shutters."
- **Mention the scene type** — portrait, landscape, street scene, or interior to improve color accuracy.
- **Request subtle or vibrant** — "muted period-accurate tones" vs. "vibrant saturated colors."

## Examples

### Portrait Colorization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Colorize this 1940s black and white portrait: natural warm skin tones, the subject is wearing a dark navy suit with a white shirt, brown hair, soft warm studio lighting tones, keep the classic portrait feel while adding realistic color"
      }
    ],
    "image_urls": ["https://example.com/vintage-portrait-bw.jpg"],
    "stream": false
  }'
```

### Historical Street Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Colorize this 1920s city street photograph: period-accurate colors for brick buildings in warm red-brown, grey cobblestone streets, vintage automobiles in dark greens and blacks, pedestrians in muted earth-toned clothing, overcast sky, historically authentic color treatment"
      }
    ],
    "image_urls": ["https://example.com/1920s-street-bw.jpg"],
    "stream": false
  }'
```

### Landscape Colorization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Colorize this black and white landscape photograph: lush green forests, blue sky with white clouds, brown earth tones on the mountain face, golden sunlight on the meadow in the foreground, natural vivid colors, photorealistic colorization"
      }
    ],
    "image_urls": ["https://example.com/landscape-bw.jpg"],
    "stream": false
  }'
```

## Workflow: Archival Colorization Pipeline

1. **Restore the source** — Fix any damage before colorization using photo restoration.
2. **Research the era** — Identify the time period and likely colors for accuracy.
3. **Provide color guidance** — Specify known colors for clothing, vehicles, buildings, and signage.
4. **Colorize the image** — Apply AI colorization with era-specific cues.
5. **Review and adjust** — Check for color bleeding, unnatural tones, and historical accuracy.
6. **Enhance the result** — Apply HDR enhancement for final polish.

## Related Skills

- [AI Photo Restoration](../ai-photo-restoration/SKILL.md) — Repair damage before colorization
- [AI HDR Enhancement](../ai-hdr-enhancement/SKILL.md) — Enhance dynamic range after colorization
- [AI Photo Style Transfer](../ai-photo-style-transfer/SKILL.md) — Apply artistic color treatments
- [AI Stock Photo](../ai-stock-photo/SKILL.md) — Generate color stock photography

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Accurate, detailed colorization
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Intelligent color inference
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Quick colorization previews

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
