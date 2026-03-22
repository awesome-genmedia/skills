---
name: ai-auto-ad
description: "Generate automotive advertisement imagery using each::sense AI. Create commercial-grade vehicle photography for dealerships, manufacturers, and automotive campaigns. Produce hero shots, lifestyle scenes, and dramatic automotive compositions. Use for: car ads, automotive advertising, dealership marketing, vehicle campaigns, auto commercials. Triggers: auto ad, car advertisement, automotive ad, vehicle ad, car commercial, dealership photo, auto marketing, car campaign, automotive photography, vehicle promotion"
allowed-tools: Bash(curl *), WebFetch
---

# AI Automotive Advertisement Generator

Generate commercial-grade automotive advertisement imagery using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A dramatic automotive advertisement: a black luxury SUV speeding along a winding coastal highway, ocean cliffs dropping away to turquoise water below, motion blur on the road and background, the vehicle sharp and in focus, golden hour sunlight catching the chrome details, cinematic wide angle, premium automotive commercial photography"
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
        "content": "A dramatic automotive advertisement: a black luxury SUV speeding along a winding coastal highway, ocean cliffs dropping away to turquoise water below, motion blur on the road and background, the vehicle sharp and in focus, golden hour sunlight catching the chrome details, cinematic wide angle, premium automotive commercial photography"
    }]
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
              {"type": "text", "text": "Create an automotive advertisement using this vehicle: place it in an aspirational urban nighttime scene, wet reflective city streets, neon signs reflecting off the paint, dramatic low angle, the vehicle as the hero, premium brand advertisement quality"},
              {"type": "image_url", "image_url": {"url": "https://example.com/vehicle-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Automotive Ads

- **Choose dramatic locations** — coastal roads, mountain passes, city streets, desert highways.
- **Use motion cues** — "speeding," "cornering," "drifting" with motion blur for dynamism.
- **Include reflections** — wet roads, polished surfaces, chrome details catch light beautifully.
- **Specify the vehicle segment** — luxury, sport, family, off-road, electric to set the right tone.
- **Match the mood to the brand** — "refined elegance" for luxury, "raw power" for performance, "adventure" for SUVs.

## Examples

### Dealership Hero Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A showroom-quality automotive photograph: a silver sports coupe in a pristine white studio environment, dramatic overhead spotlight creating defined shadows and reflections on the glossy paint, three-quarter front angle showing the aggressive stance, ultra-clean background, dealership advertising photography"
      }
    ],
    "stream": false
  }'
```

### Adventure Lifestyle Ad

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An adventure automotive advertisement: a rugged off-road truck with a rooftop tent and kayaks, parked at a scenic mountain lake campsite at sunrise, mist rising from the water, campfire embers glowing nearby, lifestyle adventure aspiration, wide cinematic composition with space for headline on the sky area"
      }
    ],
    "stream": false
  }'
```

### Electric Vehicle Campaign

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "An electric vehicle advertisement: a sleek white electric sedan parked in front of a solar-powered charging station with a modern sustainable architecture building behind, lush green landscape, bright optimistic daytime lighting, clean and futuristic atmosphere, eco-luxury automotive campaign photography"
      }
    ],
    "stream": false
  }'
```

## Workflow: Automotive Campaign Production

1. **Define the vehicle and brand tone** — Luxury, sport, adventure, family, or eco.
2. **Generate hero shots** — Create the primary ad image in a dramatic setting.
3. **Create lifestyle scenes** — Show the vehicle in aspirational real-world contexts.
4. **Produce studio shots** — Clean showroom-style images for dealership use.
5. **Generate detail close-ups** — Wheel, headlight, interior, and badge details.
6. **Adapt for platforms** — Create variants for billboard, digital, social, and print.

## Related Skills

- [AI Car Configurator](../ai-car-configurator/SKILL.md) — Vehicle customization previews
- [AI Vehicle Wrap](../ai-vehicle-wrap/SKILL.md) — Custom wrap and livery designs
- [AI Ad Creative](../../marketing/ai-ad-creative/SKILL.md) — General ad creative generation
- [AI Campaign Visuals](../../marketing/ai-campaign-visuals/SKILL.md) — Multi-platform campaign assets

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic automotive rendering
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Dramatic visual compositions
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid concept exploration

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
