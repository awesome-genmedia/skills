---
name: ai-music-video
description: "Create music videos and audio visualizers using each::sense AI. Generate cinematic music video scenes, abstract audio-reactive visuals, performance sequences, and narrative clips that match musical genres and moods. Supports live performance, abstract, narrative, and lyric video styles. Use for: music videos, album visualizers, live performance visuals, lyric videos, concert backgrounds, VJ content, audio-reactive art. Triggers: ai music video, music video, music visualizer, audio visual, concert visual, vj content, lyric video, music clip, band video, performance video, audio reactive, music animation"
allowed-tools: Bash(curl *), WebFetch
---

# AI Music Video

Create music videos and audio visualizers using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a music video clip: a singer performing on a rooftop at golden hour, city skyline behind them, warm cinematic lighting, camera slowly orbiting, lens flares from the setting sun, indie folk aesthetic, dreamy atmosphere"
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
        "content": "Generate a music video clip: a singer performing on a rooftop at golden hour, city skyline behind them, warm cinematic lighting, camera slowly orbiting, lens flares from the setting sun, indie folk aesthetic, dreamy atmosphere"
    }]
)

print(response.choices[0].message.content)
```

### With Album Art Reference

Use album artwork as a visual starting point:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a music video clip using this album cover as the visual style. Animate the scene with flowing movement, add atmospheric particles, camera slowly zooming in, moody and immersive"},
              {"type": "image_url", "image_url": {"url": "https://example.com/album-cover.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Music Video Styles by Genre

| Genre | Visual Style | Keywords |
|-------|-------------|----------|
| **Hip-Hop/Rap** | Urban, neon, cars, jewelry, dark aesthetics | neon lights, dark street, luxury, cinematic |
| **Indie/Folk** | Nature, golden light, vintage, intimate | warm film, golden hour, nostalgic, handheld |
| **Electronic/EDM** | Abstract, geometric, neon, futuristic | particle effects, glitch, neon geometry, pulsing |
| **Rock/Metal** | Dark, flames, intense, gritty | dramatic, fire, smoke, high contrast, desaturated |
| **Pop** | Colorful, choreography, bright, playful | vibrant, dance, kaleidoscope, glossy |
| **Jazz/Soul** | Moody, smoky, intimate, warm | low key lighting, smoke, warm tones, club |
| **Classical** | Elegant, nature, abstract beauty | flowing fabric, water, minimal, graceful |
| **Lo-fi/Chill** | Anime aesthetic, cozy rooms, rain | anime style, rainy window, soft glow, cozy |

## Examples

### Abstract Audio Visualizer

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate an abstract music visualizer: flowing neon ribbons of light dancing through a dark void, pulsing and undulating rhythmically, colors shifting from electric blue to magenta to gold, particles trailing behind each ribbon, deep space background, mesmerizing and hypnotic"
      }
    ],
    "stream": false
  }'
```

### Lo-fi Chill Scene

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a lo-fi music video scene: a cozy anime-style room at night, rain streaming down the window, a desk with a warm lamp and stacked books, a cat sleeping on the windowsill, steam rising from a coffee cup, soft warm glow, gentle animation, relaxing atmosphere"
      }
    ],
    "stream": false
  }'
```

### Rock Performance

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a rock music video clip: a guitarist playing on a dark stage, dramatic backlight silhouette, red and white spotlights cutting through smoke, camera low angle looking up, intense energy, sparks falling, concert atmosphere, anamorphic cinematic"
      }
    ],
    "stream": false
  }'
```

## Music Video Workflow

Generate multiple clips per shot list and edit together:

```bash
# Verse scene
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Music video clip: a person walking alone through an empty city at dawn, long shadows, melancholic atmosphere, slow tracking shot from behind, cinematic indie film look"}],
    "stream": false
  }'

# Chorus scene
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Music video clip: same person now on a rooftop, arms spread wide, wind blowing their hair, golden sunrise light flooding the scene, uplifting energy, camera orbiting slowly, lens flares, cinematic"}],
    "stream": false
  }'

# Bridge scene
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Music video clip: abstract sequence of floating lights and particles dissolving into colors, dreamlike, slow motion, macro lens, transitional visual, ethereal and otherworldly"}],
    "stream": false
  }'
```

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — General video generation
- [AI Video Loop](../ai-video-loop/SKILL.md) — Looping backgrounds for streams
- [AI Cinematic Trailer](../ai-cinematic-trailer/SKILL.md) — Dramatic visual narratives
- [Image to Video](../image-to-video/SKILL.md) — Animate album artwork

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
