---
name: ai-slow-motion
description: "Create slow motion video effects with AI frame interpolation using each::sense AI. Generate smooth slow-motion clips from text prompts or slow down existing video with AI-generated intermediate frames. Supports dramatic action, nature, sports, and artistic slow motion at various speeds. Use for: dramatic slow motion, sports highlights, nature details, artistic effects, product reveals, impact moments, dance choreography. Triggers: slow motion, ai slow motion, slow mo, frame interpolation, high fps, bullet time, time warp, slow down video, 120fps, super slow motion, dramatic slowdown"
allowed-tools: Bash(curl *), WebFetch
---

# AI Slow Motion

Create dramatic slow-motion video effects using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a slow motion video: a hummingbird hovering in front of a bright red flower, wings beating in extreme slow motion showing each individual wing stroke, iridescent feathers catching sunlight, shallow depth of field, macro lens, 1000fps look, garden background with smooth bokeh"
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
        "content": "Generate a slow motion video: a hummingbird hovering in front of a bright red flower, wings beating in extreme slow motion showing each individual wing stroke, iridescent feathers catching sunlight, shallow depth of field, macro lens, 1000fps look, garden background with smooth bokeh"
    }]
)

print(response.choices[0].message.content)
```

### Slow Down Existing Video

Apply AI frame interpolation to slow down existing footage:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Slow this video down to dramatic slow motion. Apply AI frame interpolation for smooth fluid motion, no jittering or frame blending artifacts. Maintain sharpness and detail throughout."},
              {"type": "image_url", "image_url": {"url": "https://example.com/action-clip.mp4"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Slow Motion Subjects

| Subject | Why It Works in Slow Mo | Speed Suggestion |
|---------|------------------------|-----------------|
| **Water Splash** | Reveals droplet shapes, crown splashes | 1000fps look |
| **Fire / Flames** | Shows fluid dynamics, dancing patterns | 240fps look |
| **Birds / Insects** | Wing movement, feather detail | 1000fps+ look |
| **Sports Action** | Peak moments, technique detail | 120-240fps look |
| **Fabric / Hair** | Flow, texture, graceful motion | 120fps look |
| **Breaking Glass** | Fracture patterns, shards | 2000fps+ look |
| **Rain / Snow** | Individual droplets, swirling flakes | 240-1000fps look |
| **Dance / Movement** | Grace, muscle detail, emotion | 120fps look |

## Examples

### Water Drop Impact

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a slow motion video: a single water drop falling into a still pool of dark blue water. On impact, a perfect crown splash forms and rises upward, individual droplets visible in the air, concentric ripples expand outward. Extreme slow motion, macro close-up, high-speed camera look, dramatic side lighting, black background."
      }
    ],
    "stream": false
  }'
```

### Athletic Action

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a slow motion video: a basketball player mid-dunk, suspended in the air with arm fully extended, sweat droplets flying off, arena lights creating rim light on muscles, crowd blurred in the background, dramatic slow motion, ESPN highlight style, low angle looking up."
      }
    ],
    "stream": false
  }'
```

### Paint Splash Art

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a slow motion video: vibrant paint of different colors — red, blue, yellow — being thrown at a white canvas in extreme slow motion. The paint splashes and blends in mid-air, forming abstract patterns, droplets hanging suspended, dynamic and artistic, studio lighting, clean white background, super slow motion."
      }
    ],
    "stream": false
  }'
```

## Speed Reference Guide

| Frame Rate | Slow Motion Factor | Visual Effect |
|------------|-------------------|--------------|
| **60fps** | 2.5x slower | Subtle smoothness |
| **120fps** | 5x slower | Noticeably slow, graceful |
| **240fps** | 10x slower | Sports replay quality |
| **480fps** | 20x slower | Fine details visible |
| **1000fps** | 40x slower | Phantom camera quality |
| **2000fps+** | 80x+ slower | Ultra slow, scientific |

## Prompt Tips

- **Name the fps look**: "1000fps look" or "Phantom camera quality" sets the expectation
- **Describe the peak moment**: Slow motion is about capturing the most dramatic instant
- **Mention particles**: "droplets visible," "dust particles," "sparks hanging in air" — slow motion reveals the invisible
- **Lighting is key**: Slow motion needs lots of light — mention "bright studio lighting" or "strong directional light"
- **Keep it simple**: One subject, one action — the slow motion is the star

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — General video generation
- [AI Timelapse Generator](../ai-timelapse-generator/SKILL.md) — Opposite effect — speed up time
- [AI Video Editor](../ai-video-editor/SKILL.md) — Edit and process video
- [AI Cinematic Trailer](../ai-cinematic-trailer/SKILL.md) — Dramatic slow motion shots for trailers

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
