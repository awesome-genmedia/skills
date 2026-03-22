---
name: ai-video-loop
description: "Create seamless looping videos using each::sense AI. Generate perfectly looping background videos, cinemagraphs, animated wallpapers, and endless motion clips where the end connects smoothly back to the beginning. Supports nature loops, abstract motion, ambient scenes, and decorative backgrounds. Use for: website backgrounds, digital signage, live wallpapers, presentation backgrounds, streaming overlays, ambient displays, waiting room screens. Triggers: video loop, looping video, seamless loop, cinemagraph, animated background, live wallpaper, infinite loop, looping animation, gif loop, ambient video, background video, endless video"
allowed-tools: Bash(curl *), WebFetch
---

# AI Video Loop

Create seamless looping videos for backgrounds and displays using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a seamless looping video: gentle ocean waves rolling onto a sandy beach, foam advancing and retreating, camera static, soft afternoon light, calm and meditative, the motion must loop perfectly with no visible cut point"
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
        "content": "Generate a seamless looping video: gentle ocean waves rolling onto a sandy beach, foam advancing and retreating, camera static, soft afternoon light, calm and meditative, the motion must loop perfectly with no visible cut point"
    }]
)

print(response.choices[0].message.content)
```

### From a Still Image

Create a looping animation from a static photo:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a seamless looping video from this image. Animate only the water and clouds — keep everything else perfectly still. The loop should have no visible start or end point, creating an infinite cinemagraph effect."},
              {"type": "image_url", "image_url": {"url": "https://example.com/lake-mountain.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Loop-Friendly Subjects

| Subject | Why It Loops Well | Examples |
|---------|------------------|---------|
| **Water** | Repetitive wave motion, flowing streams | Ocean waves, waterfalls, rain |
| **Fire / Flames** | Organic, non-linear movement | Campfire, candles, torches |
| **Clouds** | Slow, drifting, amorphous | Sky timelapse, fog, mist |
| **Abstract** | No reference points to spot the cut | Fluid simulations, particles, gradients |
| **Nature Sway** | Repetitive, wind-driven | Grass, trees, flowers swaying |
| **Ambient Scenes** | Subtle, repeating motion | Coffee steam, aquarium, rain on window |
| **Geometric** | Mathematical, cyclical | Rotating shapes, kaleidoscope, mandala |

## Examples

### Fireplace Ambiance

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless looping video: a cozy fireplace with dancing flames, glowing embers, and soft crackling warmth. Close-up of the fire, warm orange light flickering on stone surround, static camera, the fire animation must loop seamlessly with no visible cut."
      }
    ],
    "stream": false
  }'
```

### Abstract Gradient

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless looping video: slowly shifting abstract color gradient, deep purple transitioning to midnight blue to dark teal and back. Smooth organic movement like aurora borealis, subtle noise texture, minimal and calming, perfect seamless loop for a website background."
      }
    ],
    "stream": false
  }'
```

### Rainy Window Cinemagraph

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless looping video: raindrops streaming down a window glass, blurred city lights visible behind, warm interior glow reflecting on the glass. Only the rain moves, everything else is still. Cinemagraph style, moody and cozy, perfect infinite loop."
      }
    ],
    "stream": false
  }'
```

### Underwater Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless looping video: underwater coral reef scene, small tropical fish swimming back and forth, light rays filtering through the water surface above, gentle current moving sea plants, bubbles rising, peaceful and hypnotic, seamless loop."
      }
    ],
    "stream": false
  }'
```

## Prompt Tips

- **Always say "seamless looping"** — this is the key signal for loop-compatible generation
- **Mention "no visible cut point"** to emphasize the seamlessness requirement
- **Choose cyclical or continuous motion**: Waves, fire, and wind naturally loop; a person walking across frame does not
- **Keep camera static**: Moving cameras make seamless loops much harder
- **Limit the number of moving elements**: Fewer things in motion means a cleaner loop
- **Specify "cinemagraph style"** for loops where only part of the image moves

## Use Case Settings

| Use Case | Duration | Resolution | Notes |
|----------|----------|------------|-------|
| **Website Background** | 5-10 sec | 1920x1080 | Subtle, non-distracting |
| **Digital Signage** | 10-15 sec | 3840x2160 | Eye-catching, commercial |
| **Live Wallpaper** | 5-10 sec | Device resolution | Battery efficient, subtle |
| **Stream Overlay** | 5-10 sec | 1920x1080 | Transparent-friendly, subtle |
| **Waiting Room Display** | 10-30 sec | 1920x1080 | Calming, ambient |

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — General video generation
- [Image to Video](../image-to-video/SKILL.md) — Animate still images
- [AI Timelapse Generator](../ai-timelapse-generator/SKILL.md) — Accelerated time sequences
- [AI Music Video](../ai-music-video/SKILL.md) — Looping visuals for music

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
