---
name: ai-timelapse-generator
description: "Create timelapse-style videos using each::sense AI. Generate accelerated time sequences showing natural phenomena, construction progress, seasonal changes, day-to-night transitions, plant growth, weather shifts, and urban activity. Supports photorealistic and stylized timelapse aesthetics. Use for: nature timelapses, construction progress, seasonal transitions, day-night cycles, cloud movements, plant growth, city life, weather changes. Triggers: timelapse, time lapse, ai timelapse, fast forward, accelerated video, day to night, seasonal change, growth timelapse, construction timelapse, time passage, hyperlapse"
allowed-tools: Bash(curl *), WebFetch
---

# AI Timelapse Generator

Create timelapse-style videos showing accelerated time passages using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a timelapse video: clouds racing across a mountain landscape from day to night. The sun arcs across the sky, shadows sweep over the valley, golden hour light transitions to blue twilight, then stars emerge and the Milky Way rotates overhead. Camera locked on tripod, static composition, photorealistic timelapse."
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
        "content": "Generate a timelapse video: clouds racing across a mountain landscape from day to night. The sun arcs across the sky, shadows sweep over the valley, golden hour light transitions to blue twilight, then stars emerge and the Milky Way rotates overhead. Camera locked on tripod, static composition, photorealistic timelapse."
    }]
)

print(response.choices[0].message.content)
```

### With Starting Frame

Use a photo as the starting point for the timelapse:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a timelapse starting from this image. Show the passage of time — clouds moving rapidly, lighting changing from morning to evening, shadows sweeping across the scene. Tripod-locked, smooth timelapse motion."},
              {"type": "image_url", "image_url": {"url": "https://example.com/city-morning.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Timelapse Types

| Type | Description | Keywords |
|------|-------------|----------|
| **Day to Night** | Full day cycle in seconds | sunrise to sunset, day-night transition |
| **Cloud Movement** | Dramatic sky with racing clouds | clouds racing, stormy sky, weather front |
| **Seasonal Change** | Spring to winter in one shot | leaves changing, snow accumulating, flowers blooming |
| **Plant Growth** | Seed to bloom accelerated | germination, vine growing, flower opening |
| **Urban Activity** | City traffic, crowds, lights | busy intersection, rush hour, city lights |
| **Construction** | Building going up frame by frame | structure rising, scaffolding, progress |
| **Star Trail** | Night sky with star rotation | star trails, Milky Way rotation, long exposure |
| **Weather Front** | Storm rolling in or clearing | storm approaching, fog rolling in, clouds parting |

## Examples

### Flower Blooming

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a timelapse video: a red rose bud slowly opening into full bloom. Close-up macro shot, dark green background, petals unfurling one by one, dewdrops visible on petals, studio lighting, smooth accelerated motion, botanical timelapse style."
      }
    ],
    "stream": false
  }'
```

### City Day-Night Cycle

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a timelapse video: a city skyline view transitioning from afternoon through golden hour to nighttime. Sunlight fades, office windows start lighting up, street lights turn on, car headlights create flowing light trails, neon signs illuminate. Camera static, rooftop vantage point, photorealistic urban timelapse."
      }
    ],
    "stream": false
  }'
```

### Seasonal Landscape

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a timelapse video: a single oak tree in a field transitioning through all four seasons. Spring with green buds, summer in full green canopy, autumn with red and orange leaves falling, winter with bare branches and snow covering the ground. Same camera angle throughout, smooth seasonal transition."
      }
    ],
    "stream": false
  }'
```

## Prompt Tips

- **Specify "camera locked" or "tripod-static"** to maintain the classic timelapse look
- **Describe the time passage explicitly**: "from dawn to dusk," "over several months," "spring to winter"
- **Mention what moves**: "clouds racing, shadows sweeping, sun arcing" — not everything should change
- **Keep the composition fixed**: True timelapses keep the same framing while time passes
- **Add "smooth accelerated motion"** to distinguish from jerky or random transitions
- **For hyperlapse**: mention "camera slowly moving forward" — this is a moving timelapse

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — General video generation
- [Image to Video](../image-to-video/SKILL.md) — Animate a single frame
- [AI Video Loop](../ai-video-loop/SKILL.md) — Seamless looping timelapses
- [AI Slow Motion](../ai-slow-motion/SKILL.md) — Opposite of timelapse — slow things down

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
