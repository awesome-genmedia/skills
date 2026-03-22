---
name: ai-property-video
description: "Create property tour videos using each::sense AI. Generate walkthrough videos, aerial drone shots, and cinematic property showcases for real estate listings and marketing. Supports interior tours, exterior flyovers, and neighborhood context videos. Use for: real estate listings, property marketing, virtual tours, agent showreels, property showcase, Airbnb listings. Triggers: property video, real estate video, property tour, virtual tour video, listing video, house walkthrough, drone property video, real estate showcase, home tour, property flyover"
allowed-tools: Bash(curl *), WebFetch
---

# AI Property Video

Create property tour and showcase videos using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a cinematic real estate video: a slow, smooth camera push through the front door of a modern luxury home into a bright open-plan living room with floor-to-ceiling windows overlooking a pool and garden. Natural sunlight streaming in, warm color grading, real estate showcase quality, 4K cinematic"
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
        "content": "Generate a cinematic real estate video: a slow, smooth camera push through the front door of a modern luxury home into a bright open-plan living room with floor-to-ceiling windows overlooking a pool and garden. Natural sunlight streaming in, warm color grading, real estate showcase quality, 4K cinematic"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a property photo to generate a video tour of that specific space:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a video walkthrough starting from this room. Slow camera pan from left to right, revealing the full space. Then push forward toward the window. Smooth gimbal movement, natural lighting, real estate tour quality."
      }
    ],
    "image_urls": ["https://example.com/living-room-photo.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Video Shot Types

| Shot Type | Camera Movement | Best For |
|-----------|----------------|----------|
| **Push-In / Walk-Through** | forward dolly into a room | revealing interior spaces |
| **Pan** | horizontal sweep left to right | showing wide rooms and views |
| **Tilt** | vertical sweep bottom to top | highlighting tall ceilings, facades |
| **Orbit** | circling around a focal point | exterior establishing shot |
| **Drone Flyover** | ascending aerial pullback | showing property and surroundings |
| **Tracking** | lateral movement alongside a feature | hallways, countertops, details |
| **Reveal** | obstacle moves aside or camera emerges | dramatic reveal of a view or room |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a [style] real estate video:" + [camera movement description] + [space/property details] + [lighting and atmosphere] + [quality keywords]
```

### Camera Movement Language

Be specific about motion:
```
"slow dolly push forward through the hallway"
"smooth 180-degree pan revealing the entire living room"
"ascending drone shot pulling back from the rooftop pool"
"lateral tracking along the kitchen countertop"
"gentle orbit around the exterior of the property"
```

### Quality and Style Keywords

```
4K cinematic, smooth gimbal movement, real estate showcase,
luxury property tour, warm natural light, golden hour,
professional listing video, architectural visualization
```

## Examples

### Interior Walkthrough

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a real estate interior walkthrough video: camera starts in a bright modern kitchen with white marble countertops and slowly pushes through an archway into a spacious dining room with a large wooden table and statement chandelier. Continue pushing toward French doors that open to a landscaped backyard. Smooth steady movement, warm afternoon light, luxury home tour quality."
      }
    ],
    "stream": false
  }'
```

### Aerial Drone Exterior

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a drone aerial video of a Mediterranean-style villa: start with a close shot of the terracotta roof and pool courtyard, then slowly ascend and pull back to reveal the entire property surrounded by olive trees and rolling hills. Golden hour lighting, warm cinematic color grading, 4K real estate drone footage."
      }
    ],
    "stream": false
  }'
```

### Luxury Bathroom Reveal

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a real estate video: camera starts low, looking at polished marble floor tiles, then slowly tilts up to reveal a luxurious spa bathroom with a freestanding soaking tub centered under a skylight, double vanity with brass fixtures, and a walk-in rainfall shower behind a glass partition. Soft ambient light from the skylight, steam wisps for atmosphere, smooth slow reveal."
      }
    ],
    "stream": false
  }'
```

## Multi-Shot Tour Workflow

```bash
PROPERTY_STYLE="modern luxury home, bright and airy, warm natural light, 4K cinematic"

SHOTS=(
  "Exterior establishing: drone orbit around a contemporary two-story home with flat roof and large glass panels, manicured lawn, late afternoon sun"
  "Entry reveal: camera pushes through a tall pivot front door into a double-height foyer with a floating staircase"
  "Living room pan: slow 180-degree pan of an open living room with sectional sofa, fireplace, and floor-to-ceiling windows overlooking mountains"
  "Kitchen tracking: lateral tracking shot along a long kitchen island with waterfall marble edge, past open shelving to a breakfast nook"
  "Master suite: push into the master bedroom through double doors, camera glides past a king bed toward a panoramic window view"
  "Backyard finale: camera pushes through sliding glass doors to reveal an infinity pool at sunset with distant city lights"
)

for SHOT in "${SHOTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a real estate video shot: $SHOT. $PROPERTY_STYLE, smooth gimbal movement.\"}],
      \"stream\": false
    }"
  echo "=== SHOT ==="
done
```

## Common Pitfalls

- **Jerky camera descriptions** — always specify "slow" and "smooth" for professional results. Abrupt movements look amateurish.
- **Too many rooms in one clip** — each AI-generated video is a single continuous shot. Focus on one room transition per generation.
- **Forgetting furniture and staging** — an empty room tour is less compelling. Describe furnished spaces.
- **Unrealistic physics** — avoid camera movements that would be impossible (going through walls, instant direction changes).
- **Missing atmosphere** — without lighting and mood descriptions, videos look flat. Always mention time of day and light quality.

## Related Skills

- [AI Virtual Staging](../ai-virtual-staging/SKILL.md) — Stage rooms before creating tour videos
- [AI Interior Design](../ai-interior-design/SKILL.md) — Redesign rooms for video showcase
- [AI Exterior Remodel](../ai-exterior-remodel/SKILL.md) — Renovate exteriors before filming
- [AI Floor Plan](../ai-floor-plan/SKILL.md) — Plan the tour route with a floor plan

## Related Models

- [wan-2-1](../../../models/wan-2-1/SKILL.md) — High quality video generation
- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image stills
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
