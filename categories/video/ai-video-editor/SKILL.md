---
name: ai-video-editor
description: "Edit videos with AI assistance using each::sense AI. Apply style transfers, change visual elements, add effects, modify scenes, and transform video content with natural language instructions. Supports color grading, visual effects, scene modifications, and artistic transformations. Use for: video post-production, color grading, visual effects, style transfer, scene modification, video enhancement, content transformation. Triggers: ai video editor, edit video, video editing, video effects, color grade, video filter, transform video, video style, modify video, video post production, video enhancement"
allowed-tools: Bash(curl *), WebFetch
---

# AI Video Editor

Edit and transform videos with natural language instructions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Edit this video: apply a warm cinematic color grade with slightly desaturated tones, add a subtle film grain overlay, and enhance the contrast for a moody atmospheric look"
      }
    ],
    "image_urls": ["https://example.com/raw-footage.mp4"],
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
        "content": "Edit this video: apply a warm cinematic color grade with slightly desaturated tones, add a subtle film grain overlay, and enhance the contrast for a moody atmospheric look"
    }],
    extra_body={
        "image_urls": ["https://example.com/raw-footage.mp4"]
    }
)

print(response.choices[0].message.content)
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images/videos.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Edit Types

| Edit Type | Description | Example Prompt |
|-----------|-------------|---------------|
| **Color Grading** | Adjust colors, tones, and mood | "Apply a teal and orange cinematic look" |
| **Style Transfer** | Convert visual style of footage | "Make this look like a Studio Ghibli anime" |
| **Weather Effects** | Add environmental effects | "Add falling snow and a winter atmosphere" |
| **Time of Day** | Change lighting conditions | "Transform this daytime scene to golden hour" |
| **Visual Effects** | Add particles, glow, or overlays | "Add floating fireflies and a magical glow" |
| **Enhancement** | Improve quality and detail | "Stabilize, sharpen, and reduce noise" |

## Examples

### Cinematic Color Grade

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Apply a cinematic teal-and-orange color grade to this video. Shadows pushed toward teal, highlights toward warm amber. Slightly raised black levels for a filmic look. Consistent throughout the clip."
      }
    ],
    "image_urls": ["https://example.com/interview-footage.mp4"],
    "stream": false
  }'
```

### Style Transfer

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this real-world video into a hand-painted watercolor animation style. Soft brush strokes, gentle color bleeding at edges, paper texture visible, maintain smooth motion. Keep the same subjects and movements."
      }
    ],
    "image_urls": ["https://example.com/park-walk.mp4"],
    "stream": false
  }'
```

### Add Environmental Effects

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Add rain to this outdoor video: heavy raindrops falling, wet reflections on the ground, slight mist in the distance, darker sky. The rain should interact naturally with the scene and be consistent frame-to-frame."
      }
    ],
    "image_urls": ["https://example.com/street-scene.mp4"],
    "stream": false
  }'
```

## Prompt Tips

- **Be specific about the look**: "teal and orange" is better than "cinematic colors"
- **Mention consistency**: "Apply uniformly across all frames" prevents flickering
- **Describe the reference**: "Like a Christopher Nolan film" communicates a clear aesthetic
- **One major edit per pass**: Combining too many edits may produce inconsistent results
- **Specify what to preserve**: "Keep the original motion and composition" prevents unwanted changes

## Common Color Grade Presets

| Look | Description |
|------|-------------|
| **Teal & Orange** | Cool shadows, warm highlights — blockbuster cinema |
| **Desaturated Cool** | Muted, blue-gray tones — thriller, drama |
| **Warm Vintage** | Golden haze, lifted blacks — nostalgic, indie film |
| **High Contrast B&W** | Dramatic black and white — documentary, noir |
| **Pastel Soft** | Low contrast, soft colors — romance, dream sequence |
| **Neon Cyberpunk** | Saturated pinks, blues, greens — sci-fi, music videos |

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — Generate video from text
- [Image to Video](../image-to-video/SKILL.md) — Animate images
- [AI Slow Motion](../ai-slow-motion/SKILL.md) — Slow motion frame interpolation
- [AI Video Loop](../ai-video-loop/SKILL.md) — Create looping videos

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
