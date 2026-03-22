---
name: ai-cinematic-trailer
description: "Create cinematic trailers and dramatic video sequences using each::sense AI. Generate movie-style trailers, game cinematics, book trailers, event teasers, and dramatic narrative clips with professional cinematography and pacing. Supports action, horror, sci-fi, fantasy, drama, and thriller aesthetics. Use for: movie trailers, game trailers, book trailers, event teasers, brand films, short film concepts, pitch visualizations. Triggers: cinematic trailer, movie trailer, game trailer, book trailer, teaser video, dramatic video, film trailer, cinematic video, event teaser, epic trailer, trailer maker"
allowed-tools: Bash(curl *), WebFetch
---

# AI Cinematic Trailer

Create dramatic cinematic trailers and teaser sequences using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a video: cinematic trailer shot — a lone warrior stands on a cliff edge overlooking a burning medieval city, cape billowing in hot wind, ash falling like snow, camera slowly dollying backward to reveal the massive scale of destruction, dramatic orchestral mood, desaturated warm tones, anamorphic widescreen"
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
        "content": "Generate a video: cinematic trailer shot — a lone warrior stands on a cliff edge overlooking a burning medieval city, cape billowing in hot wind, ash falling like snow, camera slowly dollying backward to reveal the massive scale of destruction, dramatic orchestral mood, desaturated warm tones, anamorphic widescreen"
    }]
)

print(response.choices[0].message.content)
```

### With Concept Art Reference

Use concept art or storyboard frames as visual guides:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a cinematic trailer shot based on this concept art. Bring the scene to life with dramatic camera movement, atmospheric effects like fog and particles, cinematic color grading, anamorphic lens flares, slow deliberate motion"
      }
    ],
    "image_urls": ["https://example.com/concept-art.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Genre Templates

| Genre | Visual Palette | Key Elements |
|-------|---------------|--------------|
| **Sci-Fi** | Cool blues, neon accents, dark | Space, technology, neon, chrome |
| **Fantasy** | Warm golds, deep greens, rich | Magic, castles, creatures, nature |
| **Horror** | Desaturated, deep shadows, cold | Darkness, fog, tension, isolation |
| **Action** | High contrast, warm highlights | Explosions, motion blur, intensity |
| **Thriller** | Cool, muted, tight framing | Close-ups, shadows, tension |
| **Post-Apocalyptic** | Dusty, desaturated, amber | Ruins, desolation, survival |
| **Historical Epic** | Rich, painterly, golden | Armies, landscapes, grandeur |

## Cinematic Camera Language

| Shot | Use In Trailer | Keywords |
|------|---------------|----------|
| **Wide Establishing** | Opening shots, scale reveals | extreme wide, aerial, epic scale |
| **Slow Push-In** | Building tension, character intro | slow dolly in, creeping forward |
| **Pull-Back Reveal** | Showing context, scale surprise | camera pulls back, reveal |
| **Low Angle** | Power, intimidation, heroism | low angle, looking up, imposing |
| **Dutch Angle** | Unease, chaos, disorientation | tilted frame, dutch angle |
| **Whip Pan** | Energy, transitions between scenes | fast pan, whip, blur transition |
| **Overhead** | Gods-eye view, strategic scenes | top down, overhead, birds eye |

## Examples

### Sci-Fi Teaser

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: sci-fi trailer shot — a massive alien spacecraft slowly emerges from behind the dark side of the moon, casting a shadow over Earth. Tiny debris and dust float in the foreground. Cold blue lighting, lens flares, extreme wide shot, silence of space, ominous and awe-inspiring, Christopher Nolan style"
      }
    ],
    "stream": false
  }'
```

### Horror Teaser

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: horror trailer shot — a long dark hallway in an abandoned hospital, a single flickering fluorescent light. Camera slowly pushes forward down the corridor. A door at the far end slowly creaks open by itself. Desaturated tones, heavy shadows, uncomfortable tension, handheld slight shake"
      }
    ],
    "stream": false
  }'
```

### Fantasy Epic

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: fantasy trailer shot — a massive dragon descending from thunderclouds, wings spread wide, lightning illuminating its scales, swooping over a battlefield of armored soldiers below. Camera tracks the dragon from below, epic scale, rain falling, fire and smoke, Lord of the Rings epic quality, anamorphic widescreen"
      }
    ],
    "stream": false
  }'
```

## Trailer Shot List Workflow

Build a complete trailer by generating individual shots:

```bash
# Title card / Mood setter
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: black screen slowly fading in to reveal a desolate desert wasteland stretching to the horizon, wind blowing sand, extreme wide shot, post-apocalyptic, silence, slow camera rise, muted orange and gray tones"}],
    "stream": false
  }'

# Character introduction
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: medium shot of a hooded figure walking through the desert wasteland, sand swirling at their feet, tattered cloak, camera tracking alongside, determined stride, harsh sunlight, post-apocalyptic, cinematic"}],
    "stream": false
  }'

# Climactic moment
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: the hooded figure reaches the top of a dune and looks down at a massive ruined city half-buried in sand, camera pulls back to reveal the enormous scale, golden light breaks through storm clouds, epic reveal, awe and determination, post-apocalyptic, cinematic widescreen"}],
    "stream": false
  }'
```

## Cinematic Keywords Cheat Sheet

```
anamorphic widescreen, letterbox, film grain, shallow depth of field,
lens flares, atmospheric haze, volumetric light, god rays,
slow motion, dramatic pause, tension building, epic scale,
handheld shake, Steadicam, crane shot, aerial tracking
```

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — General video generation
- [AI Music Video](../ai-music-video/SKILL.md) — Music-driven visuals
- [Image to Video](../image-to-video/SKILL.md) — Animate concept art
- [AI Slow Motion](../ai-slow-motion/SKILL.md) — Dramatic slow-motion effects

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
